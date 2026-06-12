---
title: "Hard disk upgrade, SATA"
date: 2006-01-20
forum: Hardware &amp; Laptops
---

### Post by hamil on 2006-01-20
Hello!

I have bought an SATA hard drive today.. Western Digital, 320 GB.
I have installed it, but have no clue to how I can mount it? Is there any special things I should do before i proceed with the mounting? Any special modules that needs to be installed??

My /etc/modules/ shows this output:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq
nvidia

```

And the df -h shows this info:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             8.3G  2.9G  5.0G  37% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-9-386/volatile
/dev/hda6              52G   43G  6.4G  87% /home
/dev/hda1              12G  8.9G  2.9G  77% /media/hda1
/dev/sda1             233G  209G   25G  90% /media/sda1

```

And none of these are my new SATA drive..

Thanxs in advance!
Lasse

---

### Post by LordBug on 2006-01-20
> /dev/sda1             233G  209G   25G  90% /media/sda1
You have 2 SATA drives then?  With this showing up, it tells us you have the SATA module loading.  You should just need to partition (fdisk) and format the new hard drive, and then add the necessary line into /etc/fstab to auto-mount.

---

### Post by hamil on 2006-01-20
Nope.
It is not two SATA hard-drives. The one showing up as SDA1, is my external USB2.0 Hard drive.
But how do i find my new SATA hard drive, when I enter the menu for "Disks", it does not show up there. I am not able to find it, so I do not now how to format it..

Is it possible to me, at this point, to make my new SATA hard drive work as my Home disk? Or is it maybe easyer to make a clean install again??

---

### Post by Ocxic on 2006-01-20
your new SATA disk is prolly sdb not sda so try:
[code] 
sudo mkidir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1 (if this doesn't work then you'll have to format it. do you have gparted it's in the repositories, open up gparted and see if the new disk is there.

---

### Post by hamil on 2006-01-21
Well I have tried to mount it the way it is stated in your replie, but then I get the error message, that I have to mount it with an filesystem.
When I try to do so, it states that:
```
mount: special device /dev/sdb1 does not exist
```

I have also installed gPart, but iy does not see my SATA Hard drive. (It recognise all other drives on my machine)

What to do now???

---

### Post by hamil on 2006-01-21
No ideas anyone???

Well, to clarify it all:
This is a new internal Hard Drive that I recived in the mail. It is probably not formatted yet, so that would seem like an good idea to me to do, but I do not know where I can find it, and how I can use gPart to format it, when I find it.

Any help would be appreciated..

---

### Post by dlafary on 2006-01-30
Does your bios even recognize the hard drive? Western Digitals are notorious for having issues on some motherboards. Some times you have to change the heads,cylinders,sector parameters in the bios.

---

### Post by pedrobl on 2006-02-06
[QUOTE=hamil]When I try to do so, it states that:
```
mount: special device /dev/sdb1 does not exist
```
[/QUOTE]

Do you have a /dev/sdb device file? You can use MAKEDEV:
```
# ls -l /dev/sdb
ls: /dev/sdb: No such file or directory
# MAKEDEV /dev/sdb
# ls -l /dev/sdb
brw-r-----  1 root disk 8, 16 feb  7 03:14 /dev/sdb
```

You can also try ```
dmesg | less
``` and search for informatión about your disk (you need the device file name). That command should show you the same information as what you see when you boot your system. All devices should up in that file: hard disks, network cards, etc...

Good luck,

Pedro.

---

### Post by hayalci on 2006-02-15
This command should display all drives and partitions that your machine can see. From there, you may learn the name of your new disk ( probably it is /dev/sdb and previous advice didn't work out because there are no new partitions on it called sdb1 )

```
fdisk -l
```

If you see the disk there, use "fdisk /dev/sdX " (replace X with the letter you learned in the previous step.) to enter fdisk. Then create new partitions on it. Using fdisk is pretty easy, you just have to press some keys, 'm' tells you what to press. 'n' for new partition, you select place and size. 'p' prints your current partitions and you write changes by 'w'. 

If you do not see your disk in the first place, look at dmesg output and determine the problem, It would be a driver problem probably.

---

### Post by tseliot on 2006-02-16
[QUOTE=hayalci]...If you do not see your disk in the first place, look at dmesg output and determine the problem, It would be a driver problem probably.[/QUOTE]
If that's the case you might need to recompile your kernel with the support for your SATA controller (unless it's already built in your current kernel)

---

