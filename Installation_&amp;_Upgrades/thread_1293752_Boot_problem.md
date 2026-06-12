---
title: "Boot problem"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by crushingandy on 2009-10-17
I have Karmic Koala on my external HDD, and I was running it all day, but now when I try to boot, I get this error. Invalid Environment Block. I dont understand why it was working all day and now I cant even boot. Any ideas?

---

### Post by crushingandy on 2009-10-17
I read some posts about trying to fix this, and I saw that pressing E when grub loads, then delete the 2 rows:
recordfail=1
save_env recordfail
Then boot with Ctrl-X.
When I did this, I get the following error before being able to delete the two lines:
Press any key to continue
error: Invalid environment block
       Failed to boot default entries

Any help would be grateful.

---

### Post by jamesvar_70 on 2010-03-24
I am having the same problem 

Invalid Environment Block. I have a dual boot system with Ubuntu 9.10 and windows
i was getting the above message and i found the following solution 

pressing E when grub loads, then delete the 2 rows:

recordfail=1
save_env recordfail

Then  press Ctrl-X to boot.

When I do this i get the error again as

error: Invalid environment block
Failed to boot default entries
Press any key to continue
strangely i am now unable to load windows also

Any help would be grateful.

---

