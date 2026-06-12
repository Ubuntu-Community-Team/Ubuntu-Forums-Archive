---
title: "Unable to mount dvd movie"
date: 2008-11-28
forum: General Help
---

### Post by v1nny on 2008-11-28
Since upgrading to 8.10 (intrepid ibex), I've been able to play DVD movies.  They do not automount, and "mount /media/cdrom0" results in the error message: "mount: No medium found".  Burned DVD data disks and CDs automount without a problem.  Based on forum searches I've tried commenting out the /dev/scd0 line in my /etc/fstab to no effect. The output of "dmesg" does not show any lines after I attempt to insert a DVD movie disk.  Since I had been planning to do so anyway, I did a fresh install of 8.10 which had no impact on the problem. I suspect this may be an issue with UDF support, but haven't been able to track down a solution.

My system is an Intel Core 2 Duo with 2gigs of Ram.  My DVD drive is a Lite-On SATA DVD+/-RW DL.

The same disc mounts without a problem on my 8.04 server.

My /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/main-root
UUID=c41c4f96-4cde-42d6-bc81-0664a24374c7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=8781145b-910f-415d-b3b6-6af95d801273 /boot           ext2    relatime        0       2
# /dev/mapper/main-home
UUID=8098bced-7729-4bec-985b-ae1ccd8dbdcc /home           ext3    relatime        0       2
# /dev/mapper/main-var
UUID=fb9f6e5b-7710-443f-97f4-0e4a2d442a7f /var            ext3    relatime        0       2
# /dev/mapper/main-swap
UUID=fa680c15-eb10-4b5b-8309-19da289b3c1e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 0
none		/tmp		tmpfs	size=500m	0 0

```

uname -a
```
Linux ferdinand 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux
```

Any help would be greatly appreciated.  This is the first problem I've encountered on Ubuntu that I haven't been able to fix with a google search.

Thanks,
v1nny

---

### Post by cariboo on 2008-11-28
Have you got libdvdcss2 installed? Without the library you may get the error that therre is no disk in the drive.

You can install libdvdcss2 from the medibuntu repositories here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Scroll down to get the gpg key.

Jim

---

### Post by v1nny on 2008-11-29
Yup, I have libdvdcss2 installed.

```

$ dpkg -l libdvdcss2
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libdvdcss2     1.2.10-0.2medi Simple foundation for reading DVDs - runtime

```

---

### Post by doas777 on 2008-11-29
have you tried mounting as sudo? I usually have to, since I locked down mount with bastille. 

just a though

---

### Post by v1nny on 2008-11-29
```

$ sudo mount /dev/scd0 /media/cdrom0
mount: No medium found

```

Manually mounting as root did not work either.  This morning I unburied an old IDE DVD drive.  It succesfully mounts and plays DVD movies.  Its just the SATA DVD player that is having problems.  It gave me a thought, so I tried regionset to see if the region was set:

```

$ sudo regionset /dev/scd1 
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n

```

That looked OK to me as well.  Any other ideas as to what the problem may be?  Thanks for all the suggestions thus far.

v1nny

---

### Post by mc4man on 2008-11-29
There have been continuing issues with the combo of sata dvd drives, the mobo, and any particular kernel, some combo's work, others don't and how they don't work can vary.

Out of curiosity what does this show in regards to the sata dvd drive

```
sudo lshw -C disk
```

And is it listed in ..../70-persistent-cd.rules

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

Edit sorry was not paying attention  - thought your drive wasn't finding any media, above is worthless in your case

---

### Post by v1nny on 2008-11-29
On the off chance that this might be useful:

```

$ sudo lshw -C disk
  *-cdrom                 
       description: DVD writer
       product: DVD DUAL 4XMax
       vendor: GENERIC
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 2.17
       serial: 'GENERIC DVD DUAL 4XMax  2.170
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
  *-disk
       description: ATA Disk
       product: ST3320620AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@6:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 9QF1F1C7
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000489a5
  *-cdrom
       description: DVD-RAM writer
       physical id: 1
       bus info: scsi@7:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/cdrw2
       logical name: /dev/dvd2
       logical name: /dev/dvdrw2
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc
  *-disk:0
       description: SCSI Disk
       product: STORAGE DEVICE
       vendor: Generic
       physical id: 0.0.0
       bus info: scsi@10:0.0.0
       logical name: /dev/sdb
       version: 0128
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk:1
       description: SCSI Disk
       product: STORAGE DEVICE
       vendor: Generic
       physical id: 0.0.1
       bus info: scsi@10:0.0.1
       logical name: /dev/sdc
       version: 0128
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdc

```

The first cdrom is the IDE drive I have connected for testing.  The second cdrom drive is my SATA DVD drive with problems.  /dev/sdb and /dev/sdc is a USB flash reader.

```

$ cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
#  (pci-0000:00:0f.0-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
#  (pci-0000:00:0d.0-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-0:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-0:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-0:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-0:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
#  (pci-0000:00:0e.0-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0e.0-scsi-1:0:0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0e.0-scsi-1:0:0:0", SYMLINK+="cdrw2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0e.0-scsi-1:0:0:0", SYMLINK+="dvd2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0e.0-scsi-1:0:0:0", SYMLINK+="dvdrw2", ENV{GENERATED}="1"

```

I tried moving my SATA drive to another SATA port on my motherboard.  Hence the three entries in the rules above.

Thanks,
v1nny

---

### Post by mc4man on 2008-11-29
Don't see anything (see edit though
For future use you can always 'reset' your 70...rules by deleting the entries and rebooting (good pratice after changing, or adding drives. Just replace cat with sudo gedit
Just leave as such
> # This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.


When you ran the lshw was there a comm. dvd in the sata drive?

Edit: if your going to have 2 drives then you should add another fstab entry
> 
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

It also appears that your sata drive **was** and is /dev/scd1

---

### Post by Kevbert on 2008-11-29
You're lucky, I have a LiteOn SATA DVD drive which only shows up as a CD drive with lshw. The model is an LH-20A1S which is a dual layer DVDRW + DVDRAM. When I try a DVD in the drive, it reboots the PC. My IDE Samsung SH-S202J DVD+RAM drive works fine.

---

### Post by v1nny on 2008-11-29
At this point I've actually deleted the /dev/scd* entries from my /etc/fstab.  CDs and DVDs mount just as well without the entries (when they mount at all).  My SATA cdrom was /dev/scd0 until I hooked up my IDE drive at which point it became /dev/scd1 and the IDE drive was /dev/scd0.

Thanks to Kevbert, the "glass is half full" perspective helped.  It's just frustrating because the drive was working just fine in Hardy.

Thanks everyone!
v1nny

---

### Post by Kevbert on 2008-11-30
The problem I have is that both drives work fine in Windows XP, but never with Ubuntu. This is the only reason why I still have Windows.
Do you get any improvement by removing fstab entries v1nny ?

---

### Post by v1nny on 2008-11-30
No improvement.  The only difference is they mount in /media/<DISC NAME> instead of /media/cdrom0.

v1nny

---

