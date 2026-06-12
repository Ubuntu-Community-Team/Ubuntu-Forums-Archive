---
title: "/etc/aliases Execute Command as Root"
date: 2008-10-15
forum: General Help
---

### Post by NetSpike on 2008-10-15
Hi

I have a problem:  What I want to do is send a mail to [email]multidata@example.com[/email] and then have that server run a specific ruby hashbang script when it receives a mail to the multidata@ aliases.

What I done so far was I added a line to /etc/aliases as follows:
multidata: | /usr/bin/multidata/create_multidata_files.rb

Mail logs show that the server is receiving the mail to trigger the script, but the script is not executing.

Any suggestions would be great.

Thanks in advance!

---

