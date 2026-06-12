---
title: "i need to reinstall ubuntu and dont kNow hoW... hEElp plz"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by xmaster23 on 2009-04-15
hey guyz im new to ubuntu, been using it for about 4 months now and lovin it, anyway i was messin around and installed the kubuntu-desktop package and ive been having lots of trouble after that. the windows manager fails sometimes and something happened to my sound card so now ive got no sound, ive tried the sudo aptitude remove command and sudo apt-get remove but it doesnt seem to work so  i would like to reinstall ubuntu but dont know how. i have a dual boot with vista but i dont know what would happen with grub loader if i format my linux partition from vista ... any suggestions???

---

### Post by lisati on 2009-04-15
First of all, it's always a good idea to make sure you have a backup of all your important data - this includes recovery disks for Windows "just in case". Some installations of Windows come with a tool to make a set of recovery disks for you. 

How did you install Ununtu, was it through "Wubi" (within Windows) or was it in its own partition?

---

### Post by xmaster23 on 2009-04-15
i installed it in its own partition, the thing is  i cant find my recovory cd from windows,

---

### Post by louieb on 2009-04-15
Not a problem. When you get to the partition step of the install chose manual. Click on the current Ubuntu install partiton - chose edit - make its mount point / (root) , select format yes. and continue with the install. 

The installer should overwrite the old Ubuntu install and  set up Grub to boot both Ubuntu and windows. Good Luck.

---

### Post by greene.d.e on 2009-04-25
I am having the same problem.  I see what you are talking about in the manual partition section, but I got nervous that I will format something I shouldn't because when I came to the end it said that it was going to format my ubuntu and my swap file.  I am a newbie and do not completely understand the lingo and commands for /(root). I saw / and several other / with words after them but no /(root).  What does this command do?  Do I also need to write the new ubuntu over the swap /dev/sda6, or just the ubuntu section /dev/sda5?

---

