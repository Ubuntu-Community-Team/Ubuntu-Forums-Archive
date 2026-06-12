---
title: "Destroyed my ntfs partition?"
date: 2009-08-20
forum: Hardware
---

### Post by w00ly on 2009-08-20
About every 2 years or so I get tired of windows and it's slow speed and decide to give linux a try. Invariably some major catastrophe ends up happening and performing some basic task ends up not working and I go back

About a month ago I started this cycle's adventure with Kubuntu 9.04. I install it, do dist-upgrade and add codecs and samba and a few other tweaks here and there. Somewhere in this process I start getting hard crashes: ctrl alt backspace doesnt work (even though I enabled it), nor ctrl alt f1 nor alt sysrq r. I dont have to be doing anything specific...most of the time i'm watching a video and i'll get a screen flicker, the video will stop, audio continues for 60 seconds then complete stop (besides being able to move the mouse some). Also had the "flicker of death" when converting avi files to DVD format with DeVeDe and wine/Convertxtodvd. 

Rebooting also causes a crash if samba shares are mounted or a disk is in the cdrom (thus forcing me to restart by holding the power button since the escape keys dont work). I'm not sure why but it's either a message about cifs or a blank screen with the cdrom drive buzzing away. I tried upgrading to 2.6.30 kernel but that stopped my network card from functioning. Well that's kinda frustrating...I like KDE better than Gnome but it's not working very well.

I'd LIKE to like linux more than windows so I figure I'll give regular Ubuntu a try before making the switch back to something functional. I wanted to give my linux partition more space in case I decide to install both KDE and Gnome. So I start using ntfsresize to shrink my ntfs partition. I run through the info/test modes and all goes well. I make the actual run through ntfsresize and all goes well. Then it tells me I have to use fdisk to create the new partition. "wtf? Ok, that should probably be automatic with the 'ntfsresize' that I just did, but whatever.." I load up fdisk. I delete /dev/sda5. Then I add it back, making sure to put the starting cyclinder at 1031 like it was before and I added 1gb to the size for good measure. Set type to 7 for NTFS. Write changes to disk. Reboot. Come back and my drive isnt showing any more :confused: Reboot again to Ubuntu live disk and do the same thing except size to the exact same as what it was shrunk to. Same problem
```
ubuntu@ubuntu:/mnt$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf806f806

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         790     6345643+  83  Linux
/dev/sda2             791       24321   189012757+   f  W95 Ext'd (LBA)
/dev/sda5            1031       17986   136199070    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13c5a9de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
ubuntu@ubuntu:/mnt$ sudo mount.ntfs /dev/sda5 /mnt/ddrive
NTFS signature is missing.
Failed to mount '/dev/sda5': Invalid argument
The device '/dev/sda5' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```In gparted it's showing /dev/sda5 actually in a submenu of /dev/sda2...i'm not sure why it's doing this because they were all seperate before...though I cant remember what /dev/sda2 actually was...it may be the swap partition that's now gone.

Please if someone knows how I can recover my data i'd be eternally grateful. I backed up some stuff but didnt have enough space to backup all of it (and of course I forgot about critical files AFTER I had done this). I'm still gonna give Ubuntu a try but right now recovering my data is the #1 priority. As for right now though I'm going to bed because I've been working on this for like 5 hours now and it's almost 6AM :(

---

### Post by w00ly on 2009-08-20
Bump

---

### Post by w00ly on 2009-08-20
Tried using testdisk. Doing a quick search and a deep search didnt even locate it.```
Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63

     Partition                  Start        End    Size in sectors

 1 * Linux                    0   1  1   789 254 63   12691287
 2 E extended LBA           790   1  1  1029 254 63    3855537
 5 L Linux Swap             790   2  1  1029 254 63    3855474

``` I hit enter then quit and went back into analyse and it shows
 ```
Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0   1  1   789 254 63   12691287
 2 E extended LBA           790   0  1 24320 254 63  378025515
Invalid NTFS boot
 5 L HPFS - NTFS           1030   0  1 17985 254 63  272398140
 5 L HPFS - NTFS           1030   0  1 17985 254 63  272398140

```but I dont see any recovery options. Also noticed that it's showing cylinder start at 1030 even though I specified 1031 in fdisk (and it still shows that)

---

### Post by iDIEDaLONGtimeAGO on 2009-08-20
Try photorec, its bundled with testdisk. Even i inadvertently messed up an NTFS partition while moving to Ubuntu. Got back almost everything.  In testdisk, after analysis, hit deeper search/analysis. You can selectively get back the data it detects. Use 'p' to browse a folder and 'c' to copy the folder to a place of ir choice. Hope it helps.

---

### Post by w00ly on 2009-08-20
Thanks for the reply...it was slightly late though as I was installing windows to use "GetDataBack for NTFS". Actually I was trying to see what recovery utilities I could use on the windows disk but went ahead and installed. It's a good thing GetDataBack is a good program because windows decided tit was a better idea to install on the partition i'm trying to fix rather than on the free space :\ It was able to recover it though with only minimal damage...great program if anyone has a similar issue. The only problem now is deciding what I need to save since it doesnt appear to be able to recover the whole thing

---

