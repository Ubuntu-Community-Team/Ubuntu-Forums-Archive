---
title: "Xp and Ubuntu Problems"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by ardain on 2009-09-06
My computer is a Dell Inspiron 640m and I am a complete sort of new to Ubuntu.


 My Problem:
 I had Windows XP on the computer before I installed Ubuntu with an old 8.10 live cd.
After I installed Ubuntu, i Upgraded to 9.04. Then, when I rebooted to see if Xp still worked, in the GRUB boot loader, XP wasn't even in the menu. I didn't delete any Windows partitions, so i don't know what happened.:confused:Please help. This Dell is my personal use computer so I'd be glad to get a reply soon.
 Thanks in advance!

~Ardain

---

### Post by estebarb on 2009-09-06
It happens mostly because XP is not already in GRUB menu, but it is alive somewhere in your disk, don't worry. You should add it to menu.lst, that is in /boot/grub/menu.lst. You must use root powers to do it, but first you/we need some information.
How many hard disks have your computer and in which partition is installed XP and Ubuntu?

Some time ago "presence1960" help me with a little problem, I'm going to cite his post:
> Boot into Ubuntu or from the Live CD. When the desktop loads download to the desktop [Boot Info Script 0.32]("http://sourceforge.net/projects/bootinfoscript/"). Then open a termimal and run this command:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. paste the contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. This info will show us your partition table, boot info & other useful info about your setup.
__________________
[Boot Info Script 0.32]("http://sourceforge.net/projects/bootinfoscript/") courtesy of forum member meierfra


Any question with it, post it. We will wait for your RESULTS.txt to help you better.

---

### Post by Bucky Ball on 2009-09-06
```
title         Windows 95/98/NT/2000
root          (hd0,0)
savedefault
makeactive
chainloader   +1
```You need to add something like that to your /boot/grub/menu.lst where 'root (hd0,0)' = your Windows install partition.

Run:

```
sudo blkid
```... and figure out the 'sda*' of your windows drive. 

hd(0,0) = sda1; (hd1,0) = sdb1

hd*,* counts from zero and sd* counts from one. Hope that makes some sense.

---

### Post by ardain on 2009-09-06
> **estebarb said:**
> It happens mostly because XP is not already in GRUB menu, but it is alive somewhere in your disk, don't worry. You should add it to menu.lst, that is in /boot/grub/menu.lst. You must use root powers to do it, but first you/we need some information.
How many hard disks have your computer and in which partition is installed XP and Ubuntu?

Some time ago "presence1960" help me with a little problem, I'm going to cite his post:

Quote:
                                                 Boot into Ubuntu or from the Live CD. When the desktop loads download to the desktop [Boot Info Script 0.32]("http://sourceforge.net/projects/bootinfoscript/"). Then open a termimal and run this command:

     Code:
     sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file on the desktop. paste the contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. This info will show us your partition table, boot info & other useful info about your setup.
__________________
[Boot Info Script 0.32]("http://sourceforge.net/projects/bootinfoscript/") courtesy of forum member meierfra                      


Any question with it, post it. We will wait for your RESULTS.txt to help you better.

@Estebarb:I have 1 hard disk in my computer and my total hard disk space is 80.93 GB. The XP partition is 35.38GB and the Ubuntu partition is 35.87GB.

And, I dont really know what you mean by booting in to Ubuntu with the Live Disc. Is there an option in the menu? Because i let my friend borrow the disc, i wont get it back anytime this month. Is there anyway that i can fix my computer withour the disc?


@Bucky Ball: I don't really know what you mean. Sorry, I'm not the best with computers :confused:

---

### Post by Bucky Ball on 2009-09-07
Could you open a terminal (Applications->Accessories->Terminal) and paste this in:

```
sudo blkid
```

Copy and paste the result here. :)

---

### Post by ardain on 2009-09-07
haha, sorry about this, but I already got a reply and fixed the problem. Sorry for the late notice, but thanks though!
:lolflag::popcorn:

---

### Post by ardain on 2009-09-07
reply From another forum:P i mean

---

