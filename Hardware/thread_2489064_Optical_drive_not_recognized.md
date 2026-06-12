---
title: "Optical drive not recognized"
date: 2023-07-17
forum: Hardware
---

### Post by azmanam2 on 2023-07-17
I have a BluRay DVDROM drive in my tower PC running Ubuntu 18.04.6 bionic. The drive is at most 5-6 years old.

Lately, sometimes it works, sometimes it doesn't. What I mean is, I can push the eject button, insert a disk, close the drive and hear it spin, but I cannot access the contents. Doesn't matter if it's a blank disk, an audio CD, a DVD, or a BluRay.

The odd part (to me, at least) is in my terminal queries of the drive , sometimes it appears to show that it is installed, and recognized. Sometimes it doesn't exist.

Let me show you. Here's what I currently see when I query the drive:

```
sudo lshw -short
    #No entry for /dev/cdrom

sudo lshw -C disk
    #No entry for *-cdrom

sudo lsblk
    #No entry for sr0

ls -l /dev/sr0
    ls: cannot access 'dev/sr0': No such file or directory

wodim dev=/dev/sr0 --scanbus
    wodim: No such file or directory
    Cannot open SCSI driver!

wodim dev=/dev/sr0 -devices
    wodim: No such file or directory
    Cannot open SCSI driver!

sudo blkid
    #No entry for /dev/
```

But sometimes it looks like this, but still doesn't work:

```
sudo lshw -short
    #There is an entry for /dev/cdrom

sudo lshw -C disk
    *-cdrom
        description: DVD-RAM writer
        ...
        configuration: ansiversion=5 status=ready
        physical id: 0
        logical name: /dev/cdrom

sudo lsblk
    sr0    11:0    1    7.4G    0    rom

ls -l /dev/sr0
    brw-rw----+ 1 root cdrom 11, 0 May 29 16:42 /dev/sr0

wodim dev=/dev/sr0 --scanbus
    6,0,0    'HL-DT-ST'    'BDDVDRW UH12NS40'    '1.01'    Removable CD-ROM
    ...

wodim dev=/dev/sr0 -devices
    ----------
    0    dev='/dev/sr0'    rwrw--    :    'HL-DT-ST'    'BDDVDRW UH12NS40'
    ----------

sudo blkid
    /dev/sr0:    UUID="..." LABEL="..." TYPE="udf"
```

But when I inserted a disk and tried to run VLC, VLC gave the following output: 
```
Playback failure:
DVDRead could not open the disk "/dev/sr0"
Your input can't be opened:
VLC is unable to open the MRL 'dev:///dev/sr0'. Check the log for details.

#VLCLogFile:
dvdread error: DVDRead cannot open source: /dev/sr0
```

Then I restarted the computer, and the terminal queries went back to the top example where the drive wasn't recognized.

Based on some other resources I've looked at, it also seems odd that there are no entries for sr_mod or sg:

```
lsmod | grep sr_mod
    #should output something, but currently isn't
lsmod | grep sg
    #should output something, but currently isn't
```

I've tried doing *sudo mount -t auto /dev/cdrom /media/cdrom*, but I get the error *mount: /media/cdrom: special device /dev/cdrom does not exist*.

I've tried moving the SATA cable to a new port. I've tried replacing the SATA cable. I've tried using a different power port on the same power strip (that's also used to power the hard disks).

Sometimes it will work for a day or two, then stop again. It is an infrequently used drive. I'll use it to rip a bunch of movies to my hard drive over a weekend or something, then not use it again for months or longer.

Please help me get my optical drive to work consistently!

---

