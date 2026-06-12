---
title: "[SOLVED] grub on permament error 17"
date: 2008-11-03
forum: General Help
---

### Post by jaems-kun on 2008-11-03
Kay, I'm still super new at multiple operating systems so this has been a mad adventure for me.  Here's the long story short:
I crashed my acer laptop with vista a while back so I decided to take advantage of the situation and use the whole hd for xubuntu.  (I actually didn't have much choice since I couldn't find the vista install cds).  

That was fine for a while, but I'm greedy and like the idea of having more operating system options for my laptop so I eventually get ahold of an xp install disc. I partition with parted magic and install xp.  Great, except like the typical n00b at this, I messed up grub and can't get back into xubuntu.  I'm pretty sure I've exhausted all the help google can give me, or at least my patience with google's help (live cd>grub>root>setup>hd0,2,blah blah, no change), so I'm now asking directly for help.  

My current partition scheme is sda1=35gb ntfs (windows was here, now its blank because I had hoped erasing the partition would bring back xubuntu)  sda2=93gb ntfs (blank, for media)  sda3(*boot)=20gb linux (xubuntu) sda4+5=2gb swap.  

Perhaps a bit of beneficial information: for some reason "sudo nano /boot/grub/menu.lst" (or grub.conf) doesn't bring anything up for me.  Could this be my problem or am I just not looking in the right spot?

Any help appreciated.  Hope my provided information is adequate. I've spent the last two days trying to fix this so I'm pretty tired from going around in circles on google.

---

### Post by thestig_992 on 2008-11-03
use live cd to reinstall grub, google seach that. Also, gparted on the live cd will help you get rid of that empty ntfs partition.

---

### Post by TeXtonyx on 2008-11-03
When you install Vista or XP, they write to the Master Boot Record
(MBR). Linux can install to the MBR, or the /boot partition, and
the default is to the MBR. So whichever OS you installed last, has
written to the MBR which controls the booting. 

To get Xubuntu booting again one can download and burn Super Grub
disk. Run Super Grub with 'help' enabled so that your options are
explained to you as you go along. Super Grub helps you write the
Linux boot code to the MBR.

---

### Post by mdurham on 2008-11-03
> **thestig_992 said:**
> use live cd to reinstall grub, google seach that. Also, gparted on the live cd will help you get rid of that empty ntfs partition.

That's okay as far as it goes but, he has probably moved the Ubuntu install to a different partition from it's original (not actually sure). If he has, he might need to adjust it's fstab as well.

---

### Post by jaems-kun on 2008-11-03
Originally, it was all one partition and xubuntu had it all.  Now xubuntu is on sda 3, or hd0,2 and it still worked fine up until I installed windows.

I have reinstalled grub a couple times.  I've tried to "setup" both (hd0) and (hd0,2), but I get error 17 on all of them.

I've used supergrub too.  In automatic mode, manual mode and "advanced".  It always says it works, but I never get passed an error 17.

Thanks for your suggestions.

---

### Post by caljohnsmith on 2008-11-03
When you get the Grub error 17 on start up, do you get it before seeing a Grub menu, or after getting the menu and selecting an OS? 

Also, from your Live CD, how about first posting:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by jaems-kun on 2008-11-03
Yes sir!
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe426e426

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    73400984    36700461    7  HPFS/NTFS
/dev/sda2        73400985   264622679    95610847+   7  HPFS/NTFS
/dev/sda3       264622680   306568394    20972857+  83  Linux
/dev/sda4       306568395   312576704     3004155    5  Extended
/dev/sda5       306568458   312576704     3004123+  82  Linux swap / Solaris

```

I get the error before I get to the menu, then it says "press any key" which takes me to the menu (windows doesn't show up on the menu, if that means anything) but I still get error 17 if I try selecting one of the options.

I reinstalled windows once more, so that's why my table is a bit different than the info in my first post.

---

### Post by caljohnsmith on 2008-11-03
That sounds really strange you get the error 17 before getting the Grub menu, yet pressing any key takes you to the Grub menu. How about when you get the Grub menu, select the first Xubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. That might be all it takes to boot Xubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. Let me know if that works, and if it doesn't, we can work from there. :)

---

### Post by jaems-kun on 2008-11-03
Brilliant!  I've saved the menu.lst and now things are better than ever, Thank you so much!

---

### Post by caljohnsmith on 2008-11-03
> **jaems-kun said:**
> Brilliant!  I've saved the menu.lst and now things are better than ever, Thank you so much!
You're welcome, and I'm glad that it turned out to be a simple problem. Cheers and have fun with Xubuntu. :)

---

