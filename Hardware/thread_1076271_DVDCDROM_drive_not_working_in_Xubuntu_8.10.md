---
title: "DVD/CDROM drive not working in Xubuntu 8.10"
date: 2009-02-21
forum: Hardware
---

### Post by mister_playboy on 2009-02-21
Hello to everyone.  I am eternally grateful for all the wisdom I have gained by looking through this forum. :)

I would like to ask about a problem I am having on my second laptop, a vintage Gateway 3100.  The CD/DVD drive does not work in Xubuntu 8.10.  It definitely works, as I installed Xubuntu from it originally, and I recently installed BeOS (!!!) from it to dual boot with... {it doesn't work in BeOS either... ;)}  If I put a music CD in and open Music Player, it displays the first (and only the first) track's length correctly, but refuses to play.  DVDs seem to get no response at all.

sudo mount /dev/scd0 with a disk in the drive gives:

mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail gives:

[ 2752.628142] end_request: I/O error, dev sr0, sector 1055092
[ 2752.891138] end_request: I/O error, dev sr0, sector 1056332
[ 2753.174308] end_request: I/O error, dev sr0, sector 1055084
[ 2753.729968] end_request: I/O error, dev sr0, sector 1248
[ 2753.993130] end_request: I/O error, dev sr0, sector 2496
[ 2754.255860] end_request: I/O error, dev sr0, sector 1248
[ 2754.518708] end_request: I/O error, dev sr0, sector 2496
[ 2754.518826] UDF-fs: No partition found (1)
[ 2754.865148] end_request: I/O error, dev sr0, sector 64
[ 2754.865270] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

The device comes up in $ sudo lshw -C disk:

 *-cdrom
       description: DVD reader
       product: DVD-ROM SR-8171
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 059d
       serial: [MATSHITADVD-ROM SR-8171 059dPPx 06/04/98
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

Finally, the contents of my /etc/fstab:

# /dev/sda1
UUID=c6cb82aa-ff06-4734-a8c8-08f650e15cd9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=498d3a4a-e3ee-4161-ab3a-b2a4d0b3e115 none            swap    sw              0       0
/dev/scd0 /media/cdrom0 udf,iso9660 auto,user,ro,exec 0 0

I'm about out of ideas at that point... could anyone help me?  I managed to get a wireless G card working with this computer via Ndiswrapper, so I'm certainly resourceful, but I'm stuck with this one.

Thank you.

---

### Post by mister_playboy on 2009-02-21
I just wanted to add that it does, infact, work in BeOS.  So this is definitely a solvable problem... :)

---

