---
title: "Installing ubuntu fresh, but bugs still exist"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by wwnliu on 2009-07-11
My 8.10 installation is kinda messed up, and there are certain problems when I ran program like exaile and screenlets. I am hoping installing a fresh copy of 9.04 will fix the problem.

I opted to install with the existing /home partition as I don't want to go through the trouble of backing up my data files. However, after installation, not only the settings got carried over, but the problems as well. What wasn't working in 8.10, doesn't work in 9.04 as well. Is there any way to do a "really fresh" installation with an existing /home partition? Or clear the old settings in the /home partition?

---

### Post by presence1960 on 2009-07-11
Exactly what are the "problems"? Post a detailed expanation back here. If they involve your config files in /home you would be best backing up your data only from /home and marking that /home partition for format and set mountpoint to /home during the install. this will give you fresh config files, but you will have to start over for all the settings to get them back the way you want them. Then move your data back to /home. This of course is assuming the "problems" you refer to are caused by the config settings in your /home.

---

### Post by cariboo on 2009-07-11
I would suggest clearing the old settings from your /home/user directory. Another thing you can try, is create a new user, then transfer the files you want to keep from the old user to the new user.

---

