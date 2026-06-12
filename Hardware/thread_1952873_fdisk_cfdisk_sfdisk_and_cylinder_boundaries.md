---
title: "fdisk cfdisk sfdisk and cylinder boundaries"
date: 2012-04-05
forum: Hardware
---

### Post by experimenterr on 2012-04-05
[SIZE=2]Hi,

this is rather a hardware-related question, regarding [/SIZE] [SIZE=2]*proper partitioning* for a 'recent' :) system for dual-booting ubuntu and win7 (both of them 32-bits)

The system is a [/SIZE] [SIZE=2][Fujitsu-Siemens Amilo Pi 1536]("http://www.notebookreview.com/default.asp?newsID=2903") with 2GB RAM and 120GB HDD

Since I dislike graphical partitioning tools, I use console-based tools, such as[/SIZE] [SIZE=2][fdisk]("http://manpages.ubuntu.com/manpages/lucid/en/man8/fdisk.8.html")[/SIZE] [SIZE=2], [cfdisk]("http://manpages.ubuntu.com/manpages/lucid/en/man8/cfdisk.8.html"). [sfdisk]("http://linux.die.net/man/8/sfdisk").

However when I partition the disk with fdisk, sfdisk -V outputs annoying complaints on stderr such as:[/SIZE] [SIZE=2]

"Warning: extended partition does not start at a cylinder boundary.[/SIZE] [SIZE=2]
DOS and Linux will interpret the contents differently."
...
"end: (c,h,s) expected (1023,254,63) found (40,202,34)"


Is that OK? Should I care about this (obsolete?) warning?[/SIZE]  [SIZE=2]

Disk data is attached. Fdisk, sfdisk outputs are also attached:[/SIZE] [SIZE=2]
[/SIZE]
[LIST]
[*][SIZE=2]in the first case I used normal, standard fdisk, for what I got the above warnings ("different interpretation" message even with sfdisk -L -V (-L for lba)[/SIZE]
[*][SIZE=2]in the second case I used sfdisk --DOS --IBM to partition the disk, however the result looks kinda ugly :([/SIZE]
[/LIST]
[SIZE=2]
I have found some documentation regarding this in the [Large-Disk-HOWTO]("http://tldp.org/HOWTO/Large-Disk-HOWTO-6.html"), and in another thread [oldfred says that this would not matter]("http://ubuntuforums.org/showpost.php?p=10199147&postcount=7"), now where do I found some detailed docs on this or file a bug report for sfdisk/util-linux(-ng)?

I am currently using sysresccd 2.5.1 for partitioning. 
My goal would be to build an ubultu10-and-win7 dual-boot system with the following partition structure:

16G Linux primary, 48G win7 primary active/bootable, 2G Linux swap primary, extended containing: 2G win swap, and the remainder (~50G) as ntfs data partition for common use.


Another question: what is this thing with [kilobytes and kibibytes?]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/874239") What to enter to fdisk if I would like to create a partition that is not more nor less than 2GB (2x 1024MB...) 

Thank You!


[/SIZE]

---

### Post by Paddy Landau on 2012-04-05
I always use gparted, as it works so well. For every partition process, it has an option to align on a cylinder, which I always choose.

I presume that parted, fdisk, etc. must have an equivalent option.

---

### Post by experimenterr on 2012-04-05
[SIZE=2]Hmm, [gnu parted]("http://manpages.ubuntu.com/manpages/lucid/en/man8/parted.8.html")... It is included on [Parted Magic]("http://partedmagic.com/doku.php") Live CD as well... Seems nice!

I have not tried this before, since I stuck at (c)fdisk et al but see that it has the --align option, great!

OK, I will give parted a try and see what sfdisk --verify says.

[/SIZE][SIZE=2]Thanks for Your hint & reply![/SIZE]
[SIZE=2]
Any other opinion about s[criptable]fdisk and detailed docs on this topic?
[Sfdisk still seems to be under active development]("https://github.com/karelzak/util-linux/commit/26f0feac990cbd93d3f3b903bb4c9376ae8cb5f7").
[/SIZE]

---

### Post by experimenterr on 2012-04-05
[SIZE=2]Hi,
[URL="http://ubuntuforums.org/showthread.php?p=11819043"]
this might be an installation question[/URL] rather than hardware-related, please take a look at it, thanks!
[/SIZE]

---

### Post by oldfred on 2012-04-05
Thread merged back, Please do not start two threads on same topic. If you really think it is wrong use report abuse (not just for abuse, to to call attention) to get an Moderator or Admin to move it.

I stand by that today it does not really matter for cylinder alignment.

More info - mostly on newer 4kb drives:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

> **Tip:** If you want to dual-boot between Linux and an older operating system that requires cylinder alignment, try aligning the starts of all your partitions on multiples of eight cylinders. This translates to 8-sector alignment for optimum disk performance as well as cylinder alignment for the older operating system.

---

