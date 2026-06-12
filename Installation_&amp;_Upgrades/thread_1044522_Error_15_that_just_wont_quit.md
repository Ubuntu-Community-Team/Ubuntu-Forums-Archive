---
title: "Error 15 that just wont quit"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by Token-Ring on 2009-01-19
I had posted for help a few days ago and after trying the suggestions that I got I finally decided that I should just try putting everything on one hard drive to see if that simplifies things (WRONG!). 

So I installed XP on partition 1, Ubuntu on partition 2, and swap space on partition 3. Now no matter what I try I get grub error 17. I had googled and tried everything I found, but I am still quite nubbish at ubuntu.

Super Grub Disk Reports My Partitions as:
```

N   IDE  SCSI  GRUB   TYPE
1   hda1 sda1  hd0,0  NTSF
2   hda2 sda2  hd0,1  linux
3   hda3 sda3  hd0,2  swap
```

fdisk -l reports:
```
root@ubuntu:/# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf4fec6f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26771   215038026    7  HPFS/NTFS
/dev/sda2           26772       30219    27696060   83  Linux
/dev/sda3           30220       30401     1461915   82  Linux swap / Solaris

```

my device.map file states:
```
(hd0)	/dev/sda
```

and the end of my menu.lst file reads:
```

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b632148a-3eaa-4732-bfd0-a0e2383fdf25 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b632148a-3eaa-4732-bfd0-a0e2383fdf25 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

What am I doing wrong? :confused::confused:

---

### Post by dabl on 2009-01-19
Have you run ```
sudo blkid
``` to verify that the UUID numbers are correct for the partitions?

Also, don't have any USB thingys plugged in, if you happen to have "boot from USB" enabled in your BIOS.

---

### Post by Token-Ring on 2009-01-19
I get this output:
```
root@ubuntu:/# blkid
/dev/sda1: UUID="1818635318632F46" TYPE="ntfs" 
/dev/sda2: UUID="b632148a-3eaa-4732-bfd0-a0e2383fdf25" TYPE="ext3" 
/dev/sda3: UUID="4b9fb29f-d4c2-4f4c-aa7b-f681643dd0d6" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

```

I think that means that the numbers are correct.

---

### Post by dabl on 2009-01-19
Yep, they sure are.

You do only have the one hard drive connected?

From a Live CD (or however you are doing it) can you get a grub prompt with ```
sudo grub
``` and then try ```
root (hd0,1)
``` and see what it returns?

---

### Post by Token-Ring on 2009-01-19
This is all it does:

```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,1)

grub> 

```

Thank you for your help so far

---

### Post by dabl on 2009-01-19
> **Token-Ring said:**
> This is all it does:

Thank you for your help so far

Meh -- so far it isn't much!

So, grub does not find the Stage 1 boot files on (hd0,1).  Probably that means they aren't there.  If you can browse to the /boot folder there, you should see the same files that are shown down the page on this site:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

While your description of your partitioning and installing adventures sounds like you did it right, apparently something is not going down correctly, or else I'm missing something from the real situation that you have there.

Does the *buntu Live CD boot and run happily on your hardware?  Does it see the hard drive and partitions if you browse to them?

---

### Post by Token-Ring on 2009-01-19
I can browse both partitions just fine, and the live CD starts with no trouble.

I had been having a problem were the computer would not recognize both my hard drives at once (I have a old Maxtor 40GB and a one year old Seagate 250GB) So I just removed the 40GB and left only the 250 in. Could this be a problem with this hard drive being too new and my computer not playing nicely? (I have a m7vig Mobo if that tells anyone somthing)

I think my next choice is just to format the whole drive and try one more time, I have done it enought times I practically have the XP key memorized so its no big deal, just time consumeing.

---

### Post by dabl on 2009-01-19
> **Token-Ring said:**
> I can browse both partitions just fine, and the live CD starts with no trouble.

I had been having a problem were the computer would not recognize both my hard drives at once (I have a old Maxtor 40GB and a one year old Seagate 250GB) So I just removed the 40GB and left only the 250 in. Could this be a problem with this hard drive being too new and my computer not playing nicely? (I have a m7vig Mobo if that tells anyone somthing)

I think my next choice is just to format the whole drive and try one more time, I have done it enought times I practically have the XP key memorized so its no big deal, just time consumeing.

Take a look in BIOS and see whether you have any choices for "modes" for the big drive.  Is it IDE or SATA?  If the mobo and BIOS are old enough, there may be issues with the size and interface for that drive.

Were the Stage 1 files in /boot/grub?

---

### Post by Token-Ring on 2009-01-19
I saw the stage one file in the grub folder (picture attached).



My BIOS is a Phoenix - AwardBIOS

and under >Standard CMOS Features my IDE Secondary Master is listed as [ST3250620A]

Under Options for that drive are:
```
IDE Secondary Master   [auto]
Access Mode [auto]
```

IDE Secondary Master can be either Auto, Manual, or None.
Access mode can be changed from auto to CHS, LBA, or Large.

Google tells me the hard drive is a "Barracuda 7200.10 Ultra ATA/100 250-GB Hard Drive"
[Link here]("http://www.seagate.com/ww/v/index.jsp?vgnextoid=349f99f4fa74c010VgnVCM100000dd04090aRCRD&locale=en-US")



Does anything else come to mind? If I do attempt a format and reinstall would making grub its own partition do any more good?

---

### Post by dabl on 2009-01-19
OK.

I suggest you change that IDE channel to "Primary Master" and see whether it makes any difference.

---

### Post by Token-Ring on 2009-01-19
That Actually Worked! :guitar:

I unplugged the Hard Drive ribbon cable from the IDE2 and swapped it with the CD drive cable in IDE1 and now everything boots just fine. I don't know why that was necessary since I have always had the CD drives on IDE1 and hard drives on IDE2 but that did the trick!

Thank you dabl for your help. :D

---

### Post by dabl on 2009-01-20
:cool:


If you can edit your original post and put "SOLVED" at the beginning of the title, it could be of help to someone else in the future.  ;)

---

