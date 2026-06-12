---
title: "How to remove fedora 9 and install ubuntu 9.04 on my Dual Boot system"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by tvkpz on 2009-09-15
Hi,

I am a total newbie to Linux and I am trying to learn.

I have a system that is Dual Boot, i.e., runs WIN XP and the other Fedora 9.

I am not so satisfied with the Fedora 9 as many of the apps it seems are not supported and also I saw ubuntu is much better maintained. So I want to install ubuntu and remove the fedora install.

I have a lot of important data on the WIN partition. So I am afraid not to take any  foolish step that will remove that.

Can you please help me in a step by step way what I need and how to go about making a smooth transition.

Appreciate your help!

tvkpz

---

### Post by briantoumbs on 2009-09-16
Put your Ubuntu Cd in and boot from it. 

Select Install 
Follow the instructions on screen untill it gets to where you want to install.

Select Manual Install.

This will bring up a screen that shows your hard drive and how it is partitioned. 

There should be one that says ntfs and then one that is ext3 or ext4. and a swap file. 

Don't touch the ntfs one.  

check the ext3/4 one and and format it as ext3/4 with the mount point as / 
you can keep the size the same. 


This will format the Linux partition only and keep your windows the same. 


Just double check to make sure your windows/ntfs partition is not checked,

---

