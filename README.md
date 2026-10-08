# Personal Expense Tracker

A small cloud project to build yourself with HTML, CSS, and JavaScript.

**Status:** Project brief only. The application has not been implemented or deployed yet.

## Goal

Build an expense tracker you can open from different devices. Sign in, add and delete expenses, and see the same data after signing in elsewhere. Use one currency of your choice for the first version.

## Cloud setup

- **Website:** Host the HTML, CSS, and JavaScript on GitHub Pages.
- **Accounts and data:** Use Supabase Auth and a Supabase Postgres table.
- **Access control:** Enable Row Level Security (RLS) so each signed-in user can read and change only their own expenses.

GitHub Pages serves static files, while Supabase supplies authentication and data storage. This is still a browser app; you do not need to build your own server for the first version.

## First version

- [ ] Sign up, sign in, and sign out with email and password.
- [ ] Add an expense with a name, positive amount, category, and date.
- [ ] Display the signed-in user's expenses and their total.
- [ ] Delete an expense and update the total.
- [ ] Show loading, empty, and error states.
- [ ] Keep data after refreshing and show it on a second device after sign-in.
- [ ] Prevent one account from reading or changing another account's expenses.
- [ ] Publish the finished site with GitHub Pages.

Suggested categories: Food, Transport, Shopping, Bills, and Other.

## Build it in small steps

1. **Page:** Create `index.html` with a sign-in form, expense form, list, and total. Add labels to each input.
2. **Auth:** Create a Supabase project, use `@supabase/supabase-js` v2, and implement sign-up, sign-in, and sign-out. Configure the site's URL in Supabase Auth so email confirmation links return to your site.
3. **Data:** Create an `expenses` table with an ID, owner ID, name, amount in the smallest currency unit (such as cents), category, and date. Set the owner ID from the signed-in user, not a user-editable form field.
4. **Privacy:** Enable RLS. Give the authenticated role only the needed table privileges. Add separate policies for selecting, inserting, and deleting rows when the row's owner ID matches the authenticated user's ID. Do not allow anonymous access to expenses.
5. **Features:** Load expenses from Supabase, add and delete rows, and calculate the displayed total. Handle request errors clearly; never pretend an unsuccessful save worked.
6. **Publish:** Add the website files to the repository and enable GitHub Pages. Configure Supabase Auth redirect URLs for the final Pages address, then test with two accounts and two devices or browsers.

Start with step 1 and complete each step before adding the next feature.

## Check your work

- Adding expenses of 12.50 and 7.25 produces a total of 19.75.
- Deleting the 12.50 expense leaves a total of 7.25.
- Invalid input does not save an expense or change the total.
- Refreshing and signing in on another device shows the same expenses.
- A signed-out visitor cannot see expense records.
- A second account cannot read, insert, or delete the first account's records, even by calling the data API directly.
- Failed network requests show an error and leave the displayed data consistent with the server.
- Labels, focus indicators, and buttons work with Tab and Enter.
- Expense names are displayed as text, never interpreted as HTML.

## Security and scope

Use a Supabase **publishable key** in the browser, protected by correct RLS policies. Never commit a Supabase secret or service-role key; those bypass RLS. Do not store actual expense records in GitHub, source files, or browser `localStorage`. Avoid putting private amounts in URLs or analytics.

The repository is public, so review files before committing. The first version needs no bank connection, payment processing, or multi-currency conversion. The app itself has not been built yet; this README is the project plan for you to implement.

## Official references

- [GitHub Pages: create a site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
- [Supabase Auth](https://supabase.com/docs/guides/auth)
- [Supabase JavaScript client v2](https://supabase.com/docs/reference/javascript/)
- [Supabase Row Level Security](https://supabase.com/docs/guides/database/postgres/row-level-security)
- [Supabase API keys](https://supabase.com/docs/guides/getting-started/api-keys)
