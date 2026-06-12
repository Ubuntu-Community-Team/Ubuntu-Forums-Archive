---
title: "Recieving I/O error trying to resume normal boot from recovery mode."
date: 2011-01-29
forum: Hardware
---

### Post by skaldicpoet9 on 2011-01-29
Last night Ubuntu started acting erratic so I restarted it, however during the restart process it froze and I had to manually power down the laptop. 

Once I tried booting the laptop again, it would boot back into Ubuntu but would only display the desktop wallpaper and mouse pointer. 

I restarted the computer again and this time it wouldn't even display the wallpaper or mouse pointer, just a black screen. I once again had to power it down manually. 

I booted into recovery mode and tried the dpkg option to try and repair possibly broken packages, however when I tried to resume the normal boot process after the repair had completed I get this error message and the computer just hangs: 

```

end_request: I/O error, dev sda, sector 87232
```

What exactly does this mean? And what can I do to rectify this problem?

---

### Post by skaldicpoet9 on 2011-01-31
*bump*

Is there not anyone out there that knows what this error is? I have searched google a few times for something about it but can only find a few threads dealing with the issue but no real solutions. I believe that it might be HDD failure, but I am hoping that it is not because I am broke and can't really afford a new HDD.

---

### Post by matt_symes on 2011-01-31
Hi

Have you tried running fsck on the hard disk from a live CD ? Maybe that will fix the problem.

Also you can check the smart status from the LiveCD as well.

Kind regards

---

### Post by skaldicpoet9 on 2011-01-31
Hmm, how exactly do I run fsck? I looked up a few fsck commands on google but whenever I run them I get this error: ```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: No such file or directory while trying to open /dev/x

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

Is there some step I am missing here?

---

### Post by matt_symes on 2011-01-31
Hi

From the LiveCD post the output of 

```
sudo fdisk -l
```

That's a small L above. This will tell us about your partitions on your drive.

BTW: Exactly what command did you run ?

Kind regards

---

### Post by skaldicpoet9 on 2011-01-31
There isn't any output for sudo fdisk -l, it just returns another command prompt. 
The commands that I used were: ```
sudo e2fsck -y -f -v /dev/sda1
sudo fsck /dev/sda1
fsck -fyv /dev/x
fsck -b 8193 /dev/sda1
```

---

### Post by skaldicpoet9 on 2011-01-31
So, if fdisk -l isn't returning any partitions, does that mean that my HDD is screwed? I mean, I can no longer boot into Ubuntu without the LiveCD at all, I get errors if I try to load Ubuntu from the HDD.

---

### Post by matt_symes on 2011-01-31
Hi

> **skaldicpoet9 said:**
> There isn't any output for sudo fdisk -l, it just returns another command prompt. 

That is really odd and potentially a bad sign. Have you checked for loose cables (etc) in the PC.

What happens if you open a terminal and type

```
sudo blkid
```

I think the best thing might be to check your drives smart status (assuming it has it).

To test type (i am assuming sda here) (You also might have to install it)

```
sudo smartctl -t short /dev/sda
```

leave for a while to do its check and then, when finished, type

```
sudo smartctl -a /dev/sda
```

These two command are potentially useful if the file system is corrupt.

```
sudo e2fsck -y -f -v /dev/sda1
sudo fsck /dev/sda1
```

These two are not

```
fsck -fyv /dev/x
fsck -b 8193 /dev/sda1
```

I doubt your backup super block is 8193.

Kind regards

---

### Post by skaldicpoet9 on 2011-01-31
When I type in "sudo smartctl -t short /dev/sda" I get this error message:
```
smartctl 5.40 2010-03-16 r3077 [i686-pc-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

Smartctl open device: /dev/sda failed: No such device

```

and when I type in "sudo blkid" I get this message:
```
/dev/loop0: TYPE="squashfs" 

```

I tried booting Ubuntu from the HDD, and it actually booted into the Desktop this time but whenever I get into the Desktop none of the applications I have installed won't launch (firefox and my pdf viewers were the ones I tried) and then the Desktop freezes up and I had to power down the laptop again and restarted Ubuntu from the LiveCD.

edit: Also, I have a laptop so there isn't really any cords loose that I can mess with. I did open up the case and removed and reinserted the HDD to see if it was plugged in properly though.

---

### Post by matt_symes on 2011-01-31
Hi

None of the commands you tried are seeing your hard drive but it then boots ? That is strange.

My next attempt to see the drive would be to use Testdisk and see if that can see the disk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Do you have a spare hard drive you can put in the laptop to eliminate other hardware ? 

I could be wrong but it's not looking good at the moment.

BTW: what is the output of this command from the liveCD ?

```
ls -l /dev/*da*
```

That's a small L again.

Kind regards

---

### Post by skaldicpoet9 on 2011-01-31
Hmm, I assume I need to use a LiveCd version of Testdisk, right? When I try using the binary all it detects is the CD drive. 

This is the output for ls -l /dev/*da*:
```
ls: cannot access /dev/*da*: No such file or directory

```

Unfortunately I don't have any spare drives I can use on this laptop and I am too broke to afford a replacement. I just got this laptop off of craiglist, so I don't have any spare parts for it.

---

### Post by matt_symes on 2011-01-31
Hi

> **skaldicpoet9 said:**
> Hmm, I assume I need to use a LiveCd version of Testdisk, right? When I try using the binary all it detects is the CD drive.

That's not looking good. You still can't rule out other parts of the laptop but it's not looking good for the drive in my eyes. You could try with the LiveCD/USB version of Test disk, but.... (maybe worth a shot).

> Unfortunately I don't have any spare drives I can use on this laptop and I am too broke to afford a replacement. I just got this laptop off of craiglist, so I don't have any spare parts for it.

If you have a USB pen stick that is big enough you may want to consider creating a persistent LiveUSB until you can find another hard drive and run from that saving work on the stick.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Maybe look on craigslist again or ebay for a cheap drive.

I would also wait for other suggestions from others as i'm not sure what to suggest at the moment.

Kind regards

---

### Post by skaldicpoet9 on 2011-01-31
Yeah, I am pretty sure it is the HDD. Everything else seems to work just fine, although I am unsure whether the battery on the laptop is holding a charge, it's not the most pressing of my problems however. 

I will see if I can find a cheap USB drive and use that until I can replace the HDD.  

I really appreciate the help, thanks a lot.

---

### Post by Parkor on 2011-02-08
i'm currently working through similar issues and it's not my hard drive. can you boot from recovery/failsafe graphics mode.

cheers

---

