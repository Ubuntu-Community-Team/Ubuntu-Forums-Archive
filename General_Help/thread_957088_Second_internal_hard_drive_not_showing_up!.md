---
title: "Second internal hard drive not showing up!"
date: 2008-10-23
forum: General Help
---

### Post by Tictoon on 2008-10-23
Hiya, I own an Acer computer, 3 gig ram, and 2 500gb hard drives. now I have a problem. when I go into my computer:/// I do not see my drive, which is cleverly named "DATA" any way to fix this?

---

### Post by plucky on 2008-10-24
> **Tictoon said:**
> Hiya, I own an Acer computer, 3 gig ram, and 2 500gb hard drives. now I have a problem. when I go into my computer:/// I do not see my drive, which is cleverly named "DATA" any way to fix this?

Open a Terminal **(Applications > Accessories > Terminal)** and post output of ```
sudo fdisk -l
cat /etc/fstab
``` l=lowercase L not a 1.

---

### Post by Tictoon on 2008-10-24
```
gagan@gagan-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x092eca5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59760   480022168+  83  Linux
/dev/sda2           59761       60801     8361832+   5  Extended
/dev/sda5           59761       60801     8361801   82  Linux swap / Solaris
gagan@gagan-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bed52e21-41a5-4ddc-8f7f-16d31d10924e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1612ea4e-3692-49f3-8302-df013955a064 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
gagan@gagan-desktop:~$             
```

---

### Post by plucky on 2008-10-24
> gagan@gagan-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x092eca5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59760   480022168+  83  Linux
/dev/sda2           59761       60801     8361832+   5  Extended
/dev/sda5           59761       60801     8361801   82  Linux swap / Solaris


Definitely not there,can you see it in the BIOS? When you boot you need to press a function key or delete key to get into the BIOS.See if the BIOS can see both drives.

Are the drives sata or pata and what model acer is it?

---

### Post by Yellow Pasque on 2008-10-24
As plucky said, check the BIOS to see if the controller recognizes the disk.

If it does, see if you can find any errors related to disk controllers in your dmesg log. Perhaps this will help:
```
dmesg | grep ata
```

If not, were you doing any work on the internals of your PC lately? SATA cables can easily become loose or unplugged if you're not really careful when working around them.

---

### Post by Tictoon on 2008-10-24
I wasn't doing any work internaly but I was messing around with windows, then it crashed and told me "Missing OS" so I popped in a recovery cd, heres the magic part: it was BLANK!

so I popped in Ubuntu, loaded it up, and installed it to take up the whole drive. after I got my printers working, I noticed one thing: all my files on my Data Drive are gone, because my DATA drive isnt present...

---

### Post by porchrat on 2008-10-24
Sounds like your HDD has crashed and needs to be replaced.  I don't suppose Windows started acting a little funny in the days before the "Missing OS" thing?

Maybe some missing system files or not being able to run windows explorer (not internet explorer mind you I mean the navigation thing)

---

### Post by Tictoon on 2008-10-24
nope, just largely screwed up with the ultimate boot cd

---

### Post by Tictoon on 2008-10-25
Bump

---

### Post by Yellow Pasque on 2008-10-25
What's the bump for? Did the disk fail or not?

---

### Post by Tictoon on 2008-10-25
It was fine until I ran the ultimate boot cd, so are you telling m i can never access those files ever again"?!?!?!?!?!??!?!

---

### Post by Tictoon on 2008-10-26
I found something in my system when I ran disk usage analyzer: [[IMG]http://i245.photobucket.com/albums/gg79/tictoon/th_screenshot1.png[/IMG]](http://s245.photobucket.com/albums/gg79/tictoon/?action=view&current=screenshot1.png)

so does this mean that the hard drive is there?

---

### Post by Tictoon on 2008-10-27
I really think it means SOMETHING, does it?

---

### Post by Yellow Pasque on 2008-10-27
So the disk analyzer sees it, but fdisk does not? Go to System -> Administration -> Partition Editor, or do the following if it's not there:
```
sudo apt-get install gparted
gksudo gparted
```
Does the partition editor have a menu where you can select /dev/sda and /dev/sdb? If you can see your other disk there, what is it partitioned as?

---

### Post by Tictoon on 2008-10-27
no it only shows me one device

---

### Post by alienprdkt on 2008-10-27
Is your other drive (the one that wont show up) ntfs (windows)?

If so did you install ntfs-3g?

---

### Post by Tictoon on 2008-10-27
it might be.... how do I install that?

```
sudo apt-get ntfs-3g
```
is that safe to use?

---

### Post by Elfy on 2008-10-27
You should have it installed as default anyway, bu the command should be ```
sudo apt-get install ntfs-3g
```

BAck to basics - is the drive recognised by bios?


If it is boot and then open a terminal, run this comamand and see if you can see an error

```
cat /var/log/dmesg |grep ata
```

---

### Post by Tictoon on 2008-10-27
what am I looking for when Bios recognized the hard disk?

heres the output of ```
cat /var/log/dmesg |grep ata
```

```
gagan@gagan-desktop:~$ cat /var/log/dmesg |grep ata
[    0.000000]  BIOS-e820: 00000000affa0000 - 00000000affae000 (ACPI data)
[   22.263975] Memory: 2847068k/2883200k available (2177k kernel code, 34868k reserved, 1006k data, 368k init, 1965696k highmem)
[   22.263984]       .data : 0xc0320514 - 0xc041bdc4   (1006 kB)
[   23.133980] Error attaching device data
[   23.134008] Error attaching device data
[   23.134034] Error attaching device data
[   23.134061] Error attaching device data
[   27.077816] libata version 3.00 loaded.
[   28.410623] ata1: SATA max UDMA/133 abar m8192@0xfea7c000 port 0xfea7c100 irq 220
[   28.410625] ata2: SATA max UDMA/133 abar m8192@0xfea7c000 port 0xfea7c180 irq 220
[   28.410627] ata3: SATA max UDMA/133 abar m8192@0xfea7c000 port 0xfea7c200 irq 220
[   28.410628] ata4: SATA max UDMA/133 abar m8192@0xfea7c000 port 0xfea7c280 irq 220
[   29.049132] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   29.050523] ata1.00: ATA-8: ST3500820AS, SD46, max UDMA/133
[   29.050525] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   29.052286] ata1.00: configured for UDMA/133
[   29.368620] ata2: SATA link down (SStatus 0 SControl 300)
[   30.007558] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   30.010582] ata3.00: ATAPI: HL-DT-ST DVDRAM_GH15N, 1.00, max UDMA/100
[   30.169828] ata3.00: configured for UDMA/100
[   30.486783] ata4: SATA link down (SStatus 0 SControl 300)
[   31.010603] pata_amd 0000:00:08.0: version 0.3.10
[   31.010687] scsi4 : pata_amd
[   31.010727] scsi5 : pata_amd
[   31.011393] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   31.011395] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   31.176718] ata6: port disabled. ignoring.
[   32.514612] EXT3-fs: mounted filesystem with ordered data mode.

```

---

### Post by Elfy on 2008-10-27
When you get into bios it shoudl show 2 drives assuming that they are seperate physical things

---

### Post by alienprdkt on 2008-10-27
try this:

#sudo bash
#fdisk -l
if you see you second 500gb drive try this
#sudo mount -t ntfs-3g /dev/sda1(to your second 500gb drive) /media/sda1/(to your second 500gb drive) - o force

---

### Post by Tictoon on 2008-10-27
```
root@gagan-desktop:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x092eca5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59760   480022168+  83  Linux
/dev/sda2           59761       60801     8361832+   5  Extended
/dev/sda5           59761       60801     8361801   82  Linux swap / Solaris

Disk /dev/sdg: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8013d57b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1         123      987104    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(121, 254, 63) logical=(122, 227, 40)
root@gagan-desktop:~#

```


I'm having trouble having bios, when I press del, it takes me into a CMOS menu

---

### Post by alienprdkt on 2008-10-27
> **Tictoon said:**
> ```
root@gagan-desktop:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x092eca5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59760   480022168+  83  Linux
/dev/sda2           59761       60801     8361832+   5  Extended
/dev/sda5           59761       60801     8361801   82  Linux swap / Solaris

Disk /dev/sdg: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8013d57b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1         123      987104    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(121, 254, 63) logical=(122, 227, 40)
root@gagan-desktop:~#

```


I'm having trouble having bios, when I press del, it takes me into a CMOS menu

hmmm your CMOS menu, does it show your hard drives there??

---

### Post by Elfy on 2008-10-28
So what drives are visible in the cmos menu - one or two?

---

### Post by Tictoon on 2008-10-28
I'm pretty sure I only see one in my CMOS menu

---

### Post by Elfy on 2008-10-28
Well if it only shows one and you are positive that you have 2 physical drives then there is a problem with the drive.

If it's not recognised there then I don't think that you'll be able to do anything software with the drive.

Sounds like you have a dead drive.

---

### Post by Tictoon on 2008-10-28
NOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO!!!!!!!!

but then how come the disk analyzer sees 1 tb instead of 500gb?

---

### Post by Elfy on 2008-10-28
mmm - not sure then.

Try testdisk livecd - burn it as an iso and boot with it - see if that sees the drive

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

The dmesg output shows an error as well.

---

### Post by Tictoon on 2008-10-28
which version do I use?

---

### Post by Elfy on 2008-10-28
it's on parted magic amongst others - [http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)

nice an dquick to boot

you can also use your buntu livecd and install it for use in that environment

---

### Post by plucky on 2008-10-28
> **Tictoon said:**
> NOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO!!!!!!!!

but then how come the disk analyzer sees 1 tb instead of 500gb?

There is a bug in Hardy's Disk usage Analyser showing double the actual disk capacity than actually exists. See this [link](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789)


If you don't see the drive in the BIOS,then it is probably dead or doesn't exist.I would open the cover of your system and actually see if there are two physical drives.
If there are,check the cables are plugged in correctly and there is power to both drives.
Then if you still cannot see both drives in the BIOS,and your system is under warranty,send it back to get the drive replaced.


Good Luck

---

### Post by Elfy on 2008-10-28
Thanks plucky - didn't know about the bug.

---

### Post by Tictoon on 2008-10-28
> **plucky said:**
> There is a bug in Hardy's Disk usage Analyser showing double the actual disk capacity than actually exists. See this [link](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789)

Good Luck

you've answered my worst fears :(

I'll check on that warranty

---

### Post by alienprdkt on 2008-10-28
Could try opening case unplug cables and replug them back in, maybe you'll be lucky and its just a loose cable.

---

### Post by Tictoon on 2008-10-28
I can't do that, Dave...

Well I can't since if I do do that and it doesn't work, the warranty is VOID.

---

### Post by alienprdkt on 2008-10-29
ah, then if its under warranty, guess you have to send it to manufacture. If CMOS / BIOS doesn't detect the hard drive, Ubuntu isn't going to.

---

### Post by 2hot6ft2 on 2008-12-02
Just looked up and saw you wont even open the case. So guess taking it back to the store is the only solution. Somehow I suspect having linux on it may have already done your warranty in depending on the store.

Deleted all that I posted here since it required opening the case

---

