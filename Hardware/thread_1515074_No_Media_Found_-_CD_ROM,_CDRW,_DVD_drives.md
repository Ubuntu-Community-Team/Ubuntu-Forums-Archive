---
title: "No Media Found - CD ROM, CDRW, DVD drives"
date: 2010-06-21
forum: Hardware
---

### Post by undrline on 2010-06-21
Ubuntu sees that the drive is there, reads its correct brand and so forth, but it won't ever acknowledge that there's any media present.

 The machine is a HP DC5100.  I have tried three drives: two Lite-On and one HP drive.  All internal drives.  One was a CD  ROM, one was a CD/CD-RW, and one was a CD/CD-RW DVD ... respectively.  Of course, I've tried blank, audio, data, and dvd  discs.  The same problem existed on all drives, regardless of media.

I've checked the Lite-On ([liteonit.com]("http://us.liteonit.com")) website, and they offer no support for Linux.  I'd prefer the HP one (the one that came with the machine and has the ability to play DVDs) anyway.  I've checked these forums, and googled all over myself.  Unfortunately I can't think of any key words that would stand out, so I might not have tried something that's already been posted.

I installed Ubuntu Desktop over LUbuntu via the Synaptic Package Manager ... is it possible that something went missing by installing this way?  Is there a way I can pin down what's going wrong, rather than just seeing the symptom of no media found?  I've seen the word "fstab" a lot?  Also, I've poked around in /etc/ and /dev/ looking for my device ... I don't think it's there.

I'll keep scouring, looking for answers, but hopefully someone can help me here.

---

### Post by undrline on 2010-07-07
With 7775 views, I guess I'm not the only one out there with issues. I've come across a lot of unhelpful threads. None seem to apply to any of the recent releases (I'm on Lucid 10.04) Then there's [this one]("http://ubuntuforums.org/showthread.php?t=1135452"), which gave lots of useful things to try, and seemed to help a lot of people. I left in the CD-ROM drive, the one drive that I know - without a doubt - is a working drive. And, at [the suggestion]("http://ubuntuforums.org/showpost.php?p=7181660&postcount=14") to use "a dvd or cd with a known filesystem in the drive (a movie, data cd not burned on vista, an ubuntu live cd)" I tried putting in a scanner driver CD (Onyx_14, below) that I know is nothing but a data file disk, and it whirred to life, prompting me to autorun or open with the file manager! So, something is going on.


with a store-bought audio CD purchased prior to DRM protections ...

sudo mount -t iso9660 /dev/sr0 /media/cdrom
```
mount: no medium found on /dev/sr0
```mount
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
gvfs-fuse-daemon on /home/redacted/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=redacted)
```more /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a9816ead-a370-4ae5-92c6-89baafeb461e /               ext4    errors=remount
-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a31a6ab1-63f0-460d-a9b4-1234a1673878 none            swap    sw            
  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```dmesg | tail -n10```

[   17.160191]    groups: 0-1 (cpu_power = 1178)
[   17.224032] end_request: I/O error, dev fd0, sector 0
[   17.256032] end_request: I/O error, dev fd0, sector 0
[   25.256008] eth0: no IPv6 routers present
[67471.776932] i2c i2c-0: sendbytes: NAK bailout.
[87580.208116] i2c i2c-0: sendbytes: NAK bailout.
[87760.230594] i2c i2c-0: sendbytes: NAK bailout.
[88314.585183] i2c i2c-0: sendbytes: NAK bailout.
[111938.273689] pcmanfm2[16089]: segfault at 55d ip b6f06ebc sp bffa8258 error 6 in libc-2.11.1.so[b6e97000+153000]
[111979.608205] usb 3-1: USB disconnect, address 2
```Then, I put the scanner disk in and ...

sudo lshw -C disk
```
  *-cdrom                
       description: SCSI CD-ROM
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/Onyx_14
       capabilities: audio partitioned partitioned:mac
       configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
  *-disk
       description: ATA Disk
       product: WDC WD3200AAKS-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WCAYU2731203
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0009b7ce
```grep "UDMA" /var/log/dmesg
```
[    0.387982] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x14e0 irq 14
[    0.387987] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x14e8 irq 15
[    0.544031] ata3: SATA max UDMA/133 cmd 0x1818 ctl 0x1830 bmdma 0x14f0 irq 19
[    0.544036] ata4: SATA max UDMA/133 cmd 0x1820 ctl 0x1834 bmdma 0x14f8 irq 19
[    0.722760] ata3.00: ATA-8: WDC WD3200AAKS-00UU3A0, 01.03B01, max UDMA/133
[    0.735938] ata3.00: configured for UDMA/133
```

Anyone out there who can help me with this?  Hints, help, suggestions, even pageslaps appreciated.

---

### Post by undrline on 2010-07-07
huh.  per [this post]("http://ubuntuforums.org/showpost.php?p=8270471&postcount=3") I tried:

```
sudo hal-disable-polling --device /dev/sr0
```

then

```
sudo hal-disable-polling --device /dev/sr0 --enable-polling
```

appeared to make it read the audio CD ...

---

### Post by undrline on 2010-07-07
...and silly me, took that opportunity to shut down, switch out the CD-ROM for the CD-RW/DVD, and try again ...

After having no success and going back to the CD-ROM, it only reads that data disk ](*,)

---

### Post by undrline on 2010-07-19
Another thing I've tried was to install **ubuntu-restricted-extras** per the official documentation:
[https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%2010.04%20LTS%20%28Lucid%20Lynx%29%20and%209.10%20%28Karmic%20Koala%29](https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%2010.04%20LTS%20%28Lucid%20Lynx%29%20and%209.10%20%28Karmic%20Koala%29)

This didn't help.

---

### Post by U235master on 2011-04-28
bump. im having the same exact problem on Maverick 10.10, and id really like to be able to fix it.

---

### Post by LarryJ2 on 2011-06-08
I have the same problem in 11.04 Natty Narwal.  No media detected  shown in system -> Admin -> Disk Utility

I know the hardware is OK.  This PC had 10.04 LTS on it until just a few hours ago.

---

### Post by beyondwithinitself on 2012-01-25
I'm having the same problem as everyone else here.  The disk drive is recognized by Disk Utility but is seemingly unmountable ("mount: /dev/sr0: unknown device") and inaccessible ("No Media Detected").

---

