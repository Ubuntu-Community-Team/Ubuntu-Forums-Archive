---
title: "T41p - dual boot - blue screen on windows"
date: 2006-02-25
forum: Hardware &amp; Laptops
---

### Post by flopiano on 2006-02-25
Hi all,

I own a Thinkpad T41p and, until yesterday, I had a dual boot configuration XP/Fedora Core 2. I hadn't upgrade my linux distro because when I installed it
it took me quite a while before having all working (wi-fi, read ntfs, mplayer etc.).
Today I decided to switch to Ubuntu and everything was indeed smooth and painless.

Wi-Fi worked without problems, the windows partition was already mounted and with a couple of apt-get I also had all the codecs I needed to play movies.

I was happy all the day until I tried to boot XP. But, sadly, I got a blue screen
right after the windows xp splash screen.

I don't remember how I did configure Grub the first time (in 2004, with Fedora) but I think it was on the MBR. And the same I did this time.

After reading something *after* the installation, I indeed discovered the cause of my troubles.

Before the installation I read some generic (but very good indeed) instructions for installing Breezy on a Thinkpad T42 (and everything went fine).

Now, after some googling, I discovered that
"Older Thinkpads like T40(p) or T41(p) use a HPA (Hidden Protected Area) instead of this system partition for this PreDesktop Area"

And actually when I did the partitioning there was some 2 or 3 Gb available on disk and I, without thinking too much, I just added a /var partition, erasing so this PreDesktopArea that apparentely was vital for the windows boot.  :-(

Now the Windows partition seems OK, but I just cannot boot it.
Is it at all possible to fix it ?
AFAIK, the hidden partition was needed for recovery and for the blue "access ibm" key. 

One possible way that I could try is to restore the hidden partition in some way, for example dd'umping it from another t41p (from a coworker) is that feasible ?
Or maybe there is an easiest way ?

Thanks for any advice.

Fabio,

Below you can get some additional information:

This is the partition table:
```

# fdisk -l
Disk /dev/hda: 60.0 GB, 60011642880 bytes
16 heads, 63 sectors/track, 116280 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       78825    39727768+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           78826       79028      102312   83  Linux
/dev/hda3           79029       99833    10485720   83  Linux
/dev/hda4           99834      116280     8289257    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/hda5           99834      101914     1048792+  82  Linux swap / Solaris
/dev/hda6          101915      109319     3732088+  83  Linux
/dev/hda7          109332      116280     3502138+  83  Linux

```

```

#df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3             10321168   1839092   7957792  19% /
tmpfs                   517948         0    517948   0% /dev/shm
tmpfs                   517948     12644    505304   3% /lib/modules/2.6.12-10-686/volatile
/dev/hda2                95877     27086     63676  30% /boot
/dev/hda6              3673444    315500   3171340  10% /home
/dev/hda1             39727768  37673812   2053956  95% /media/hda1
/dev/hda7              3447108    460432   2811572  15% /var
/dev/hdc               1378688   1378688         0 100% /media/cdrom0

```
and here is the relevant entry on /boot/grub/menu.lst:

```

# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by flopiano on 2006-02-25
Solved!
After some more googling I found out what to do:
I went in the bios and disabled the hidden recovery partition.
After that XP booted fine.

Fabio

---

### Post by niv on 2006-02-25
Oh wow...well I tried the same thing, only I can't seem to get any operating system to boot (quickly). Very annoying.

---

