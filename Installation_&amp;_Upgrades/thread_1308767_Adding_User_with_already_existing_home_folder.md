---
title: "Adding User with already existing home folder?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Spartachris on 2009-10-31
I need some help! I did a fresh install of 9.10 (AMD64)on an existing / partition with a separate /home partition. I guess I did it correctly, as the home partition was not over-written and the user's home folders were intact (I have six--one for everyone in my family).

But the only user is me, which I setup during the fresh install. I cannot add the other users under System>Administration>Users and Groups because it tells me the there is already a home folder for that user.

Did I do the install wrong? Is there some way I can add the other five users without first deleting their /home folder?

Thanks for your help on this!

---

### Post by hal10000 on 2009-10-31
```
 sudo adduser --home /home/your_sister your_sister
```
if /home/your_sister already exists, then it will **not** be created, i guess this is what you want.
But because probably the new users UID and GID differs from the old ones, you may have to change the owner of the files in the homedirectory:
```
sudo chown -R your_sister:your_sister /home/your_sister
```

---

### Post by Spartachris on 2009-11-01
hal10000 --

Thanks so much! That worked perfectly, and as it turns out, I did not have to change the permissions.

Now...was there another way I could have done the clean install to avoid this step? I ask because Linux seems to mean "ten different ways to do something" :)

Thanks again for helping me out with this!

---

### Post by hal10000 on 2009-11-02
I'm not sure, but i guess that during the installation process you have the choice to take over the existing structure of your home partition.

---

### Post by momist on 2010-01-11
Thanks to hal10000 for this - I've needed it twice in as many months (don't ask!   ):popcorn:

---

### Post by boombox1387 on 2010-01-24
Just wanted to add my thanks as well.  It took a while to find it, but this is exactly what I was looking for.

---

