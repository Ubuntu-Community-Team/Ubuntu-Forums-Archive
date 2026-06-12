---
title: "Installed Ubuntu , Erased Vista Accidentally, now I cant Recover Vista....any ideas?"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by taylaboy on 2009-02-27
I installed Ubuntu tonight in an effort to learn a new and more stable operating system since my 64 bit Vista that came with my HP Elite has been acting up.  In the process, I think instead of adding another partitian that would allow me a dual boot, I completely erased Vista and all the files on my PC and just installed Ubuntu( I think.)  

I never used anything but Windows and Mac, so I am having problems connecting to the internet and using applicants with Ubuntu, and need Vista for work but I am screwed. (using an outside laptop right now)  Maybe I should be in an HP Forum asking this, but when I got my HP, I made the back up recovery disks from the Partition all new HP's come with.  WHen I tried to recover with those disks, I get Error Warnings that this PC cannot recover with those disks.  SO basically, I have a PC with Ubuntu on it, that doesnt recognize or activate any of my drivers, or connect to the internet. Nor will it allow me to recover from the only disks HP provide.  

Am I going to have to buy Vista or something? I am clueless on what my options are here.  IDeal situation would be both OS(s) that I can jump back and forth too.  But right now, I need to find a way to get Vista either working again, or back on this PC with the recovery disks I have.  I am glad I backed everything up on my external HD before I did this but, Any advice is greatly appreciated.

---

### Post by albandy on 2009-02-27
Could you explain the process you followed to install ubuntu?
Maybe it's possible to start Vista modifiying your boot configuration.

So enter a console (applications --> accesories --> Terminal) and type there:

sudo fdisk -l /dev/sda

it will print your partitions,  paste it here.

---

