---
title: "DMA Probs on Via Chipset with DVDRom (Toshiba) in Hoary"
date: 2004-12-26
forum: Hardware &amp; Laptops
---

### Post by Pietro Pizzi on 2004-12-26
Hi,

This is my first post. I use Ubuntu for about 3 Weeks and I like it! Befor i used Gentoo for about 2 Years. But now i have a problem for which i can't find a solution. (and sorry for my non perfect english)

Starting point: DMA isn't working by default so i would enabled it with "hdparm -d /dev/hd[a-d]" but i get an error. So i seached a little bit and found a solution that says: Put the Module via82cxxx befor ide-generic in /etc/modules. When i do this i can enable DMA. But now there comes my real...

..PROBLEM: When i Do this my DVDRom isn't working correct anymore. Strange things: It doesn't shows in k3b, libdvdread can't accessed to it through libcss, i can't unmount it without sudo,... but gnome mouts it and i can browse the folders.
My other Drives funktion correct (see my sys below).

For info: In WinXP, i have one installed for gaming, works all correkt. So i think it's up to Linux/Ubuntu!?

I have also checked a tip that says: add "options ide-cd dma=1" to /etc/modules.conf. But that makes no difference. Additional i have varied the location from via82cxxx in modules.

My System:
hda - 80GB WinXP(2*NTFS) IBM HD
hbb - Toshiba DVDRom SD-M1612 (problematic!!)
hdc - Nec DVDRW 2500
hdd - Plextor CDR
sda - 120GB Barracuda, 1Partitio, ext3 @ at Onboard FastTrack Promis Chip (PDC20376)
sdb - 200GB Barr., 3Part, swap/raiserfs @ Promis 150TX2plus (PDC20375) PCI (sdb2=root/boot partition thrue GRUB in MBR)
I have an AthlonXP 2600+ on a Asus A7V8X
And i'm in Hoary

Some infos without Modul via82cxxx in modules:

$ hdparm /dev/hdb
/dev/hdb:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

$ cat /etc/fstab
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               reiserfs defaults        0       1
/dev/sdb3       /home           reiserfs defaults        0       2
/dev/sdb1       none            swap    sw              0       0
/dev/sda1       /home/pietro/.disk1     ext3    defaults,user,noauto   0        2
/dev/hda1       /media/winsys   ntfs    ro,user,noauto,umask=0         0        0
/dev/hda2       /media/windata  ntfs    ro,user,noauto,umask=0         0        0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom2   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,sync  0       0

$ sudo cat /proc/ide/hdb/settings
name                    value           min             max             mode
----                    -----           ---             ---             ----
current_speed           0               0               70              rw
dsc_overlap             1               0               1               rw
init_speed              0               0               70              rw
io_32bit                1               0               3               rw
keepsettings            0               0               1               rw
nice1                   1               0               1               rw
number                  1               0               3               rw
pio_mode                write-only      0               255             w
unmaskirq               1               0               1               rw
using_dma               0               0               1               rw

$ cat /proc/ide/via
----------VIA BusMastering IDE Configuration----------------
Driver Version:                     3.38
South Bridge:                       VIA vt8235
Revision:                           ISA 0x0 IDE 0x6
Highest DMA rate:                   UDMA133
BM-DMA base:                        0x8400
PCI clock:                          33.3MHz
Master Read  Cycle IRDY:            0ws
Master Write Cycle IRDY:            0ws
BM IDE Status Register Read Retry:  yes
Max DRDY Pulse Width:               No limit
-----------------------Primary IDE-------Secondary IDE------
Read DMA FIFO flush:          yes                 yes
End Sector FIFO flush:         no                  no
Prefetch Buffer:               no                  no
Post Write Buffer:             no                  no
Enabled:                      yes                 yes
Simplex only:                  no                  no
Cable Type:                   80w                 80w
-------------------drive0----drive1----drive2----drive3-----
Transfer Mode:       UDMA      UDMA      UDMA      UDMA
Address Setup:      120ns     120ns     120ns     120ns
Cmd Active:         360ns     360ns     360ns     360ns
Cmd Recovery:       210ns     210ns     210ns     210ns
Data Active:         90ns      90ns      90ns      90ns
Data Recovery:       30ns      30ns      30ns      30ns
Cycle Time:          22ns      60ns      60ns      60ns
Transfer Rate:   88.8MB/s  33.3MB/s  33.3MB/s  33.3MB/s

$ cat /etc/modules
sd_mod
sr_mod
psmouse
mousedev
#via82cxxx
ide-cd
ide-disk
ide-generic
sbp2
lp

$ lsmod | egrep "dma|via|ide"
snd_via82xx            27236  2
snd_ac97_codec         70544  1 snd_via82xx
snd_pcm                95368  2 snd_via82xx,snd_pcm_oss
snd_page_alloc          9800  2 snd_via82xx,snd_pcm
gameport                4480  1 snd_via82xx
snd_mpu401_uart         7744  1 snd_via82xx
snd                    55140  9 snd_via82xx, ...
via82cxxx              13724  1
via_ircc               25744  0
irda                  192128  1 via_ircc
via_agp                 9408  1
agpgart                33704  1 via_agp
ide_generic             1344  0
ide_disk               20032  1
ide_cd                 41760  0
ide_core              139440  5 usb_storage,via82cxxx,ide_generic,ide_disk,ide_cd
cdrom                  39900  2 ide_cd,sr_mod

I hope anyone can help me becaus that is the only major problem i have with my box, and i don't like the Option DMA or. DVD.

Thanks,
 Pietro

---

### Post by Pietro Pizzi on 2005-01-04
Hi,

My problem is still the same but i have done furter testst (without any changes). So i post what i have checked and hope that anyone can gave me a hint!

* I have changed my DVD Rom to a new "AOpen 1648/AAP Pro" so that says for me the Drive isn't the Problem.
* Then i switcht it to /dev/hda (form b), but there is no change. (The HD, on hdb now, works with dma when i enabled the via82cxxx)

And now i post some infos that i collect with the via module is enabled:

totem:
it comes up (automatic when i inserted the disk) with "totem can't play dvd.."
but with "totem dvd://media/cdrom0/" it plays it. Output:
** (totem:10381): WARNING **: Couldn't find themed icon for "panel-screenshot"
libdvdnav: Using dvdnav version 1-rc7 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Attempting to use device /dev/hdb mounted on /media/cdrom0 for CSS authentication
libdvdread: Could not open /dev/hdb with libdvdcss.
libdvdread: Can't open /dev/hdb for reading
libdvdread: Device /dev/hdb inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/pietro/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!

dvd copy with dvdbackup breakes:
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Attempting to use device /dev/hdb mounted on /media/cdrom0 for CSS authentication
libdvdread: Could not open /dev/hdb with libdvdcss.
libdvdread: Can't open /dev/hdb for reading
libdvdread: Device /dev/hdb inaccessible, CSS authentication not available.
libdvdread: Fatal error in block read.
Mirror of DVD failed

k3b don't see the drive

drive can't ejekt with computer:/// -> eject, error: "unable to open /dev/hdb"
but when i pressed the drives open button after i try to eject it it comes out

my other drives works if they should:
copy dvd in my dvdr with dvdbackup:
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom1 for CSS authentication
libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient
libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014e
libdvdread: Elapsed time 0
...

and yes, now all drives enebled the dma, but without access to my dvd it dosn't help.
$ sudo hdparm /dev/hd[a-d]
/dev/hda:
 multcount    = 16 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 82348277760, start = 0

/dev/hdb:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument


So, have anyone an idea what i can do now??

Thanks,
Pietro

---

