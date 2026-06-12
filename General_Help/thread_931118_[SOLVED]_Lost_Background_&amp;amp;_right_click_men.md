---
title: "[SOLVED] Lost Background &amp;amp; right click menu"
date: 2008-09-26
forum: General Help
---

### Post by brucenduane on 2008-09-26
I installed Ubuntu 8.04.1 clean install on my notebook  Toshiba Satellite A205-S5905 with 2 Gig memory and 250 Gig USB Hard Drive.

Downloaded CD from Ubuntu.com website and the install went well.  Installed latest packages of base after install.  Rebooted and everythings is fine.
Installed a number of packages that are similar to what I had on this machine when it was running Ubuntu 7.10.  Rebooted several times and no problem.

Rebooted and background fine, a background in directory ~/wall/back.jpg

I then changed the user password using passwd in a terminal window.
Rebooted and no background, just a light tan background.  No menu when I right click the mouse.  The upper and lower panels are present and unchanged from before the reboot.

I have installed this twice now and the problem occurs after I change the password both times.

I do not know what the window manager is or what special effects are in operation --- this is default install of Ubuntu 8.04.1.  

I do have UbuntuStudio 8.04.1 with the rt kernal running in another partition with the same packages plus those that come with UbuntuStudio
and I do not have this problem with I changed the password there.  

Please tell me what to do to fix this.
I don't know if I am using the Window Manager from Metacity or Compiz and I was not changing this from the default.

Be detailed in your commands, assume I'm a newbie.

Thank you for your help!!!
-Bruce.

---

### Post by chavanak on 2008-09-27
What is the exact command you give to change your password!!

---

### Post by brucenduane on 2008-09-27
The command in a Terminal window was: passwd

I think it has something to do with the disk icons.
The 250 gig hard drive has 10 partitions: 1 vfat and 9 ext3
It sometimes doesn't like a partition and HAL loads it different than
what is in /etc/fstab.  When it does, the wallpaper and menu aren't there.

Question: What runs to put the partition icons on the background=wallpaper
and puts up the wallpaper and responds with the right-click menu?


I ran the command in a terminal of : compriz
Then with to System==>Preferences==>Appearance and set effect to OFF.
Rebooted and the background and menu were there.  Did nothing.
Rebooted and the background=wallpaper and menu were gone.  Did nothing.
Rebooted and the background and menu were there.  Did nothing.

Question: There doesn't seem to be any consistency with what is happening.
Question:Is this a HAL vs Gnome problem in 8.04.1?

I don't have this issue with 7.10 Gusty Gibbon on any of my systems
including this notebook. 

Looking at the package list, I have metacity and compriz on the notebook
if that is helpful and I am running the gnome window manager.

Thanks for you help!!!

---

### Post by brucenduane on 2008-09-30
Problem Solved!!!

-bruce.

---

### Post by sayakb on 2008-10-01
Please mark the thread as solved (Thread tools->Mark thread as solved)

---

