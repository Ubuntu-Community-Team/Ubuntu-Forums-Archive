---
title: "[SOLVED] CD-ROM problem, can't mount"
date: 2008-08-10
forum: Hardware
---

### Post by dalhamir on 2008-08-10
Hey, I'm having problems mounting my dvd/cd drive. It doesn't autodetect anything anymore, and whenever I try to mount it, with a data cd in the drive it get the error
```
mount: No medium found
```

here's the output of a few things that seem relevant.
```
$ mount
/dev/hdc5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/hdd1 on /home/khill type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/video type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/hdc1 on /media/xp type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/khill/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=khill)

$ sudo lshw -C disk 
  *-cdrom                 
       description: DVD writer
       product: _NEC DVD_RW ND-3540A
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 1.04
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2 status=nodisc
  *-disk:0
       description: ATA Disk
       product: ST3160023A
       vendor: Seagate
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: 3.06
       serial: 5JS0YYMQ
       size: 149GiB (160GB)
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma5 signature=0850067c smart=on
  *-disk:1
       description: ATA Disk
       product: Maxtor 6L200P0
       vendor: Maxtor
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: BAH41G10
       serial: L40SZTHH
       size: 189GiB (203GB)
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma6 signature=2255fd0d smart=on
  *-disk
       description: ATA Disk
       product: WDC WD2500KS-00M
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WCANK3712067
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0007a0fe

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc5
UUID=bb789df7-790e-4dcf-9323-e7410a5226bb /               ext3    relatime,errors=remount-ro 0       1
# /dev/hdc6
UUID=d4119bf4-3206-481b-b0fe-784504744471 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/hdd1	/home/khill	ntfs-3g	uid=1000,gid=1000,umask=007	0	0
/dev/sda1	/media/video	ntfs-3g	uid=1000,gid=1000,umask=007	0	0
/dev/hdc1	/media/xp	ntfs-3g	uid=1000,gid=1000,umask=007	0	0

$ cat /etc/udev/rules.d/70-persistent-cd.rules 
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# _NEC_DVD_RW_ND-3540A (pci-0000:00:1f.0-ide-0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.0-ide-0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.0-ide-0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.0-ide-0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.0-ide-0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
```

the fact that /dev/hda is never mentioned anywhere in the output of 'mount' seems odd, anyone have any ideas?

---

### Post by noobuntu35 on 2008-08-10
> **dalhamir said:**
> Hey, I'm having problems mounting my dvd/cd drive. It doesn't autodetect anything anymore, and whenever I try to mount it, with a data cd in the drive it get the error
```
mount: No medium found
```

here's the output of a few things that seem relevant.
```
$ mount
/dev/hdc5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/hdd1 on /home/khill type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/video type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/hdc1 on /media/xp type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/khill/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=khill)

$ sudo lshw -C disk 
  *-cdrom                 
       description: DVD writer
       product: _NEC DVD_RW ND-3540A
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 1.04
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2 status=nodisc
  *-disk:0
       description: ATA Disk
       product: ST3160023A
       vendor: Seagate
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: 3.06
       serial: 5JS0YYMQ
       size: 149GiB (160GB)
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma5 signature=0850067c smart=on
  *-disk:1
       description: ATA Disk
       product: Maxtor 6L200P0
       vendor: Maxtor
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: BAH41G10
       serial: L40SZTHH
       size: 189GiB (203GB)
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma6 signature=2255fd0d smart=on
  *-disk
       description: ATA Disk
       product: WDC WD2500KS-00M
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WCANK3712067
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0007a0fe

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc5
UUID=bb789df7-790e-4dcf-9323-e7410a5226bb /               ext3    relatime,errors=remount-ro 0       1
# /dev/hdc6
UUID=d4119bf4-3206-481b-b0fe-784504744471 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/hdd1	/home/khill	ntfs-3g	uid=1000,gid=1000,umask=007	0	0
/dev/sda1	/media/video	ntfs-3g	uid=1000,gid=1000,umask=007	0	0
/dev/hdc1	/media/xp	ntfs-3g	uid=1000,gid=1000,umask=007	0	0

$ cat /etc/udev/rules.d/70-persistent-cd.rules 
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# _NEC_DVD_RW_ND-3540A (pci-0000:00:1f.0-ide-0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.0-ide-0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.0-ide-0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.0-ide-0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.0-ide-0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
```

the fact that /dev/hda is never mentioned anywhere in the output of 'mount' seems odd, anyone have any ideas?

the CDROM is mounted in your /media directory as you can see from your output your etc/fstab shows it here. So the system recognizes it's there.At least thats good no replacement parts yet...
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
I was just checking a short section in a book I have here, did you recently add any new devices or hardware that may be interfering with your IRQ by creating a conflict? If so disable one (the newer one likely) to make sure the DMA and IRQ aren't conflicting. I'm going to keep reading to find something more specific but this is atleast a try.One thing I have read up on, make sure the drive is still working.Can you hear it running? It may be that it is just time for a new hard drive, have you tried other cd's sorry can't remember if you said you did

---

### Post by dalhamir on 2008-08-10
No new hardware. It was working, then I tried to write what ended up to be an incomplete .iso file to a blank disk. It gave me an error, spit out the disk, and I've never been able to get it to automount or manually mount again. Weird huh? Is there a way to make ubuntu forget about a piece of hardware, and then reinstall it? Maybe that would work.

---

### Post by noobuntu35 on 2008-08-10
> **dalhamir said:**
> No new hardware. It was working, then I tried to write what ended up to be an incomplete .iso file to a blank disk. It gave me an error, spit out the disk, and I've never been able to get it to automount or manually mount again. Weird huh? Is there a way to make ubuntu forget about a piece of hardware, and then reinstall it? Maybe that would work.

there should be a way to add and remove hardware like with windoze even if its a gui based I will check out some sites, there was some stuff I saw earlier today and also a little more in the books I have.
found this run this command and see what your output is
/usr/lib/nautilus-cd-burner/list_cddrives
here is what mine does, still working on the UT install by the way any know how? 
@ubuntu:~$ /usr/lib/nautilus-cd-burner/list_cddrives
Drive:
  name:			DVD-RAM GSA-H54N
  device:		/dev/scd0
  door:			closed
  type:			CD-R, CD-RW, DVD-RAM, DVD-R, DVD-RW, DVD+R, DVD+R DL, DVD+RW, CD, DVD
  is mounted:		FALSE
  max read speed:	8468 KiB/s (CD 56.4x, DVD 6.2x)
  max write speed:	8468 KiB/s (CD 56.4x, DVD 6.2x)
  write speeds:		8400 KiB/s (CD 56.0x, DVD 6.2x)
			8250 KiB/s (CD 55.0x, DVD 6.0x)
			8100 KiB/s (CD 54.0x, DVD 5.9x)
			7950 KiB/s (CD 53.0x, DVD 5.8x)
			7800 KiB/s (CD 52.0x, DVD 5.7x)
			7650 KiB/s (CD 51.0x, DVD 5.6x)
			7500 KiB/s (CD 50.0x, DVD 5.5x)
			7350 KiB/s (CD 49.0x, DVD 5.4x)
			7200 KiB/s (CD 48.0x, DVD 5.3x)
			7050 KiB/s (CD 47.0x, DVD 5.2x)
			6900 KiB/s (CD 46.0x, DVD 5.1x)
			6750 KiB/s (CD 45.0x, DVD 4.9x)
			6600 KiB/s (CD 44.0x, DVD 4.8x)
			6450 KiB/s (CD 43.0x, DVD 4.7x)
			6300 KiB/s (CD 42.0x, DVD 4.6x)
			6150 KiB/s (CD 41.0x, DVD 4.5x)
			6000 KiB/s (CD 40.0x, DVD 4.4x)
			5850 KiB/s (CD 39.0x, DVD 4.3x)
			5700 KiB/s (CD 38.0x, DVD 4.2x)
			5550 KiB/s (CD 37.0x, DVD 4.1x)
			5400 KiB/s (CD 36.0x, DVD 3.9x)
			5250 KiB/s (CD 35.0x, DVD 3.8x)
			5100 KiB/s (CD 34.0x, DVD 3.7x)
			4950 KiB/s (CD 33.0x, DVD 3.6x)
			4800 KiB/s (CD 32.0x, DVD 3.5x)
			4650 KiB/s (CD 31.0x, DVD 3.4x)
			4500 KiB/s (CD 30.0x, DVD 3.3x)
			4350 KiB/s (CD 29.0x, DVD 3.2x)
			4200 KiB/s (CD 28.0x, DVD 3.1x)
			4050 KiB/s (CD 27.0x, DVD 2.9x)
			3900 KiB/s (CD 26.0x, DVD 2.8x)
			3750 KiB/s (CD 25.0x, DVD 2.7x)
			3600 KiB/s (CD 24.0x, DVD 2.6x)
			3450 KiB/s (CD 23.0x, DVD 2.5x)
			3300 KiB/s (CD 22.0x, DVD 2.4x)
			3150 KiB/s (CD 21.0x, DVD 2.3x)
			3000 KiB/s (CD 20.0x, DVD 2.2x)
			2850 KiB/s (CD 19.0x, DVD 2.1x)
			2700 KiB/s (CD 18.0x, DVD 1.9x)
			2550 KiB/s (CD 17.0x, DVD 1.8x)
			2400 KiB/s (CD 16.0x, DVD 1.7x)
			2250 KiB/s (CD 15.0x, DVD 1.6x)
			2100 KiB/s (CD 14.0x, DVD 1.5x)
			1950 KiB/s (CD 13.0x, DVD 1.4x)
			1800 KiB/s (CD 12.0x, DVD 1.3x)
			1650 KiB/s (CD 11.0x, DVD 1.2x)
			1500 KiB/s (CD 10.0x, DVD 1.1x)
			1350 KiB/s (CD 9.0x, DVD 0.9x)
			1200 KiB/s (CD 8.0x, DVD 0.8x)
			1050 KiB/s (CD 7.0x, DVD 0.7x)
			900 KiB/s (CD 6.0x, DVD 0.6x)
			750 KiB/s (CD 5.0x, DVD 0.5x)
			600 KiB/s (CD 4.0x, DVD 0.4x)
			450 KiB/s (CD 3.0x, DVD 0.3x)
			300 KiB/s (CD 2.0x, DVD 0.2x)
			150 KiB/s (CD 1.0x, DVD 0.1x)
			
Media:
  label:		'Unreal2 Install'
  type:			Commercial CD or Audio CD (has-data)
  is writable:		FALSE
  is appendable:	FALSE
  capacity:		649.55 MiB approx. or 74 mins 3 secs
  size:			649.55 MiB approx. or 74 mins 3 secs
---

---

### Post by noobuntu35 on 2008-08-10
oh and on an off hand note have you tried the man page?
man mount from CLI will give you some commands that may help

---

### Post by noobuntu35 on 2008-08-11
I ran the same command on my system as you did yours to see the output difference. here is mine
*-cdrom                 
       description: DVD-RAM writer
       product: DVD-RAM GSA-H54N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@7:0.0.0 <--- mine is not a scsi device its ide
       logical name: /dev/cdrom <----  next 4 not listed on yours
       logical name: /dev/dvd 
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.00
       serial: [HL-DT-STDVD-RAM GSA-H54N1.0007/04/10
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
here is yours 
 sudo lshw -C disk 
  *-cdrom                 
       description: DVD writer
       product: _NEC DVD_RW ND-3540A
       physical id: 0
       bus info: ide@0.0 <--- ? relevant??? maybe not
       logical name: /dev/hda <--- another really odd difference
       version: 1.04
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2 status=nodisc
do you have another CD/dvd drive to put in and try from another working system?

---

### Post by dalhamir on 2008-08-11
I'll try reading the mount man pages later today, here's the output of the other command you suggested.

$ /usr/lib/nautilus-cd-burner/list_cddrives

Drive:
  name:			_NEC DVD_RW ND-3540A
  device:		/dev/hda
  door:			closed
  type:			CD-R, CD-RW, DVD-R, DVD-RW, DVD+R, DVD+R DL, DVD+RW, CD, DVD
  is mounted:		FALSE
  max read speed:	8467 KiB/s (CD 56.4x, DVD 6.2x)
  max write speed:	8467 KiB/s (CD 56.4x, DVD 6.2x)
  write speeds:		8467 KiB/s (CD 56.4x, DVD 6.2x)
			7056 KiB/s (CD 47.0x, DVD 5.2x)
			5645 KiB/s (CD 37.6x, DVD 4.1x)
			4234 KiB/s (CD 28.2x, DVD 3.1x)
			2822 KiB/s (CD 18.8x, DVD 2.0x)
			1411 KiB/s (CD 9.4x, DVD 1.0x)
			
Media:
  label:		''
  type:			Couldn't open media
  is writable:		FALSE
  is appendable:	FALSE
  capacity:		Could not be determined
  size:			Could not be determined

Not much difference save the speeds listed and of course, the inability to detect media in the drive.

---

### Post by noobuntu35 on 2008-08-11
Why does it appear as an hda dev instead of the cdrom??? when I get home from work today I'll check that it seems like you need to change the device to a cdrom.I don't dare respond until I can look at my books at home. (posting from XP at work LOL)

---

### Post by Bucky Ball on 2008-08-11
I know this sounds crazy but my cd drive crashed the other day in exactly the same circumstances. I restarted the laptop and it was fine again ...

---

### Post by dalhamir on 2008-08-11
@Bucky - yeah, I tried rebooting a couple of times, no good. Maybe I'll try physically unplugging the drive, booting up, then shutting down, plugging it back in, and seeing what happens...

@Noobuntu - not sure what you mean by "Why does it appear as an hda dev instead of the cdrom???" Thanks for trying to figure this out with me...

---

### Post by mc4man on 2008-08-11
While it's not common to be running 8.04 and still be using hdx instead of sdx for hdds (2 out of 3) and scdx for cd/dvd drives there's no reason things can't work properly as such. All your posted info is fine and as it should be and the drive is being detected. That and this
>  No new hardware. It was working,........I've never been able to get it to automount or manually mount again
points more to a hardware than Os problem.

You could  try re seating the ide connector at the back of the drive and if no go maybe get some canned air and blow it out.
While anythings possible the odds are the drive is either dirty (dust on lenses), dying, or dirty and dying.

---

### Post by noobuntu35 on 2008-08-11
lets try this then run this command mount -t udf I just ran it 
here is the new output from
 sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD-RAM GSA-H54N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 1.00
       serial: [HL-DT-STDVD-RAM GSA-H54N1.0007/04/10
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
  *-disk

here is my output from previous command line from before:
description: DVD-RAM writer
product: DVD-RAM GSA-H54N
vendor: HL-DT-ST
physical id: 0.0.0
bus info: scsi@7:0.0.0 <--- mine is not a scsi device its ide
logical name: /dev/cdrom <---- next 4 not listed on yours
logical name: /dev/dvd
logical name: /dev/scd0
logical name: /dev/sr0
version: 1.00
serial: [HL-DT-STDVD-RAM GSA-H54N1.0007/04/10
capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration: ansiversion=5 status=ready
*-medium
physical id: 0
logical name: /dev/cdrom

  -t vfstype
              The  argument following the -t is used to indicate the file sys&#8208;
              tem type.  The file system types which are  currently  supported
              include:  adfs,  affs,  autofs,  cifs,  coda,  coherent, cramfs,
              debugfs, devpts, efs,  ext,  ext2,  ext3,  hfs,  hfsplus,  hpfs,
              iso9660,  jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc, qnx4,
              ramfs, reiserfs, romfs, smbfs, sysv, tmpfs,  udf,  ufs,  umsdos,
              usbfs,  vfat,  xenix,  xfs, xiafs.  Note that coherent, sysv and
              xenix are equivalent and that xenix and coherent will be removed
              at  some  point  in  the future &#8212; use sysv instead. Since kernel

---

### Post by noobuntu35 on 2008-08-11
> **mc4man said:**
> While it's not common to be running 8.04 and still be using hdx instead of sdx for hdds (2 out of 3) and scdx for cd/dvd drives there's no reason things can't work properly as such. All your posted info is fine and as it should be and the drive is being detected. That and this

points more to a hardware than Os problem.

You could  try re seating the ide connector at the back of the drive and if no go maybe get some canned air and blow it out.
While anythings possible the odds are the drive is either dirty (dust on lenses), dying, or dirty and dying.

I agree and am wondering if another working drive has been tried.

---

### Post by noobuntu35 on 2008-08-11
after running mount -t udf this is what this commands output looks like now

/usr/lib/nautilus-cd-burner/list_cddrives
Drive:
  name:			DVD-RAM GSA-H54N
  device:		/dev/scd0
  door:			closed
  type:			CD-R, CD-RW, DVD-RAM, DVD-R, DVD-RW, DVD+R, DVD+R DL, DVD+RW, CD, DVD
  is mounted:		TRUE <---- compare to my last copy/paste
  max read speed:	8468 KiB/s (CD 56.4x, DVD 6.2x)
  max write speed:	8468 KiB/s (CD 56.4x, DVD 6.2x)
  write speeds:		8400 KiB/s (CD 56.0x, DVD 6.2x)
			8250 KiB/s (CD 55.0x, DVD 6.0x)
			8100 KiB/s (CD 54.0x, DVD 5.9x)
			7950 KiB/s (CD 53.0x, DVD 5.8x)
			7800 KiB/s (CD 52.0x, DVD 5.7x)
			7650 KiB/s (CD 51.0x, DVD 5.6x)
			7500 KiB/s (CD 50.0x, DVD 5.5x)
			7350 KiB/s (CD 49.0x, DVD 5.4x)
			7200 KiB/s (CD 48.0x, DVD 5.3x)
			7050 KiB/s (CD 47.0x, DVD 5.2x)
			6900 KiB/s (CD 46.0x, DVD 5.1x)
			6750 KiB/s (CD 45.0x, DVD 4.9x)
			6600 KiB/s (CD 44.0x, DVD 4.8x)
			6450 KiB/s (CD 43.0x, DVD 4.7x)
			6300 KiB/s (CD 42.0x, DVD 4.6x)
			6150 KiB/s (CD 41.0x, DVD 4.5x)
			6000 KiB/s (CD 40.0x, DVD 4.4x)
			5850 KiB/s (CD 39.0x, DVD 4.3x)
			5700 KiB/s (CD 38.0x, DVD 4.2x)
			5550 KiB/s (CD 37.0x, DVD 4.1x)
			5400 KiB/s (CD 36.0x, DVD 3.9x)
			5250 KiB/s (CD 35.0x, DVD 3.8x)
			5100 KiB/s (CD 34.0x, DVD 3.7x)
			4950 KiB/s (CD 33.0x, DVD 3.6x)
			4800 KiB/s (CD 32.0x, DVD 3.5x)
			4650 KiB/s (CD 31.0x, DVD 3.4x)
			4500 KiB/s (CD 30.0x, DVD 3.3x)
			4350 KiB/s (CD 29.0x, DVD 3.2x)
			4200 KiB/s (CD 28.0x, DVD 3.1x)
			4050 KiB/s (CD 27.0x, DVD 2.9x)
			3900 KiB/s (CD 26.0x, DVD 2.8x)
			3750 KiB/s (CD 25.0x, DVD 2.7x)
			3600 KiB/s (CD 24.0x, DVD 2.6x)
			3450 KiB/s (CD 23.0x, DVD 2.5x)
			3300 KiB/s (CD 22.0x, DVD 2.4x)
			3150 KiB/s (CD 21.0x, DVD 2.3x)
			3000 KiB/s (CD 20.0x, DVD 2.2x)
			2850 KiB/s (CD 19.0x, DVD 2.1x)
			2700 KiB/s (CD 18.0x, DVD 1.9x)
			2550 KiB/s (CD 17.0x, DVD 1.8x)
			2400 KiB/s (CD 16.0x, DVD 1.7x)
			2250 KiB/s (CD 15.0x, DVD 1.6x)
			2100 KiB/s (CD 14.0x, DVD 1.5x)
			1950 KiB/s (CD 13.0x, DVD 1.4x)
			1800 KiB/s (CD 12.0x, DVD 1.3x)
			1650 KiB/s (CD 11.0x, DVD 1.2x)
			1500 KiB/s (CD 10.0x, DVD 1.1x)
			1350 KiB/s (CD 9.0x, DVD 0.9x)
			1200 KiB/s (CD 8.0x, DVD 0.8x)
			1050 KiB/s (CD 7.0x, DVD 0.7x)
			900 KiB/s (CD 6.0x, DVD 0.6x)
			750 KiB/s (CD 5.0x, DVD 0.5x)
			600 KiB/s (CD 4.0x, DVD 0.4x)
			450 KiB/s (CD 3.0x, DVD 0.3x)
			300 KiB/s (CD 2.0x, DVD 0.2x)
			150 KiB/s (CD 1.0x, DVD 0.1x)
			
Media:
  label:		'Unreal2 Install'
  type:			Commercial CD or Audio CD (has-data)
  is writable:		FALSE
  is appendable:	FALSE
  capacity:		649.55 MiB approx. or 74 mins 3 secs
  size:			649.55 MiB approx. or 74 mins 3 secs

---

### Post by dalhamir on 2008-08-12
wow, somehow I never expected a drive to die this quickly working one minute, not working the next, crazy. I've had one die before, but it just wouldn't light up or open.

I don't have another working drive handy, but I did boot up in XP with this drive and still nothing detected. XP is having problem and I haven't used it in a month, but it works well enough to test the drive. I tried cleaning the lens with some compressed air, but no luck either.

Sorry noobuntu, thanks for trying to help with a problem that ended up being just bad hardware and not a software issue at all.

---

### Post by noobuntu35 on 2008-08-12
> **dalhamir said:**
> wow, somehow I never expected a drive to die this quickly working one minute, not working the next, crazy. I've had one die before, but it just wouldn't light up or open.

I don't have another working drive handy, but I did boot up in XP with this drive and still nothing detected. XP is having problem and I haven't used it in a month, but it works well enough to test the drive. I tried cleaning the lens with some compressed air, but no luck either.

Sorry noobuntu, thanks for trying to help with a problem that ended up being just bad hardware and not a software issue at all.

Sometimes it is hardware sometimes it's not. The good news is I mounted my drive through helping you out.Thanks for the response that the hardware was the issue (it's what I was thinking to begin with) don't forget to mark this thread as Solved

---

