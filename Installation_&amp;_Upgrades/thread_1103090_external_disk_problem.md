---
title: "external disk problem"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by Meow27 on 2009-03-22
ok im picking up from this post here
[http://ubuntuforums.org/showthread.php?t=1092491](http://ubuntuforums.org/showthread.php?t=1092491)

here's how i set up my harddisk

1st partition is ntfs, next is a extended partition which has 2 small ext3 partitions, a swap and another larger ext3 partition.
(in that order)

i need help i installing ubuntu (and possibly other Linux distros in the smaller ones)

problem is, all of the software im using either asks if i want to sue my main harddisk or some usb drive, but doesn't recognize my external drive as either, so i don't know how to get ubuntu on without using questionable software which places a fake partition file ontop of my partitions (i dont believe in things like virtual harddisk booting if im not using a virtual machine manager)


additionally i need grub to be install on the disk's MBR and i don't want it to touch my internal disk's MBR. is there any linux or windows executable that will let me do that step smack off the bat?

thanks in advance

---

### Post by Meow27 on 2009-03-22
after further experimentation, i have found that the Ubuntu 810 live cd DOES NOT RECOGNISE ANY PARTITIONS ON MY EXTERNAL DISK. 

it just reads it as a blank, though i dont really know what it reads it as. anyhow i dont see any straight forward way of installing ubuntu on my external harddisk, help me plz! T.T

---

### Post by Meow27 on 2009-03-24
bump-de bump bump

---

### Post by Meow27 on 2009-03-25
bump

---

### Post by Claus7 on 2009-03-25
Hello,

so you are aware that this disk has the partitions you say so. What does the commands:
```
sudo fdisk -l
```
and
```
df -h
```
say?

Regards!

---

### Post by Meow27 on 2009-03-25
```
sudo fdisk -l
[sudo] password for username: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2226eb33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1594    12803773+   7  HPFS/NTFS
/dev/sda2            1595        5422    30748410   83  Linux
/dev/sda3            5423        9729    34595977+   f  W95 Ext'd (LBA)
/dev/sda5            5423        5684     2104483+  82  Linux swap / Solaris
/dev/sda6            5685        9729    32491431    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6824b6d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       33387   268181046    7  HPFS/NTFS
/dev/sdb2           33388       38913    44387595    5  Extended
/dev/sdb5           33388       34024     5116671    b  W95 FAT32
/dev/sdb6           34025       34828     6458098+  83  Linux
/dev/sdb7           34829       35089     2096451   82  Linux swap / Solaris
/dev/sdb8           35090       38913    30716280   83  Linux

```
```
username@Nebula-Class:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              30G   18G   13G  59% /
varrun                502M  112K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M  100K  501M   1% /dev
devshm                502M   76K  501M   1% /dev/shm
lrm                   502M   39M  463M   8% /lib/modules/2.6.24-23-generic/volatile
/dev/sda6              31G   18G   14G  57% /WIN_DATA
gvfs-fuse-daemon       30G   18G   13G  59% /home/username/.gvfs
/dev/sdb1             256G   21G  236G   9% /media/Dan_Data
/dev/sdb5             4.9G  938M  4.0G  19% /media/LIVE DISK
/dev/sdb6             6.2G  143M  5.7G   3% /media/disk-1
/dev/sdb8              30G  173M   28G   1% /media/disk-2

```

---

### Post by Claus7 on 2009-03-25
Hello,

can you try:

(a directory just for mounting your external drive)
sudo mkdir /media/test

(unmounting part of your ext hdd)
sudo umount /dev/sdb1
sudo umount /dev/sdb5
sudo umount /dev/sdb6
sudo umount /dev/sdb8

(mounting all of it)
sudo mount /dev/sdb /media/test

Regards!

---

### Post by Claus7 on 2009-03-25
Hello,

checking more the output of the commands you provide it seems that the partitions are slightly different from the ones you describe in your first post. The linux ones are recognised via df -h command. The ntfs one not. It would be nice to install ntfs-3g from synaptic for that to work. If the command:
sudo mount /dev/sdb /media/test
does not work
you should try to mount manually every single one partition you want specifying also the type of the partition e.g.:
sudo mount -t ntfs /dev/sdb1 /dev/test1

It seems that your pc recognises pretty well your ext hdd. 

Regards!

---

### Post by Meow27 on 2009-03-26
oh snap, did you want me to give you those values on the livecd?

i did this from my hardy install, so of course everything is normal there >.>

ill post the output of those commands on the livecd

(but ill still try doing the mounting stuff as well)

---

### Post by Claus7 on 2009-03-26
Hello,

> **Meow27 said:**
> oh snap, did you want me to give you those values on the livecd?

From hardy I suppose that you want things to work. No? What is the reason of putting inside the cd in order to recognise your hdd?

Regards!

---

### Post by Meow27 on 2009-03-26
ill explain myself again


my original intention for the hdd, was to have 1 large data partition, then several other ones to work as OSes if i decided to demonstrate, or just use a persistent linux install from my harddisk, as you can see, i wanted 2 demonstrations and one main.

the problem was, was that the ubuntu intrepid install cd did not recognize my external hdd's partitions, and the only possible way for installing ubuntu on it was to wipe it out completely (cause manual partitioning wouldn't work at all  (works fine for the internal disks though))

ill try getting the outputs for the livecd by tonight

edit- ntfs-3g was installed with the hardy installation i think

---

### Post by Claus7 on 2009-03-26
Hello,

things are better understood now. Yup, since you want to make a fresh install from the live cd to your small ext hdd partition, it would be nice to know the results from the live cd. Yet if the live cd during an installation cannot see your ext hdd partitions I do not think how this would help you to make the installation you wish...Just a check won't matter.

Have you tried this? 
[http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/)
That way it may recognise the ubuntu cd your ext hdd and allow you to manually install intrepid on the partition you want. Just check it out, it needs some work to be done though.
 
Regards!

---

### Post by Meow27 on 2009-03-26
can you explain more? i have tried the guide already.

---

### Post by Claus7 on 2009-03-26
Hello,

telepathy. I was thinking about what it was going on and there you are! Of cource coincidence. If you have tried the guide I do not think that there are a lot of things to do. Let's recapitulate:

[LIST]
[*]you have an external hdd which has many partitions
[*]in one of them you want to install intrepid
[*]you put the cd, you connect the hdd and you see that you cannot format the hdd to your big disappointment
[*]you can format it, yet not manually, which means that you have to say good bye to all your partitions
[/LIST]

I sent you this guide in which I supposed that removing temporarily your internal hdd, the ubuntu cd might recognise your ext hdd and format it. Yet, you say that you can't. Another idea should be to mount the partition you want via the cd, yet I have no idea how you would be able to install the operating system there...

This is what I meant...

Regards!

---

### Post by Meow27 on 2009-03-28
k i tried it with the jaunty livecd.

from what i understand, the livecd recognizes the partitions from the terminal commands, but does not recognize any usage (empty drive no partitions) with all of the graphical partition managers inside the gui.

---

### Post by Claus7 on 2009-03-30
Hello,

if I have understood you correctly (I'm not the best mind in the world, far from it) you can format your ext hdd, yet without the graphical environment. Go for it. I do not think that this is a big deal. No matter what, have a backup or whatever. If you mess with such things it is sometimes unavoidable to make a mistake and loose data. 

1. If you use the cd you have and as you say you are able to see the partitions via command line, I 'm still telling you that I do not know how to install the operating system. I do know how to format the partition you want. 

2.If it is the case as you describe it, then I would suggest you to try something more. Go there and download the alternate cd, which will enable you to install the operating system via command line.
[http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate](http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate)

Here what I suggest you from the information you provide is: combining the ability to have a cd which will recognise your ext hdd with its partitions and also to be able to install the os via command line.

Are you sure that you are doing all the procedure correctly? You mentioned that you have followed a guide I had sent you as a link. Are you sure that you did what this guide told you to do? How are you sure that the jaunty cd recognises your ext hdd? Are you sure that this drive is working properly?

Regards!

---

