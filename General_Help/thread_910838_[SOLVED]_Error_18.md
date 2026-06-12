---
title: "[SOLVED] Error 18"
date: 2008-09-04
forum: General Help
---

### Post by bpurvis on 2008-09-04
*sigh :(

I have had this installation working beautifully for months, and then one day I didn't have my laptop plugged in, I was looking at photos and it dies on me. No big deal, right?

Well apparently not because when I plug it in to start it up, no dice. It froze on the first loading screen that shows this:

```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error18

```

Any insight would be much appreciated, I think I can just re-install Ubuntu, but I don't want to lose any of my files.

btw, It was Ubuntu v8.04 fully updated.

Thanks

---

### Post by Diabolis on 2008-09-04
> 
Quoted from the GNU/GRUB manual

    18 : Selected cylinder exceeds maximum supported by BIOS
        This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by bpurvis on 2008-09-05
Thanks for the reference, but I already looked into that. It makes sense on a new install, but why on mine when it has been better than functionable for several months?

The other fix that I read about was to establish HDD ordering in bios, but I only have one HDD, and again, it has worked for a long time. Also my cheap Acer Aspire 3690-2576 has a locked bios, no access.

Any other ideas? I'm juiced:confused:

---

### Post by Crafty Kisses on 2008-09-05
Have you tried using SuperGRUB to restore your boot?

---

### Post by Bucky Ball on 2008-09-05
[www.supergrubdisk.org](www.supergrubdisk.org)

---

### Post by bpurvis on 2008-09-05
Well, I've now tried _everything _ relating to my issue on the Super Grub Disc, and nothing helped. I think I'll have to get a 2.5" external HDD enclosure, take out my laptop hard drive and back up the info I need. Then find a working copy of XP, as this is my University laptop and I can't have this happen in the future. Too bad, I liked Ubuntu.

---

### Post by Bucky Ball on 2008-09-05
And you have a given up a little easy ... On dual boot machines, if you don't shut down windoze properly and try to boot ubuntu, you encounter all sorts of problems and need to boot to windows then shut it down correctly. This could be related as even though you are not talking about windoze, it could be a similar position as you have a half cocked shutdown. Post the details of how many hard drives you have and if you're dual booting Windoze and ubuntu and if so, where are they installed.

  :)

Possibilities which may (or may not) work:

* Setting the hard drive to** NORMAL** in the BIOS seems to have fixed this problem for others, not LBA or auto, but if that doesn't work ...

** Try setting the hard drive to auto in the BIOS (not LBA), or set to LBA if it is auto. LBA should give it 255 heads and bring things back together.

If none of this works, from the live cd, (or any other way) can you boot to a shell and type:

**sudo umount -a**

This will unmount all your drives (hopefully correctly). Then try to reboot into grub and let us know what happens?

Your machine has been running beautifully for months, you encounter one problem and you're ready to scrap the lot and go back to windoze? Imagine, if you will, the multitude of problems you may have encountered using that OS over the same time period ... but Linux is not for everyone ... :)

---

### Post by bpurvis on 2008-09-05
Well I would love to continue trying, but I'm not used to this much help from forums! Last time I tried troubleshooting Ubuntu, after days of working at the problem it turned out there was no way to get the internal wifi working. (This is on my friend's laptop right after trying to convince him that linux can be better than anything you have to buy).

It's not a dual boot, single HDD, single partition Hardy installation.
The bios on this laptop (System BIOS Version: v1.3505, VGA Bios Version: Napa 1313) is very limited, and I'm not new to bios.

Also i'm trying to boot straight to a shell but nothing seems to work. Also couldn't find any documentation on how to it from the Live disc.

Let's beat it.

---

### Post by Bucky Ball on 2008-09-05
Lets ... :twisted:

New day here and things to do so will be in and out, but ...

Was that a Broadcom wireless card? Spent months trying to get mine up in Gutsy and gave up. Installed Hardy during the mid-year uni break and using the new Broadcom b43 driver (System->Admin->Hardware Drivers) and fw-cutter had it up and running in about 10 minutes! 

Now this is strange. Error 18 suggests that your grub has somehow been moved outside where the system is expecting to find it. I can't really see how this is possible. But anyways. Let's just try and reinstall grub for now and clean up the mess (if any) later. Try this:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)

From this page:

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

Once you can get to a grub shell, the info on either of these pages should get us going.

---

### Post by caljohnsmith on 2008-09-06
Bpurvis, if things were working previously as you say, then I think fixing your problem might be as simple as doing an "fsck" on your Ubuntu partition. From the Live CD, open a terminal and do the following:
```
sudo fdisk -lu
```
Find your Ubuntu main partition in the form "sdaX", and then use that:
```

sudo umount /dev/sdaX  [COLOR="Blue"][just to make sure sdaX isn't mounted somewhere][/COLOR]
sudo fsck /dev/sdaX
```
Be sure to say "y" to any errors fsck asks to fix. If you still have a Grub problem after rebooting, then I think Bucky Ball's advice is the next thing to try, namely reinstalling Grub to the MBR. But if you try to reinstall Grub to the MBR before the fsck, I think you will most likely get an error when you do the "find /boot/grub/stage1" command and won't be able to continue since your Ubuntu partition is unreadable. Let us know how it goes. :)

---

### Post by bpurvis on 2008-09-06
this is what happened...

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Attempt to read block from filesystem resulted in short read while tr
ying to open /dev/sda1
Could this be a zero-length partition?
ubuntu@ubuntu:~$
```


I was going to try to reinstall the grub as per Bucky Ball suggested, but I'll wait to make sure I did this correctly.

Thanks.

---

### Post by caljohnsmith on 2008-09-06
So are you sure sda1 is your Ubuntu partition? If so, it won't do any good at this point I think to try and reinstall Grub, because that partition somehow messed up. It would be helpful if you could post the full output of:
```
sudo fdisk -lu
```

---

### Post by bpurvis on 2008-09-06
got it, this is exactly what was in the terminal

```


ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk Identifier: 0xe1a4b4be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   150288074    75144006   83  Linux
/dev/sda2       150228075   156296384     3004155    5  Extended
/dev/sda5       150228138   156296384     3004123+  82 Linux swap / Solaris
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Attempt to read block from filesystem resulted in short read while tr
ying to open /dev/sda1
Could this be a zero-length partition?
ubuntu@ubuntu:~$

```

Thank you again

---

### Post by caljohnsmith on 2008-09-06
That's definitely not a good sign that fsck can't check sda1. Try mounting it and post the output of the following:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```

---

### Post by bpurvis on 2008-09-06
Sorry, was that supposesed to be entered on separate lines or the same line?

---

### Post by Bucky Ball on 2008-09-07
Separately. One, hit enter, then the next. :)

---

### Post by bpurvis on 2008-09-07
The first line of code didn't work, but I tried the second line anyways.

```

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail or so

ubuntu@ubuntu:~$ ls -l /mnt
total 0
ubuntu@ubuntu:~$ 

```

then when I did as suggested and looked at the dmesg | tail syslog this is what I saw


```

ubuntu@ubuntu:~$ dmesg | tail 
[ 1195.439382] ata1: EH complete 
[ 1195.440387] EXT3-fs: can't read group descriptor 3 
[ 1195.440821] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB) 
[ 1195.440833] sd 0:0:0:0: [sda] Write Protect is off 
[ 1195.440836] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[ 1195.440853] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't 
support DPO or FUA 
[ 1195.440870] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB) 
[ 1195.440880] sd 0:0:0:0: [sda] Write Protect is off 
[ 1195.440882] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[ 1195.440897] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't 
support DPO or FUA 
ubuntu@ubuntu:~$ 


```


Thanks again, and the replies are taking awhile because it's not quick typing it from my laptop to my desktop.

---

### Post by bpurvis on 2008-09-21
Well, No replies recently so I took my laptop in to get the data backed up on the hard drive, and it had been a hdd failure. I have now installed a new hard disk drive, and i put ubuntu studio on it.

sounds like a case closed.

---

