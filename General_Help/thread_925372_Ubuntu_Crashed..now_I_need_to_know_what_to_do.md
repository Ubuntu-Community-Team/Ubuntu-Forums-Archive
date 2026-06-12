---
title: "Ubuntu Crashed..now I need to know what to do"
date: 2008-09-20
forum: General Help
---

### Post by lsutiger on 2008-09-20
I was doing a backup to my usb hard drive and I must heve mistyped. The backup got created in a folder in the root partition and ate the free space there. 

I rebooted in recovery mode, found the backupfile, deleted it, then typed exit. Ubuntu tried to start, but got stopped on something saying ntf. So I powered down and powered back up and ubuntu starts but stops at a blank screen with a blinking cursor. Here is from the dmesg log:
```
[   18.744000] EXT3 FS on sda1, internal journal
[   19.608000] kjournald starting.  Commit interval 5 seconds
[   19.608000] EXT3 FS on sda2, internal journal
[   19.608000] EXT3-fs: mounted filesystem with ordered data mode.
```

And from the system log:
```
Sep 20 13:35:48 linux-1501 kernel: [  368.440000] RPC: failed to contact local rpcbind server (errno 5).
Sep 20 13:35:48 linux-1501 kernel: [  368.440000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Sep 20 13:35:48 linux-1501 kernel: [  368.768000] NFSD: starting 90-second grace period
```

I am backing up right now...I booted off of the cd.

I can boot into recovery mode. I just do no know what to do!
Please help!

---

### Post by Monotoko on 2008-09-20
backup everything you need, then format, then reinstall. I did that once too

---

### Post by lsutiger on 2008-09-20
HA! I was trying to avoid that!

---

### Post by gnuvistawouldbecool on 2008-09-20
But crude as it is, with the generally rapid install time of Ubuntu, it is the simplest option, really.

---

### Post by Monotoko on 2008-09-20
aye, it isnt like trying to reinstall windows, where you need all the drivers ect, and have to spend all day getting it running, then windows tells you theres something wrong and gives you a BSoD and then you need reinstall AGAIN  (god, that day was bad...)

its a 10 minute job with linux :P

---

### Post by lsutiger on 2008-09-20
Craptastic!!!
I was using gzip to zip to a file, and I guess I misunderstood the command...now all of my files on the hard drive are zipped!!!
Is there a quick fix to zip?
the command I used was :
 gzip -r /media/disk/complexity/* >> /media/disk-1/back-09-20-2008.gz
trying the opposite:
gunzip -r /media/disk/complexity/*

---

### Post by lsutiger on 2008-09-21
OK - got a new install. Having a few problems.

1) I can not get the compiz cube to work. All the other settings are working. When I run the compiz settings manager, I can not click on desktop cube (it's sorta greyed out)
2) I have a winxp setup in virtual box that says 'inaccessible' The error I am getting from details is ```

The Revision filter expression '1.00' is not valid.


Result Code: 
NS_ERROR_INVALID_ARG (0x80070057)
Component: 
USBDeviceFilter
Interface: 
IUSBDeviceFilter {d6831fb4-1a94-4c2c-96ef-8d0d6192066d}

```
3) emerald is not working. when I choose a theme it stays the same as the first one chosen.

Any help wuld be greatly appreciated!!

---

### Post by -Zeus- on 2008-09-21
remove the .compiz, .emerald, folders from ~, and maybe .virtualbox as well?

---

### Post by mrowth on 2008-09-21
> **Monotoko said:**
> aye, it isnt like trying to reinstall windows, where you need all the drivers ect, and have to spend all day getting it running, then windows tells you theres something wrong and gives you a BSoD and then you need reinstall AGAIN  (god, that day was bad...)

its a 10 minute job with linux :P
Are those *literal* 10 minutes? It usually takes an hour here, much like Windows (only without the driver CDs, and with more things broken until BIOS and grub have been poked around in properly)

---

### Post by lsutiger on 2008-09-21
LOL! 10 minutes..maybe to load. I have spent this morning till now getting 'my ubuntu box' back! But well worth it. 

A while back, I tried the upgrade option to 8.04 on a cloned hard drive, and it was not nice! so I waited until I 'had a problem' like this. And after all I did not need to reinstall/upgrade. I rebooted the 'crashed' ubuntu, went about my business doing house chores, and BAM! I hear the ubuntu greeting! Well, since I had a good backup, I said what the heck!

On the errors I recently had in the new install -
1) I had to enable a bunch of plugins for compiz. Since I kept left my home directory alone during the install, I didn't think I needed to reset those settings
2) I edited the machine's xml file. I found the offending line and deleted it.
3) Emerald is supposed to load on boot, but it is not working. I have run emerald --replace at bootup.

I am having a problem with the mplayer plugin for firefox-3. I got rid of totem as that program does not work well as a media player in firefox. mplayer has always worked for me, but now it d/l(buffers) the file and nada!

Thanx for the interest and help!

---

