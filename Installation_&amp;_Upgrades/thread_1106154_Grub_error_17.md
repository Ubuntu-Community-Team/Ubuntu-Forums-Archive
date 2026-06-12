---
title: "Grub error 17"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by Erik. on 2009-03-25
Hello ubuntu users,

I have a problem running ubuntu.

I have 3 hdd's 

1) 160 Gig
2) 200 Gig
3) 640 Gig

On the first one i have windows installed, whit some partitions.
On the second one i have ubuntu installed.
The last one is just data hdd.

I wanted to boot my computer to windows, it was crap, why i don know i get a bleu screen every time i restart my computer.

I wanted to boot linux, did not boot.
Installed ubuntu again but i got an error, grub error 17.

I have read that you need to set the hdd to auto and not large, lost the name of the setting, you need to set it into the bios.

All the settings are good.
Now i also read something about the hdd's and ubuntu, it does not know how to boot?

Now i still have my error and i am trying from Saturday.
I am out of hope and want to ask for help.

i am running he lice CD now.

opend terminal and here is some output:

fdisk -l:

```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3488a202

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77825   625129281    7  HPFS/NTFS

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01992018

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2551    20490876    7  HPFS/NTFS
/dev/sdb2            2552       19929   139588785    5  Extended
/dev/sdb5            2552        6377    30732313+   7  HPFS/NTFS
/dev/sdb6            6378       10203    30732313+   7  HPFS/NTFS
/dev/sdb7           10204       14029    30732313+   7  HPFS/NTFS
/dev/sdb8           14030       19929    47391718+   7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x625002f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24037   193077171   83  Linux
/dev/sdc2           24038       24792     6064537+   5  Extended
/dev/sdc5           24038       24792     6064506   82  Linux swap / Solaris

```

output from: cat /etc/fstab

```

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdc5 swap swap defaults 0 0

```

I have installed ubuntu on the 200 Gig hdd and made the bootloader on the 160 Gig.

Hope you can help me.

Edit: When i boot on my 160 gig hdd i see the word grub all over my screen.

---

### Post by MountainX on 2009-03-25
The problem sounds like your HDD identifiers are switching. This is common in setups like yours. It is easy to solve, but you have to become familiar with how drive idents are assigned in grub and then in Ubuntu (they are not the same).

check out this post:
[http://ubuntuforums.org/showpost.php?p=6811432&postcount=6](http://ubuntuforums.org/showpost.php?p=6811432&postcount=6)

then maybe see this one: 
[http://ubuntuforums.org/showpost.php?p=6811755&postcount=8](http://ubuntuforums.org/showpost.php?p=6811755&postcount=8)

This is my learning experience with this problem:
[http://ubuntuforums.org/showthread.php?t=1080832](http://ubuntuforums.org/showthread.php?t=1080832)

---

### Post by Erik. on 2009-03-25
Thanks for your fast replay!

I uploaded the txt file mabey you can help me a bit?

Do not know what to do whit the file and information.

---

### Post by MountainX on 2009-03-25
Hopefully caljohnsmith will look at the uploaded results. He's the guy who helped me.

Have you considered temporarily removing the Windows disk? You could install Ubuntu on one disk and make sure your data disk is seen after the OS disk (in BIOS). Make sure the Ubuntu disk is the first HDD in the BIOS.

I know others can tell you how to do it without removing a HDD, but I'm offering a very simple approach that may be just something you can do temporarily to make some progress and to learn how this works.


EDIT: after looking at your results, you have a very complex setup with lots of partitions. If you are new to Linux, this may be a complex task to resolve without some good help from the forum. It is over my head. It would be a lot simpler if you remove all but one disk and let Ubuntu use the whole disk. You'll get it installed in a snap. Then, as a next step, you could carefully add your data disk and use the bootinfoscript to track the changes. Run it each time you add something.

---

### Post by Erik. on 2009-03-25
I am not new to ubuntu but i am not pro.

I will pull out my other hdd's and install it again.
Try to run it and every time put an hdd to my computer hope the problem will resolve.

Thanks for looking.

wow, can't believe it!

What i did :
```

sudo grub
grub> device (hd0) /dev/sdc
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```

And i tried to boot and it works fine!
I am now in the installed ubuntu.

Can you now tell me what i did wrong or what did goes wrong and how i can resolve it.

---

