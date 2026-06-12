---
title: "New Jaunty install, can't reuse /home"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by tarpon_bill on 2009-04-27
For once I decide to do a wipe and install, OS only. I had already put /home into another partition and have been using that. So then comes Jaunty and decided to just reinstall the OS only and reuse the /home partition

Everything works, except how to reuse the previous user profiles and the files within. Currently I have a brand new user in /home and it works fine.

But how do I recover the old users and make use of them once again. All the files are there, switching to root accesses them, but I want to reinstate the old users ...

---

### Post by StuartN on 2009-04-27
I have never tried it, but the "right" way must be something along the lines:

  sudu adduser --home /home/username --no-create-home username

Probably a safer bet is to mv /home/username /home/oldusername, then create the new user username, then mv /home/oldusername /home/username. (I.e. temporarily rename the users home to old, recreate the user, then overwrite their newly created home with the old one). Note that this will overwrite all the hidden "." files with user settings and you might want to keep any Ubuntu 9.04 specifics.

After creating the resurrected username you will have to chown -R username /home/username to reset the (numerical) ownership of the files.

---

### Post by tarpon_bill on 2009-04-28
Thanks for the clues, is it just me or is there an easy way to do this? I had to do another Jaunty install and could not find anything during the install which points to connecting up old users to their existing partitions. 

I tried gingerly to mv things around and the permissions seem to work correctly. I got side tracked and haven't had enough time to get back to it for a more thorough look see. I will report back when I fully figure it out.

You would think this is something everyone would want to do ...

---

### Post by tarpon_bill on 2009-04-29
sudo adduser --home /home/test --no-create-home test --uid 1002

It works, but you need to be real careful, else you trip over the permissions. The correct way to do this, my example assumes user name 'test' with a uid of 1002.

The tricky part is getting the uid right. You need to sudo ls -la in the intended users home directory, and search for the old uid and then use that. Ubuntu numbers from 1000 up and is the first number in the listing. For example, on my system the user 'test' has a uid of 1002.

If you blow it, you can delete the user with the "System->Administration->Users and Groups" dialog and leave the files alone. So it is somewhat reversible.

Patience and care are best when it comes to systems spelunking ... else disaster looms just a key click away. I would recommend reading the entire "adduser" man page before starting.

---

