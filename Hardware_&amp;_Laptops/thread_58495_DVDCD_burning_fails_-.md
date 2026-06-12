---
title: "DVD/CD burning fails -"
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by halo five on 2005-08-20
Hi there,

I installed Ubuntu 5.04, cd and dvd burning worked fine, I switched to SuSE for a while (mistake!) and then reinstalled ubuntu, and now my DVD burner doesn't work.  Whenever I burn .  I think it might not be mounting my dvd burner correctly, but I'm new and don't know how to investigate this very well.  When attempting to burn anything (iso, audio, data, etc.) in Gnomebaker or Nautilus, I get the following error as soon as the process starts:

"Fail to change write speed 4235->1248" or something along those lines.

This is the output I get from tput of hdparm /media/cdrom:

/media/cdrom:
 BLKROGET failed: Inappropriate ioctl for device
 BLKRAGET failed: Inappropriate ioctl for device
 BLKGETSIZE failed: Inappropriate ioctl for device
will@kain:~$ 

Also, I think I should see my dvd burner when I type "df", but I don't:

will@kain:/$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             18406060   1944068  15527012  12% /
tmpfs                   518244         0    518244   0% /dev/shm
/dev/hdc1             38472372  28594296   7923772  79% /home
/dev                  18406060   1944068  15527012  12% /.dev
none                      5120      2800      2320  55% /dev
will@kain:/$

hda1 and hdc1 are hard drives.  My dvd burner should be hdb.  The output from dmesg is interesting:

hda: Maxtor 32049H2, ATA DISK drive
hdb: VOM-12E48X, ATAPI CD/DVD-ROM drive        
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 39062500 sectors (20000 MB) w/2048KiB Cache, CHS=38752/16/63, UDMA(33)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
hdc: MAXTOR 6L040J2, ATA DISK drive

From this it looks like my DVD burner (hdb) is detecting as a CD/DVD-ROM, not a burner, but I don't know if this is an issue or not.

Anyone have any ideas what's going on?  I don't want to have to switch back to Windows to get my DVD burner working again  :| 

Thanks!

---

### Post by halo five on 2005-08-22
Nothing, eh?

---

### Post by halo five on 2005-10-19
Still looking for help on this one.....pleasethanks!

---

### Post by earobinson on 2005-10-23
im having dvd burining problems 2

---

