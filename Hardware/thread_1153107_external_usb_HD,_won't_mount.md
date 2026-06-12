---
title: "external usb HD, won't mount"
date: 2009-05-08
forum: Hardware
---

### Post by Ber P on 2009-05-08
I've just upgraded to 9.04 and hoped that my trouble with my external maxtor 5000 HD would be gone, but sadly it isn't.

Starting in 8.10 my external HD wouldn't mount anymore. It worked fine in previously releases, and it works fine under XP. After searching this forum, I found that it was a bug in 8.10 and it would be fixed in future relases - but it still dosn't work.
Has anyone sugestions?

dmseg gives this result: ```
[ 2228.305622] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[ 2235.801471] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 2235.801482] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[ 2242.541260] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 2242.541271] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[ 2249.480437] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 2249.480448] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information

```

lsusb returns this:

```
:~$ lsusb
Bus 001 Device 005: ID 0d49:5020 Maxtor Mobile Hard Disk Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 03f0:2f11 Hewlett-Packard PSC 1200
Bus 004 Device 002: ID 046d:c503 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

It's Device 005. 

sudo fdisk -l doesn't show the drive at all.
I've made sure to safely remove the drive from windows when I've removed it.

---

### Post by DJYoshaBYD on 2009-05-08
try and mount it using your fstab file...

i usually mount like this 

open a terminal
```
sudo gedit /etc/fstab
```

then you will see a file... at the bottom of the file is where we do this..

find out which dev your HD is on..... sda1, sdb1, etc etc.. i forget how to check this, though..

go back to your terminal.. we will make a folder to mount that drive to
```
sudo mkdir /media/maxtor
```

then, go back to your open gedit file, and type the following at the bottom..

```
/dev/sdb1      /media/maxtor    ntfs-3g   defaults      0         0
```

make sure you make sdb1 whatever your drive is.. it could be sda2, sdb2, etc etc etc... 

could someone else chime in and tell us how to check that again?

but yeah.. after you edit fstab, then save and close it.. I usually restart to see if it picks it up from boot.. it should, if you got the right device listed (sdb, sda, etc).. I use this method to perm mount my internal ntfs drive in my myth box...

anybody feel free to step in and give us a hand, here.. lol

---

### Post by Ber P on 2009-05-08
I don't think it get's a sd_ name. I think I should be able to see it with fdisk then. The other drives are named here.....

---

### Post by DJYoshaBYD on 2009-05-08
well, it will not hurt to try.. lol.. at lease go through a few of the SD_ names and see if one of them works... I mount my kingston thumbstick like this when it wants to be picky on certain machines... 

im sure how else.. most of the time, my drives are all plug and play, unless its internal.. then I usually have to force mount..

---

### Post by Ber P on 2009-05-08
hmmmmm.....tried with sdb1, sdb2, sdc1, sdc2..... no luck. 
I think the trouble is the >>[sdb] Sense Key : No Sense<< part of the dmesg. I'm not saying that I understand anything of these log's, but it looks like it can't recognize the drive. But how come it shows up in the lsusb list??? And why did it stop recognizing it in 8.10? 
AAaaarghhhh... this is getting frustrating.

---

### Post by DJYoshaBYD on 2009-05-08
well, it should work fine.. i mean, i have never really had a problem with USB drives at all... so, i dont know.. it showing up, but i dont know.. any drive should get assigned a sd_ type dev name.. then the dev is mounted to a folder, and there ya go.. try downloading ntfs-tools in your repositories... it may enable read/write and mount for it.. cause with 8.04.1 and up, i have seen it just flat out make a folder and mount it automatically..

maybe try reinstalling ntfs-3g and see if that helps.. just got synaptic, and search ntfs, and download a few things, and update your system if it needs it... im not sure why it wouldnt pick up your drive...

---

### Post by Ber P on 2009-05-08
It works fine with my USB stick (also ntfs formated). I've read about it being a bug with some devices in 8.10. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960) , but I'm not sure if the bug report is still open?!?! 

Anyway, I'll give the ntfs updating a go. I'll be back shortly....

---

### Post by DJYoshaBYD on 2009-05-08
it probably is a small bug, but honestly, I havent noticed that with any hardware yet in 8.10.. it seems to be about as good as 8.04 in terms of compatibility and stability..

give that a try, and then run that "ntfs-configuration tool" and enable both check boxes.. restart, with the device unplugged, then try and plug it in and see if it works..

---

### Post by Ber P on 2009-05-08
I can't find any ntfs stuff i Synaptic, which is not installed. 
Since the behaviour is so similar to my 8.10 installation, I suspect it is a kernel thing (as mentioned in the bug - but it looks like it is closed even though the later posts are confirming trouble in the new kernel also)?!?

---

### Post by Ber P on 2009-05-08
hmmmm.... the ntfs configuration tool makes something wierd now. When trying to enable write support it hits me with an error about my ntfs installation. I've tried to re-install as it suggests - but it changes nothing. Maybe my installation is indeed in trouble.....

---

### Post by DJYoshaBYD on 2009-05-08
well, try reinstalling ubuntu, but use 8.10 or 8.04... 9.04 is just buggy, and thats all there is to it.. im willing to bet money, if you downgrade even just to 8.10, it will work fine..

---

### Post by Ber P on 2009-05-08
I think I'll stay with 9.04 for now, and just use my external drive from a VirtualBox XP session. Guess I'll try and look into the bug repports.
Thanks for your help! It has been exceptionel quick response!!

---

### Post by DJYoshaBYD on 2009-05-08
ok.. but, as you can see, everyone is having issues with jaunty... all your problem will most likely go away if you downgrade... dont be scared to.. back up your stuff, spend 30 minutes, and try it... id be willing to be cash it would help... lol

but, good luck with jaunty.. im sticking with the ones that work.. keep us posted if you find a solution, hombre..

---

### Post by Ber P on 2009-05-11
Hmmmm.....after hours of googling and snooping around on launchpad etc., I found that the problem is caused by a kernel bug. There are some workarounds messing around with files in /etc/udev/rules.d. I got close to a solution with this workaround from the RedHat forum ([https://bugzilla.redhat.com/show_bug.cgi?id=473017):](https://bugzilla.redhat.com/show_bug.cgi?id=473017):)

```
sudo cp /lib/udev/rules.d/60-persistent-storage.rules
/etc/udev/rules.d/60-persistent-storage.rules

edit: /etc/udev/rules.d/60-persistent-storage.rules

change line 62 from: KERNEL!="sr*", IMPORT{program}="vol_id --export $tempnode"
to: KERNEL!="sr*", ENV{DEVTYPE}=="partition", IMPORT{program}="vol_id --export
$tempnode"
```

After this, the drive actually mounts. But only stays for a short while, before it's back to square one, with the "sense key: no sense" error again.

If there's any experts who know about the 60-persistent-storage.rules file, I would be happy to hear!

---

### Post by WhiteScars on 2009-05-20
i have similar issue, I got 1 TB Maxtor USB disk. I does not automount during OS load. But when i unplug the device and plug it, it mounts and eveything runs perfectly. 

do you guys have any idea how to fix this. 
Here is some outputs

lsusb
```

Bus 001 Device 006: ID 0d49:7410 Maxtor 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 005 Device 002: ID 046d:08a0 Logitech, Inc. QuickCam IM
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 002: ID 045e:00b0 Microsoft Corp. Digital Media Pro Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

sudo fdisk -l
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb07e156

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4902    39375283+   7  HPFS/NTFS
/dev/sda2            4903       30400   204812685    f  W95 Ext'd (LBA)
/dev/sda5            8727       30400   174096373+   7  HPFS/NTFS
/dev/sda6            8429        8726     2393653+  82  Linux swap / Solaris
/dev/sda7            4903        7820    23438772   83  Linux
/dev/sda8            7821        8428     4883728+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x115c115c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

```

---

