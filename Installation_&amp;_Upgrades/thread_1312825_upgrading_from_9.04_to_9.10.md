---
title: "upgrading from 9.04 to 9.10"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by yorkshireflatcap on 2009-11-03
All,
 
Firstly, let me apologise if this has been asked a thousand times, but I feel that I've exhausted all other avenues without much sucess.
 
I've recently upgraded - through the software manager - from 9.04 to 9.10 and I'm having all sorts of problems!! I've been reading that this upgrade is experiencing a few 'teething' problems!!
 
After the upgrade is complete, I restart my laptop and I get **Kernel Panic - Not syncing: VFS: Unable to mount root fs on unknown block(0,0)** :confused:
 
I've been trying to correct the situation, but I feel I'm getting a little out of my depth here - especially on the administrator side of things.
 
If I select the option at boot up **Ubuntu 8.10, kernal 2.6.27-9-generic (on /dev/sda1)**, it allows me into the OS, but my file system has my user profile, and directory structure on another partition (I think sda7). So I can see my files, but I need my password to access them. :confused:
 
Is there a way where I can roll back to previous version, **9.04** and try and do a fresh install?
 
Regards
 
Yorki

---

### Post by yorkshireflatcap on 2009-11-03
What if I do a fresh install??  will I have to back up all my files that I wish to keep??  Please help as I am really struggling to fix this issue!
 
Many thanks

---

### Post by NoaHall on 2009-11-03
If you do a fresh install, it'll work fine. The problem seems to be that the location of the OS is wrong. Try going into 8.10 and running "sudo update-grub"

---

### Post by yorkshireflatcap on 2009-11-03
After I've done sudo update-grub then what?  Apoologies for the silly questions, but I'm relitively new  to Ubuntu... since V8.
 
Regards
 
John

---

### Post by yorkshireflatcap on 2009-11-03
Does anyone know how to do a rollback to a previous version of Ubuntu as the latest version seems to be SNAFU.
 
Thanks

---

