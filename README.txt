O/L Paper Hub — Professional edition

Contents
- index.html : student website. All CSS and JavaScript are inline; student-studying.png is the homepage hero photo.
- admin.html : secure admin portal. All CSS and JavaScript are inline.
- supabase-setup.sql : database and storage security policies.

IMPORTANT — FIRST RUN
- Keep student-studying.png in the same folder as index.html, then open index.html in a browser to see the student homepage.
- Preview mode does not yet have real uploaded PDFs; download buttons become available after Supabase is configured and papers are uploaded.
- The admin page will show a setup-needed message until Supabase is configured.
- For a live deployment, host both HTML files on the same static hosting site (for example GitHub Pages, Netlify, or Vercel).

Setup
1) Create a Supabase project.
2) Run supabase-setup.sql in SQL Editor.
3) Create a Storage bucket named papers (the included SQL creates it as private).
4) In BOTH HTML files, replace SUPABASE_URL and SUPABASE_ANON_KEY with your project URL and publishable/anon key. Never use a service-role/secret key in browser code.
5) In index.html only, replace WHATSAPP_NUMBER with the site WhatsApp contact number (digits only, including country code). If left blank, WhatsApp opens its share screen so the student can choose a chat.
6) Create your administrator user under Supabase Authentication.
7) Add that user's UUID to public.admin_users from SQL Editor, for example:
   insert into public.admin_users(user_id) values ('YOUR_AUTH_USER_UUID');
8) Deploy the HTML files and SQL on your hosting provider.

Security
- Admin is not linked from the public student homepage.
- Admin access requires a Supabase Auth session and allowlisted admin_users row.
- RLS policies protect paper writes/deletes and storage uploads/deletes.
- Public site only reads paper records and can create temporary signed download URLs.
- Never publish the service role key.
