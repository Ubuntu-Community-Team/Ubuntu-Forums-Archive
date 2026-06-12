---
title: "Problem uninstalling/reinstalling after first install failed"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by AcousticMinja on 2009-06-23
Hi all, I am quite new to Linux. I've heard about Ubuntu/Kubuntu for a while and I decided that I would try it for myself. I recently received a new hard drive and decided I would dual boot Vista and either Ubuntu or Kubuntu (whichever I got first). I downloaded wubi and tried installing Kubuntu from there. I made the huge mistake of clicking on my E: drive which had windows 7 on it. I cancelled the installation after I realized what I did and then restored my computer to the settings right before my installation attempt. I received my Kubuntu CD and decided to install from there(just incase wubi didn't work). I was given the option to boot from the CD to install on a separate partition...I clicked that and checked "reboot now". After that, I clicked finish hoping it would automatically restart. Nothing happened. So then I tried clicking "help boot from CD"...then the error message came up saying that a previous version of Ubuntu was installed on my E: drive and it would'nt let me install Kubuntu on my F:drive. I searched the forums and found a link to this program that allows you to uninstall ubuntu. After opening, nothing happened. I tried doing the same thing a few times and I got the same outcome. I assumed maybe it already worked. So then I tried installing again and I received the same message. I looked in my E: folder and I can't find E:/ubuntu or anything. Is there something I forgot to do? Or should I reformat my E:drive? 
Please let me know what I should do. 
Thank you for your time! :)


*update*
I reformatted my E: and F: drives and attempted to install again...the same exact error message comes up. This is getting very frustrating.

---

### Post by presence1960 on 2009-06-23
are your windows partitions booting? If so I suggest you do some reading to familiarize yourself with what it is you are trying to do prior to actually trying to install Ubuntu/Kubuntu. Here are some links:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  -for a free pdf Ubuntu pocket Guide which has a great step by step overview of the installation process.

Don't go formatting anything yet! what is the setup of each hard disk and the partitions on each disk. if each disk/partition is dedicated to windows you may need to create a new partition to install Ubuntu to. That is unless you want to lose the data on the partition you install Ubuntu to. Why don't you familiarize yourself with the install process first, then report back your disk & partition scheme so we can help you get this installed.

Installing a new OS should not be taken lightly, especially if one has never done it before. Restoring windows from a recovery CD/DVD or recovery partition does not count because it automatically sets the partitions and installs all the drivers for you. Now if you have installed windows from a Windows installation CD/DVD you know the difference.

---

### Post by Sef on 2009-06-24
Use the Live CD and open a Terminal (GNOME) under accessories or Konsole (Kubuntu), and copy and paste this command:

```
sudo fdisk -l
```Then copy and paste the results here.

---

