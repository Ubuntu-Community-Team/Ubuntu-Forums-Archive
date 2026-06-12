---
title: "Accounts invalid after upgrading from 7.10 to 8.04"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by ngolian on 2009-01-20
I started an upgrade on my sister's PC last night but I couldn't stay long enough to wait for it to complete and I had to leave it running.

Now, after rebooting, the user names/passwords of her and her husband have become invalid. I'm not there at the moment so I've got limited information, but I can visit later.

I have my own account on it and I used that to do the upgrade. Might it have deleted all the accounts except that one? How do I fix it if there are no valid accounts left?

---

### Post by taurus on 2009-01-20
See if those accounts are still there.

Applications -> Accessories -> Terminal
```
ls -la /home
```
You can change the password for those two accounts and see if they can log back in again with their username and the new password.

```
sudo passwd *sister*
sudo passwd *husband*
```
Replace *sister* & *husband* with the correct usernames.

---

### Post by ngolian on 2009-01-20
The trouble is you can't get to the terminal if you can't log in!

I've been round now and it turned out things had got a bit confused because the system's a bit cobbled together with 2 HDs, both with Windows and Linux on. The versions still in use are on sda1 (Win) and sdb6 (Lin) but the Ubuntu upgrader must have thought the abandoned Ubuntu installation on sda was important and had made it grub's default. I tidied up the grub config on sdb and reinstalled it to sda's boot block.

But I still don't know why the old Ubuntu on sda wouldn't accept anyone's login, because they always use the same passwords so they shouldn't have been different from what they are now.

---

### Post by taurus on 2009-01-20
I thought you said you have an account on that machine and are able to log in!

> I have my own account on it and I used that to do the upgrade.

---

