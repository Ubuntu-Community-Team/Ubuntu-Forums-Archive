---
title: "[SOLVED] Generic Mounting Problems"
date: 2008-08-23
forum: General Help
---

### Post by elli222 on 2008-08-23
SOLVED! noting like thinking on the bog! (see bottom for awnser)

hi :) i am relatively new to Linux and also new to these forums, learning how useful the command line is really has helped me alot, i almost always have one open.

But today i ran into a problem even the command line couldn't fix. Mounting.

I use the term "Generic Mounting Problems" to describe odd behaviour of  my removable media.

For some memory cards, i have to Reboot and leave them in, others just need plugging in (and automount takes it from there) But these to cards are very similar technology. One is a micro SD in a Micro SD>SD adapter, and one is a mini SD in a Mini SD>SD adapter. and one volume is recognised as "Disk" and the other is recognised as "Memory Card"
The Micro SD one works fine, But the Mini SD, i have to reboot with the media in for it to be recognised.

But worst of all is my CD/DVD+RW Drive.

Recently, i haven't been able to mount anything on a disk, or with little success. But both the Cd's and the drive work fine on windows.

With Cd's:
Automount either does noting or spits out an error message:
```
Invalid mount option when attempting to mount the volume 'example'.
```
While using the mount command brings this:
```
 wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
Following the coomand line's suggestion, i tried the last 10 lines of "dmesg"
```
[ 2922.703498] sr 2:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 2922.703503] end_request: I/O error, dev sr0, sector 76
[ 2922.703572] ISOFS: unable to read i-node block
[ 2922.703575] ISOFS: changing to secondary root
[ 2922.728849] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2922.728853] sr 2:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 2922.728856] sr 2:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 2922.728860] end_request: I/O error, dev sr0, sector 1076
[ 2922.728926] ISOFS: unable to read i-node block
[ 2922.728929] isofs_fill_super: root inode is not a directory. Corrupted media?

```
I (think!) it is saying somting about I/O read errors and CRC failures, suggesting that the disk is corrupted... But most of these messages are cryptic to me :confused:

With DVD's (and some Cd's)
No errors seem to appear, the automount works, the mount command works, but either a blank directory structure is created (Example: AUDIO_FS and VIDEO_FS appear, but they contain nothing) OR a corrupted disk is displayed, with half completed files scattered  on the disk (nothing opens, apart from small graphics and freaky coincidences where the file has been corrupted in a way its still readable, Odd eh?) These disks are readable in the same drive in windows

If it helps, im trying to mount CD's from a company called "Sold-Out-Software" (apart from the DVD's)
Also, this may be irrelevent but i have problems booting my computer (at BIOS level) i think this is a motherboard fault or a broken wire in the power button :/ The CD/DVD drive STILL works fine in windows...

Any help would be greatly appreciated :)

SOLVED!
I suddenly remembered that i updated my menu.lst- although thiss shoulnt bother most people, i also remembered i had to install with the all_generic_ide boot paramiter.

The update removed this!

EET WORKS!

---

### Post by elli222 on 2008-08-24
i hate to do this but... bump!

unfortunatly i will be away for 4 days :?

---

### Post by elli222 on 2008-08-29
bump again :(

---

### Post by EmanresuusernamE on 2008-08-29
Have you tried manually typing in the mount command?  What format is the Mini-SD in?  FAT, FAT32, NTFS?  So far it would seem that manually mounting is all you need to do.  Should be something like:

mount /dev/scd0 /mnt/scd0 -t (vfat, ntfs-3g)

If it works on a Windows system, Ubuntu is not recognizing the filesystem type correctly.

---

### Post by elli222 on 2008-08-30
the CD's/DVD's are all ISO9660 (well, they SHOULD be, i dont know of any other CD filesystems...)

My micro SD card is vfat and my mini SD card... i dont know (its probably vfat too...

Ive tried manual (sudo) mounting, it gives me cryptic error messages as stated in first post...

This is really confusing, The drive is fine and so are the CD's

---

### Post by drs305 on 2008-08-30
Are the CDs you are trying to mount commercial CDs or ones you created on vista? 

**Update:** Forgot you mentioned the source. How about other commercial CD's?

---

### Post by mc4man on 2008-08-30
The errors are suggestive of a hardware issue. You may want to try some other media, an audio cd or data cd from some source other than Sold-Out-Software.
What may prove informative is to grep your logs for DMA or UDMA
> grep 'DMA' /var/log/kern.log

Also ck. this to see drive transfer capability vs. current mode

> sudo hdparm -i /dev/scd0
(asumming drive is /dev/scd0 which it appears to be

---

### Post by elli222 on 2008-09-10
whoops! i forgot about my problem till my teacher asked me to use a maths CD!

My CD/DVD+RW drive is a sony AW G170A

This is sudo hdparm -i /dev/scd0 just as requested. i will get the other logs later
```
/dev/scd0:

 Model=SONY    DVD RW AW-G170A                 , FwRev=1.71    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no

 * signifies the current active mode

```

---

