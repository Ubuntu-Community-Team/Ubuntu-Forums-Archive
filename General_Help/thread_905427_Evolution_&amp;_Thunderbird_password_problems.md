---
title: "Evolution &amp; Thunderbird password problems"
date: 2008-08-30
forum: General Help
---

### Post by Okiebuntu on 2008-08-30
I did a fresh install of the latest Ubuntu, did all the required updates to the latest kernel, etc. When I set up my Evolution account, it never ask me for a password when it first checks mail..I've tried deleting the account and making a new one, unchecking "save password", etc. 

I've also tried logging out, restarting the mail client, restarting the computer, etc., with no luck.

Thunderbird does the same thing, it never asks for a password and I don't have the option of a password manager

---

### Post by milton1 on 2008-08-30
I don't know about evolution, but the Thunderbird password management is under edit -> preferences -> privacy -> passwords.

If you remove saved passwords from thunderbird and are still not asked to enter them, I would suspect some manner of keyring in gnome or kwallet in kde may be storing your passwords for some reason.

---

