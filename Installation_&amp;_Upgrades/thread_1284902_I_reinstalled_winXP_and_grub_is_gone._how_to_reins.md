---
title: "I reinstalled winXP and grub is gone. how to reinstall grub?"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by anomalous_underdog on 2009-10-07
I have a dual boot windows xp and ubuntu 9.04. I reinstalled the windows xp part and it removed grub and instead it now boots straight into windows so I can't access Ubuntu anymore.

How do I reinstall grub while keeping my current ubuntu installation intact?

---

### Post by callan79 on 2009-10-07
> **anomalous_underdog said:**
> How do I reinstall grub while keeping my current ubuntu installation intact?


Don't you love how Windows just takes over the whole PC?

Good news is that it's easy to fix.

There's a few guides on the ubuntu.com website - go to [help.ubuntu.com](http://help.ubuntu.com) and search for "restore grub".

I do have a guide on my own website - mainly for my own use since I had to use it so often in the past - [http://flog.cruzn.net.au/articles/restore-grub.shtml](http://flog.cruzn.net.au/articles/restore-grub.shtml)

All the best!
Callan

---

### Post by Partyboi2 on 2009-10-07
Hi, you can boot a ubuntu live cd and follow [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") to restore grub.

---

### Post by howefield on 2009-10-07
In addition to callan79s' advice, I'd add that it is worth taking an image of your disk using something like Clonezilla.

Making an image of your drive once you have set it up and got it "pristine" means reinstalling partitions/disks is a breeze.

---

### Post by Zoot7 on 2009-10-07
```
sudo grub
find /boot/grub/stage1
root (hdx,y) - where (hdx,y) is the output of the find command
setup (hd0)
```

That'll re-install grub to the mbr for you. :)

---

### Post by anomalous_underdog on 2009-10-07
> **callan79 said:**
> 
I do have a guide on my own website - mainly for my own use since I had to use it so often in the past - [http://flog.cruzn.net.au/articles/restore-grub.shtml](http://flog.cruzn.net.au/articles/restore-grub.shtml)

All the best!
Callan

In your guide it says 
> Type "setup (hd0)" (again, change the zero depending on what the above results were)

I found this to be wrong. It really should be "(hd0)"; the zero shouldn't be changed

---

### Post by presence1960 on 2009-10-07
> **anomalous_underdog said:**
> In your guide it says 


[B]I found this to be wrong. It really should be "(hd0)"; the zero shouldn't be changed

that is not necessarily true.[/B] My sdc disk boots first and contains Ubuntu & windows. When I set up GRUB it is setup (hd2). The reason being is that GRUB and BIOS read the order of disks differently. GRUB uses the output from fdisk -l. which in my case is sdc (hd2). But in BIOS my sdc boots first.

So in conclusion there is no hard & fast "rule" as to what setup (hdx) should be, it depends entirely on your setup. If you only have one hard disk then obviously it is  setup (hd0), but with multiple disks depending on your setup that may change. here is my setup:

raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85858585

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2368a10a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02020202

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sdc2            5223       10444    41945715    5  Extended
/dev/sdc5            5223        5744     4192933+  82  Linux swap / Solaris
/dev/sdc6            5745        8094    18876343+  83  Linux
raz@raz-desktop:~$ 

sda is a data ext 3 partition
sdb is an ext 3 partition for backups & images of my partitions & OSs
sdc has windows & ubuntu on it.

GRUB is on sdc. sdc boots first in BIOS, but fdisk reports it as 3rd disk. So when I run sudo grub I get:
> 
raz@raz-desktop:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,5)
grub> root (hd2,5)
root (hd2,5)
grub> setup (hd2)
setup (hd2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+17 p (hd2,5)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> 

Setup GRUB is setup (hd2) because that is the first disk to boot in BIOS. If I put it as setup (hd0) GRUB would not take over on boot because (hd0) does not boot first in BIOS. So you see it depends entirely on your setup what the x is in setup (hdx)

---

