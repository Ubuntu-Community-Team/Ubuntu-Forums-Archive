---
title: "Upgrade to 9.04 Borked Adduser"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by dsoper on 2009-05-21
Hi all,

I just upgraded an 8.04 LTS box to 9.04.  Everything seems to work fine, except adduser and useradd.  When I use adduser, I create the user and it asks for the user's Kerberos password.  Since the user doesn't have a password, it barfs.  When I use useradd, and specify a password, it creates the user, but that user can't log in.  Further investigation finds that the password I specified is stored in /etc/shadow, in clear text.  The GUI-based tools for creating users work fine.

Any idea what the problem might be?

Cheers,
Dennis

---

