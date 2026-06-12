---
title: "Due to Improper Shutdown, Filesytem Corrupted"
date: 2010-12-16
forum: Hardware
---

### Post by Aaron Whisman on 2010-12-16
Recently, while my laptop was booting up Lucid Lynx, my girlfriend mistook a moment of blank screen as the system being in standby and hit the power button, shutting the system down before it was ready to do so. Upon rebooting, I received an error message stating that it failed to mount /dev, /sys/, /proc, and that the target filesystem doesn't have /sbin/init.

I put in an old live CD I had of Edgy Eft in (for some reason my Lucid Lynx DVD has gone missing) for some info on what exactly happened. I am unable to mount /dev/sda1, where the OS is installed.

dmesg | tail presents

EXT3-fs: sda1: couldn't mount because of unsupported optional features.

fsck outputs "fsck.ext3: Filesystem has unsupported feature(s) while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 <device>"

Can anyone walk me through remounting my harddrive or at very least extracting some very important and not backed up data?

Thanks in advance, help will be rewarded with even more thanks! :O

---

### Post by Aaron Whisman on 2010-12-16
I've been searching for hours and have found a few people with a similar problem but  none of the solutions seem to be exactly what I need. I've tried running e2fsck with all alternate superblocks in case the superblock was what was corrupted, no success. I'm kind of at a standstill with fixing this with what I know.

---

### Post by Aaron Whisman on 2010-12-17
Bump for any help at all.

---

### Post by CharlesA on 2010-12-17
Boot off a more recent live cd and run fsck on the drive. Lucid defaults to EXT4, which Edgy wouldn't have supported.

---

### Post by Aaron Whisman on 2010-12-17
Thank you very much, I suspected this was possible. Off to find my lucid disc..

---

### Post by CharlesA on 2010-12-17
> **Aaron Whisman said:**
> Thank you very much, I suspected this was possible. Off to find my lucid disc..
Good luck. If it's still not working after you run fsck, let us know. :)

---

### Post by Aaron Whisman on 2010-12-18
> **CharlesA said:**
> Good luck. If it's still not working after you run fsck, let us know. :)

I couldn't find my disc so I just created a live USB of Lucid, BUT after I chose to boot from the USB at the menu, the loading screen took much longer than I remember it taking before.. I checked the progress and it says it can not find /dev/sda and hangs up there... What on earth can I do now?

I checked to see if the problem was in the Live USB itself by booting from it on another computer and all was in order, so it definitely is my hdd..

---

### Post by CharlesA on 2010-12-18
I've run into that when a drive was going bad on me.

I'd suggest burning the iso to a cd (after checking the MD5SUM) and trying to boot off it, that way you'll rule out conflicts.

---

### Post by Aaron Whisman on 2010-12-18
I downloaded the ISO on a public computer and made the live USB there. Can I take the files directly from the flash drive and burn a live cd without having to redownload Lucid?

---

### Post by CharlesA on 2010-12-18
I don't know as I've never tried it, but I doubt it.

Probably have to download the ISO again. :(

---

### Post by Aaron Whisman on 2010-12-18
Okay, haha. Not *terrible* news, but I will get back to you to tell you if it has worked. Thanks

---

### Post by Aaron Whisman on 2010-12-21
After booting with a live cd I get the same error, here is the entire loading screen's output:

(process:397): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
Killed
stdin: error 0
unable to open '/dev/sda'

And it hangs up there. What shall I doooo?

---

### Post by CharlesA on 2010-12-21
Something is defintiely hosed up. I don't know if it's cuz the file system is corrupted, or what. :(

Do you have another system you could hook the drive up to to see if you can run fsck on it that way?

---

### Post by Aaron Whisman on 2010-12-22
I have a windows laptop available that I could run my live cd on but I'm not sure how I could attach my laptops hdd to that one.

---

### Post by CharlesA on 2010-12-22
That's the problem, unfortunately. If you've got a Windows CD, you could try booting off it and seeing if it actually sees the drive. Worth a shot, but I don't know what good it'll do, as Windows can't read EXT4 without some modifications.

---

### Post by Aaron Whisman on 2010-12-22
Kids, that's why you always backup your data. 

I wonder why edgy eft will boot but not the live cd of lucid.

---

### Post by CharlesA on 2010-12-22
I'm guessing Edgy boots cuz it doesn't know what ext4 is.

But yeah, that's why you backup yer data, hopefully you have a good backup. :(

If you do, you could just use edgy to wipe out the partitions (using gparted) and see if it'll boot up on the lucid cd afterword.

---

### Post by Aaron Whisman on 2010-12-24
Any other opinions before I format my harddrive and lose my work?

---

### Post by Aaron Whisman on 2010-12-24
I'm going to blow up. I tried to format the partition in gparted from a live cd of egdy  and while it was trying to create new ext3 filesystem I got the error:

sh: nice: Input/output error

---

### Post by CharlesA on 2010-12-24
It really sounds like the drive is having problems. :(

Have you tried running a manufacturer's diagnostic disk?

---

### Post by Aaron Whisman on 2010-12-24
Fixed it with fire.

---

### Post by frank09 on 2011-01-07
I incurred in the same issue today, but casually and fortunately everything went ok!!!
Below the solution that came up for me.


Suddenly boot was failing on my netbook with Ubuntu 10.04 Remix, with error:
    ```
ubuntu no init found try passing init bootarg
```Booting from the Ubuntu Remix pendrive failed as well with error:
    ```
stdin: error 0 unable to open '/dev/sda'
```So I had no chance to launch an fsck, or even to know if the HDD were still alive.

Casually I tried to boot with another pendrive on which I had the CloneZilla Live application. With this, the boot finally succeeded, even though in CloneZilla command shell I could not launch any command to check my HDD.

Encouraged from this unexpected boot, I tried again with Ubuntu Remix pendrive, and voilà... boot succeeded. From there I launched
```
     sudo fsck /dev/sda1
```and the issue was solved!

Good luck to you all. :D

---

### Post by j3ffyang on 2011-02-10
Fixed by applying GParted [http://gparted.sf.net/download.php](http://gparted.sf.net/download.php) > Happy @ open source

---

### Post by rvchari on 2011-02-10
if the file extension in usb say *.iso then u can simply copy paste the iso image to any hard disk and burn the iso on cdrom.
usb stick must be having that iso.
if u check that u need not download again.

---

