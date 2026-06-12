---
title: "Do I need to back-up my files before I upgrade? [Noob]"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by opower95 on 2009-11-04
Looks like Ubuntu has finally decided to agree with me and upgrade without any problems :D. When the upgrade is finished and my computer reboots, will all of my files be gone?

Also, how do I know whether or not "community maintained software" is enabled? 
Thank you.

---

### Post by Sunflower1970 on 2009-11-04
It's *always* a good idea to make sure to back up your files before an upgrade, clean install, etc. You never know what may happen.

For the repos, look in Synaptic. System-->Administration-->Synaptic Package Manger. 

When Synaptic opens up, (and I'm not on Ubuntu at the moment--doing this from memory), up at the top, under 'Settings' look for Repositories. Open it up, and one of the tabs will show you what repos are enabled or not. Just check the ones you want enabled, and uncheck the ones you don't want enabled.

---

### Post by egwest on 2009-11-04
> **opower95 said:**
> Looks like Ubuntu has finally decided to agree with me and upgrade without any problems :D. When the upgrade is finished and my computer reboots, will all of my files be gone?

Also, how do I know whether or not "community maintained software" is enabled? 
Thank you.


Backing up your personal files is highly recommended, if the upgrade fails to take fully, you may have to do a complete fresh install. 
I have an external hard drive that I use to backup all my personal files/folders to when doing an upgrade.

---

### Post by howefield on 2009-11-04
Also just to say, that backing up files is not just a good idea at upgrade time. It should be part of your ongoing computing strategy.

As more of your life goes digital, there is an ever growing requirement to have a robust backup schedule.

---

### Post by rich97 on 2009-11-04
I believe Ubuntu Karmic had upgrade software built in? No?

---

### Post by Maheriano on 2009-11-04
Ya I back up my files regularly. I'm actually in the process of setting up a scheduler to back up my files every 2-3 days so I don't lose anything in case of a crash. My next step from there is to either do a second backup on a remote server or to back up onto an external drive which I keep in a safety deposit box in case my house burns down.

Anyway, you might also want to consider splitting your partitions if you're going to do an install to the newest version. If you have a separate /home and / partition then it is very unlikely that an upgrade will even touch those partitions and those files should be fine.

---

