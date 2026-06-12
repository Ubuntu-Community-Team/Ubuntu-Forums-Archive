---
title: "Can't Upgrade from 8.10 to 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by alistair23 on 2009-04-24
So I have ubuntu with 8.10 fully updated with windows dual boot. So I started to use update-manager upgrade, which would have taken 5 hours. So I decided to use the alternative CD. So I downloaded that and mounted the ISO. I then ran the command. It asked if I wanted to use the Internet for updates. The first time I said yes. After 5 min of fetching I gave up and canceled. I ran it again saying no. It then gave an error saying:

> Error authenticating some packages  It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

There was a huge list. So I tried again saying yes to Internet updates, it ran through saying uninstall this, install that and upgrade this. There were 400MB of upgrades, I only have a small amount of bandwidth, so that is to much. I canceled it again and tried again saying no to Internet. But it still came up saying download 400MB of updates. So no matter what I do it tells me to download, and that I can't do.

So what can I do??? Can I clear the catch and start again? Could I backup my stuff install 9.04 newly then move everything across? Or am I stuck? Someone please help. PLEASE

---

### Post by Moog on 2009-04-24
> **alistair23 said:**
> So I have ubuntu with 8.10 fully updated with windows dual boot. So I started to use update-manager upgrade, which would have taken 5 hours. So I decided to use the alternative CD. So I downloaded that and mounted the ISO. I then ran the command. It asked if I wanted to use the Internet for updates. The first time I said yes. After 5 min of fetching I gave up and canceled. I ran it again saying no. It then gave an error saying:



There was a huge list. So I tried again saying yes to Internet updates, it ran through saying uninstall this, install that and upgrade this. There were 400MB of upgrades, I only have a small amount of bandwidth, so that is to much. I canceled it again and tried again saying no to Internet. But it still came up saying download 400MB of updates. So no matter what I do it tells me to download, and that I can't do.

So what can I do??? Can I clear the catch and start again? Could I backup my stuff install 9.04 newly then move everything across? Or am I stuck? Someone please help. PLEASE


Ensure the CD is in the drive.

Go to 
System -> Administration -> Software Sources
Untick all of the online repositories and ensure the CD is ticked.
Allow the repositories to update then run update manager...
System -> Administration -> Update Manager

Let us know how you get on.

---

### Post by alistair23 on 2009-04-24
Hey, thanks for that. That worked great. I got rid of all of my sources. But it wanted to uninstall 154 packages, so I did it anyway and managed not to uninstall packages. So now everything works except when I boot it boots like the old Ubunut, it takes a while and has the old status bar, is that something with GRUB, I didn't change my configuration maybe thats it? So could someone tell me what to do?

---

### Post by alistair23 on 2009-04-27
Hey, I fixed it. I just changed the GRUB config to the new Kernel vesion. I will change it to solved if I can. But now I have trouble with my NVIDIA driver but I found something which should help at [http://ubuntuforums.org/showthread.php?t=1139101](http://ubuntuforums.org/showthread.php?t=1139101). BTW: that was just for people who read the forum, I don't need any replies.

---

