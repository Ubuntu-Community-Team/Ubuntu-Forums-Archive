---
title: "[SOLVED] Check Disk on SD/MicroSD Card?"
date: 2008-12-08
forum: Hardware
---

### Post by anxiousdog on 2008-12-08
I have a microSD in my Blackberry that somehow got corrupted. My Blackberry says that I need to run a disc check for errors and try to fix them. I am not sure how to do this in Ubuntu (Ibex).

Any help?

---

### Post by prshah on 2008-12-08
> **anxiousdog said:**
> I have a microSD in my Blackberry that somehow got corrupted. My Blackberry says that I need to run a disc check for errors and try to fix them. I am not sure how to do this in Ubuntu (Ibex).


If the card is using FAT/FAT32/VFAT filesystem (Most likely), plug it into a card reader/writer, plug that into your Ubuntu system (or enable Disk / USB Mass Storage Device mode in the Blackberry, if such an option is available).

Your card should now be visible on the desktop; right click it and unmount it.

Open a terminal (Applications-Accessories-Terminal) and give the command```
sudo fsck -a /dev/sdd1
``` (Replace /dev/sdd1 with the actual partition device for the micro sd card). fsck = File Systen ChecKer.

Note that there is a (small) chance that you can lose data by this; it _may_ delete corrupted file entries.

If you have any doubts about which device or file type or so on, the following information (with the card plugged in) will be helpful for a quick response when you post back```
sudo fdisk -l
mount
dmesg | tail -20

```

If the fsck is successful, it will not return any output.

Post back with more details (as above) if you have any questions.

---

### Post by anxiousdog on 2008-12-08
Thanks!

This is the error I get with the fsck:

> anxiousdog@ubuntu1:~$ sudo fsck -a /dev/sdg
fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdg
/dev/sdg: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


---

### Post by prshah on 2008-12-08
> **anxiousdog said:**
> 
This is the error I get with the fsck:

Try ```
sudo fsck -a /dev/sdg1
``` Usually, the device will be /dev/sdg, and the partition /dev/sdg1.

---

### Post by prshah on 2008-12-08
> **anxiousdog said:**
> 
This is the error I get with the fsck:

Try ```
sudo fsck -a /dev/sdg1
``` Usually, the device will be /dev/sdg, and the partition /dev/sdg1.

---

### Post by prshah on 2008-12-08
> **anxiousdog said:**
> 
This is the error I get with the fsck:

Try ```
sudo fsck -a /dev/sdg1
``` Usually, the device will be /dev/sdg, and the partition /dev/sdg1.

---

### Post by anxiousdog on 2008-12-09
> **prshah said:**
> Try ```
sudo fsck -a /dev/sdg1
``` Usually, the device will be /dev/sdg, and the partition /dev/sdg1.

That was it! It repaired 8 bad sectors and deleted the offending file(s). It's working great now!! Thanks so much.

---

### Post by Max Avion on 2009-04-13
Hello, 

I am also needing to do the same thing but am not sure which device is the SD card. Would you be able to help me out? Would be very much appreciated.
The only external hardware device that I is plugged in is the SD card. 

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        9054    72678060    7  HPFS/NTFS
/dev/sda3            9055        9315     2096482+   f  W95 Ext'd (LBA)
/dev/sda4            9316        9729     3325455   db  CP/M / CTOS / ...
/dev/sda5            9055        9315     2096451   dd  Unknown

Many thanks in advance.
Max

---

### Post by prshah on 2009-04-16
> **Max Avion said:**
> 
The only external hardware device that I is plugged in is the SD card. 


Unfortunately, I can't see it either. Try the below commands in the terminal (Applications-Accessories-Terminal)

a) Unplug the device
b) wait 10 seconds
c) plug the device back in, then give this command, and post back the output```
sleep 10 && dmesg | tail -23
```
d) Also post the output of the command```
sudo fdisk -l
``` (That's small letter "L", not "1")

---

### Post by Max Avion on 2009-04-18
Thank you very much for the reply PRShah. Sorry for taking so long to reply. Here is the information that you asked for. 

```
$ sleep 10 && dmesg | tail -23 

[  253.768149] wlan0: no IPv6 routers present
[  613.534011] CPU0 attaching NULL sched-domain.
[  613.534041] CPU1 attaching NULL sched-domain.
[  613.540295] CPU0 attaching sched-domain:
[  613.540317]  domain 0: span 0-1 level MC
[  613.540324]   groups: 0 1
[  613.540346]   domain 1: span 0-1 level CPU
[  613.540352]    groups: 0-1
[  613.540363] CPU1 attaching sched-domain:
[  613.540379]  domain 0: span 0-1 level MC
[  613.540385]   groups: 1 0
[  613.540394]   domain 1: span 0-1 level CPU
[  613.540410]    groups: 0-1
[  927.484026] CE: hpet increasing min_delta_ns to 15000 nsec
[  927.484026] CE: hpet increasing min_delta_ns to 22500 nsec
[  927.484026] CE: hpet increasing min_delta_ns to 33750 nsec
[  927.484026] CE: hpet increasing min_delta_ns to 50624 nsec
[ 1195.747189] type=1505 audit(1240031879.459:5): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=8451
[ 1195.995670] type=1505 audit(1240031879.706:6): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=8456
[ 1195.997291] type=1505 audit(1240031879.710:7): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=8456
[ 1872.157284] mmc0: new high speed SD card at address b368
[ 1872.519013] mmcblk0: mmc0:b368 SMI   1997312KiB 
[ 1872.519118]  mmcblk0:

```

```
$ sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        9054    72678060    7  HPFS/NTFS
/dev/sda3            9055        9315     2096482+   f  W95 Ext'd (LBA)
/dev/sda4            9316        9729     3325455   db  CP/M / CTOS / ...
/dev/sda5            9055        9315     2096451   dd  Unknown

```

FYI: It is a 2GB MicroSD card plugged into the computer via SD adapter card. 

Thank you again for your help, I really appreciate it. 

Cheers,

Max

---

### Post by TerrorAndHubris on 2009-05-14
Hey, I just had the exact same problem, and was having no luck with /dev/sdg1 or sdd1 for that matter. doing the same 'sleep 10 ...' command and had a similar print-out, i went:

```
ls /dev/m*
```

found there was /dev/mmcblk0 and /dev/mmcblk0p1

for me i got my disk fixed using 

```
sudo fsck -a /dev/mmcblk0p1
```

but its likely yours is without that p1 added, that was something different in my 'sleep' output.

---

### Post by _salem_ on 2009-08-18
I'm just trying this now.

Mine was also /dev/mmcblk0p1
(it's a sandisk 8gb micro, plugged into an Sd adaptor, in my laptop's built-in SD reader slot).

My blackberry keeps having a spaz with this card after it's been in for about a day or 2, and refuses to read until i reformat.

So i was trying the:
sudo fsck -a /dev/mmcblk0p1

but it just seems to blink for a second, and then returns me to the prompt. I can't believe it's scanning the whole card in just 1 second.

Is there something I am doing wrong?

---

### Post by frmdstryr on 2010-08-10
When my Blackberry is plugged in, sudo fdisk -l shows it under /dev/sdd1.  When i use umount /dev/sdd1 then sudo fsck -a /dev/sdd1 i get the error:
```

r@p:~$ sudo fsck -a /dev/sdd1
fsck from util-linux-ng 2.17.2
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
Unable to create unique name
```

---

### Post by _kate_ on 2011-07-30
That is my problem, too!

---

### Post by _kate_ on 2011-07-30
I got the answer. Use -r instead of -a in the fsck command. 
The post that I found this information in was here: [http://ubuntuforums.org/showthread.php?t=1568715](http://ubuntuforums.org/showthread.php?t=1568715)
Phew!

---

### Post by audios on 2011-09-02
argh, i have this same issue with errors on the media card in my BBerry.  I have been trying sudo fsck -a /def/sdg  but with no results.  when i do the lsusb i get this 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0fca:8004 Research In Motion, Ltd. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
the name of the drive when it shows up is 3398-829E and i can open with a folder and view all my photos and such, it just wont work on the BBerry.  i tried sdg, sdg1, -a, -r, and i always get an error, the last few times the errors have been  fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: No such file or directory while trying to open /dev/3398-829E
Possibly non-existent device?
im confused, and new to ubuntu any info would be awesome

---

### Post by prshah on 2011-09-02
> **audios said:**
> 
fsck.ext2: No such file or directory while trying to open /dev/3398-829E
Possibly non-existent device?

The 3398-829E directory will be in /media/, not in /dev/; however, you cannot use that since fsck-ing a mounted partition is problematic (I think?).

However, you can use System-Administration-Disk utility to find, unmount, check/repair and then re-mount.

Please post back if you need more details.

---

