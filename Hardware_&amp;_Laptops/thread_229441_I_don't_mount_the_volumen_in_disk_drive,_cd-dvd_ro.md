---
title: "I don't mount the volumen in disk drive, cd-dvd rom an cd-dvd recorder"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by Mmarvaloca on 2006-08-04
Hi!
I have installed 4.10 (Warty Warthog) in an AMD K7 Athlon. When finish, I am going to test a cd but I see that me does not recognize the units and that not the volume of the disk drive mounts me, of the read-only cd-dvd and of the recorder of cd-dvd.  It gives me the following errors:  
Disk Drive:
mount: I could not determine the filesystem type, and none was specified
Cd-dvd and of the recorder of cd-dvd:
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
or too many mounted file system

mount: No medium found

I have tried solutions that have seen for internet: mount-to; mount /dev/hdd /average/cdromo but al not to have many know-how not itself as to solve the problem.
root@ubuntumaki:/home/pinxs00 # mount /dev/hdd /media/cdrom -t iso9660
mount: block device /dev/hdd is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
or too many mounted file systems
root@ubuntumaki:/home/pinxs00 #

I facilitate information, if serves of aid of the fstab, mtab and of the dmesg.
Thanks beforehand by the possible aid

etc/fstab:

# /etc/fstab: static file system information.
#
#
proc /proc proc defaults 0 0
/dev/hdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

/etc/mtab:

/dev/hdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0

dmesg:

st: I/O error, dev hdd, sector 1020996
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019972
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019748
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1020404
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019380
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019156
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1020396
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019372
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019148
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837772
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836748
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836524
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837764
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836740
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836516
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837172
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836148
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 835924
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837164
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836140
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 835916
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1248
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1024
UDF-fs: No partition found (1)
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 64
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1021004
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019980
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019756
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1020996
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019972
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019748
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1020404
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019380
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019156
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1020396
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019372
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019148
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837772
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836748
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836524
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837764
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836740
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836516
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837172
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836148
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 835924
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837164
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836140
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 835916
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1248
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1024
UDF-fs: No partition found (1)
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 64
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1021004
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019980
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019756
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1020996
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019972
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019748
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1020404
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019380
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019156
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1020396
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019372
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019148
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837772
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836748
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836524
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837764
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836740
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836516
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837172
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836148
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 835924
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837164
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836140
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 835916
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1248
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1024
UDF-fs: No partition found (1)
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 64
isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 64
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1021004
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019980
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019756
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1020996
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019972
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019748
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1020404
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019380
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019156
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1020396
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019372
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1019148
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837772
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836748
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836524
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837764
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836740
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836516
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837172
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836148
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 835924
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 837164
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 836140
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 835916
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1248
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 1024
UDF-fs: No partition found (1)
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x51
end_request: I/O error, dev hdd, sector 64
isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16
root@ubuntumaki:/home/pinxs00 #


P.d.: Another question (do not I know if has relation with the previous thing) :  The sound does not function and do not I know because (I have installed OSS Mixer and ALSA mixer), I have killed the devil of the sound: killall esd but nothing.  I have installed alsa-base and alsa-utils but nothing.  As the following thing command information:  Root@ubuntumaki:/home/pinxs00 # lspci | grep -i audio 0000:00:11.5 Multimedia audio controller:  VIA Technologies, Inc.  VT8233/A/8235/8237 AC97 Audio
Controller (rev 50) root@ubuntumaki:/home/pinxs00 # ls -the /total dev/snd 0 drwxr-xr-x 2 root root 160 2006-08-04 13:23.  Drwxr-xr-x 9 root root 4460 2006-08-04 13:23..  Crw-rw---.  - 1 root audio 116, 0 2006-08-04 13:23 controlC0 crw-rw---.  - 1 root audio 116, 24 2006-08-04 13:23 pcmC0D0c crw-rw---.  - 1 root audio 116, 16 2006-08-04 13:23 pcmC0D0p crw-rw---.  - 1 root audio 116, 25 2006-08-04 13:23 pcmC0D1c crw-rw---.  - 1 root audio 116, 17 2006-08-04 13:23 pcmC0D1p crw-rw---.  - 1 root
audio 116, 33 2006-08-04 13:23 timer

Be it more possible patients, I am not more than a user recien arrived at Linux!

---

