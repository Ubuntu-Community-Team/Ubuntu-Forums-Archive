---
title: "Autologin for multiple users with LUKS"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by Micha_R on 2009-10-06
Hi,

I have setup an encrypted partition containing a LVM volume for my ubuntu installation. Just /boot is not encrypted. Now I have 2 Users who have a password each to decrypt the LUKS-partition. These passwords are the same as the login passwords for those users. Now here is what I would like to do, but I don't know if it is possible:

I would like to have a skrip that compares the entered LUKS password with existing user passwords, and if it finds a match, executes an auto login for exactly that user.

In that way both users would need to type in the password only once at startup.

Do you think that this would be possible?

Mike

---

### Post by Micha_R on 2009-10-08
No ideas? Anyone?

---

