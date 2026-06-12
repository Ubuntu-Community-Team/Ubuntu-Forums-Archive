---
title: "Grub loader on External Hard Drive"
date: 2008-10-23
forum: General Help
---

### Post by kr4zyc1d on 2008-10-23
Hello all,  I am in need of some help here as I have been scratching my head for quite a while on this problem.  Here is my basic setup:
I have a Dell Inspiron E1505 tri-booting XP, Ubuntu, and MacOSX86.  Now, I have been setting those up for a while, and every so often an update or install of a new operating system will take place, in which case I must pull out a stack of CD's that I have been carrying with me for the past month or so.  

I then had this brilliant idea: Take an external Hard Drive (a spare 2.5 inch that I have lying around) and break it into 5 partitions (Grub, XP, Ubuntu, Mac, and Extra).  My goal is to be able to boot to the external HD and have grub control all of my partitions, in the sense that there will not be operating systems installed on these partitions but simply the Installer files on each respective partition.  In easier terms, I would like to have a boot (live) cd of each operating system stored on the respective partition and be able to call it using grub.  I am well aware and have successfully booted and installed Ubuntu via USB but it has always just started with that.  I would like a grub loader to show me the options of installer CD's that I have to not only make it simple, but incredibly fast, efficient and no more CD'S!!!  

Thus far, I have successfully copied all grub information into the grub partition and can boot to the USB, and when I do, I get the grub option list to pick from my partition (I have set up my menu.lst)  I have also setup the Ubuntu partition as per a tutorial on Live USB disks.  However, when I choose the grub menu item I get many errors (I change the menu.lst readily while booted and continue trying) of them [Error 17, 19, 1, 8... etc] to name a few.  

Either way, does anyone know how to do this successfully.  I have a good thought in mind and would really like to wrap this up soon.  I have heard thoughts of using BartPE to control the windows partition, and using Mac Recovery in Disk Utilities to set that partition up, but I do not want to go filling this thing up and formatting it every few minutes just to try something new - (i.e., lets do one OS at a time to keep things simple and fast, and then put it all together at the end)

Thanks in advance for anyone who can help out with this project, it will be greatly appreciated and I am willing to write a tutorial on this subject once I can put it to bed.  Thanks again.

---

### Post by kr4zyc1d on 2008-10-24
I have a few more details:
External HD is listed as sdb, hd1
Grub     sdb1   hd1,0
Linux    sdb2   hd1,1
Windows  sdb3   hd1,2
Mac      sdb4   hd1,3
Extra    sdb5   hd1,4

Those are the labels and disk/partition numbers if they are any more help for figuring this out.  Thanks.

---

### Post by bapoumba on 2008-10-25
Mac software should only be installed on Apple hardware. Closing the thread, sorry.

---

