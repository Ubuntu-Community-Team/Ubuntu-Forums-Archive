---
title: "The Case of the Disappearing CD/DVD"
date: 2008-09-13
forum: Hardware
---

### Post by Belgatom on 2008-09-13
Here's the story. 

IN April, after some carefull consideration, I switched to Ubuntu for good. Hardy Heron for it's LTS. Everything went smoothly. My machine has 5 hard disks and one CD/DVD drive. I mount one of my disks permantently, the rest just whenever I need them. Recently, I upgraded some hardware. New Videocard, new memory and I removed one of my SATA disks for a few tests in another system. Everything looked great, Ubuntu found new Graphics Card and downloaded new drivers. For the rest, nothing changed much. 

Untill I wanted to rip an new cd I bought. I put in the CD/DVD drive, nothing happened. Then I noticed in Diskmounter (thingie on my bar) that my CD/DVD wasn't mounted. Strange I thought, oh well, let's just mount it like I do the other disks. 

```
mount: special device /dev/scd0 does not exist
```

I rebooted and went in the Bios to see if it wasn't found (but then it wouldn't show up in Diskmounter). And there it was. I decided to try another CDwriter drive which I had lying around. No change there. Still got found in Bios, found by Diskmounter but not mountable.

Next I checked out Fstab (I had to look up all these things, it's not like I am a Linux specialist)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=833bf90a-3ef3-402e-aab3-418f77764853 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=87f39345-89c1-477d-bda7-d1194680ef4d /home           ext3    relatime        0       2
# /dev/sda5
UUID=32ad76c1-6b8c-4fa3-ab11-57910bc7679c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1	/media/MusicDisk ntfs defaults,locale=en_US.UTF-8 0 1
```

I showed it to some friends of mine who have been running Ubuntu longer than me. ONe suggested to rem the /dev/scd0 line, as the CDrom should be mounted automatically. 

Did that. Only change that made, was that in Diskmounter, one of the diskicons disappeared. (Makes kinda sense to me).

I went the hardware way and started swapping cables around but to no avail. Finally I looked up how I could find out it Ubuntu actually realised there was a CDdrive present. 

```
belgatom@chieftec:~$ dmesg |grep CD 
[   25.428968] scsi 1:0:1:0: CD-ROM            LITEON   CD-ROM LTN526    YH0X PQ: 0 ANSI: 5
[   26.421974] Uniform CD-ROM driver Revision: 3.20
[   26.422031] sr 1:0:1:0: Attached scsi CD-ROM sr0
```

I assume this means, it does. So why can't I mount it. 

Typically human off course, but now I can find a thousand of uses why I need that CDdrive. 

Please help if you can.

---

### Post by IntuitiveNipple on 2008-09-13
That extract from dmesg seems to show the device is known about. Check that the system has only the one SCSI CD device node:
```

ls -1 /dev/scd*

/dev/scd0

```
The next thing is to find out if udev has created the device node correctly. Here's the command to use and example output so you know what to expect. Adjust the **--name=** value if it is different on that system:
```

udevinfo --query=all --name=scd0

P: /block/sr0
N: scd0
S: disk/by-path/pci-0000:00:1f.1-scsi-0:0:0:0
S: sr0
S: cdrom
S: cdrw
S: dvd
S: dvdrw
E: ID_CDROM=1
E: ID_CDROM_CD_R=1
E: ID_CDROM_CD_RW=1
E: ID_CDROM_DVD=1
E: ID_CDROM_DVD_R=1
E: ID_CDROM_DVD_RAM=1
E: ID_CDROM_MRW=1
E: ID_CDROM_MRW_W=1
E: ID_CDROM_RAM=1
E: DEVTYPE=disk
E: ID_VENDOR=MATSHITA
E: ID_MODEL=DVD-RAM_UJ-850S
E: ID_REVISION=1.60
E: ID_SERIAL=
E: ID_SERIAL_SHORT=Uu&#65533;
E: ID_TYPE=cd
E: ID_BUS=scsi
E: ID_PATH=pci-0000:00:1f.1-scsi-0:0:0:0
E: GENERATED=1

```

---

### Post by Belgatom on 2008-09-13
```
~$ udevinfo --query=all --name=scd0
P: /block/sr0
N: scd0
S: disk/by-path/pci-0000:00:1f.1-scsi-1:0:1:0
S: sr0
S: cdrom1
S: cdrw1
S: dvd1
S: dvdrw1
E: ID_CDROM=1
E: ID_CDROM_MRW=1
E: ID_CDROM_MRW_W=1
E: ID_CDROM_RAM=1
E: DEVTYPE=disk
E: ID_VENDOR=LITEON
E: ID_MODEL=CD-ROM_LTN526
E: ID_REVISION=YH0X
E: ID_SERIAL=
E: ID_SERIAL_SHORT=
E: ID_TYPE=cd
E: ID_BUS=scsi
E: ID_PATH=pci-0000:00:1f.1-scsi-1:0:1:0
E: GENERATED=1

```

This is what I got. Don't know for sure what to look for. Looks pretty much the same like yours. 

Extra info:

Friend asked to see of /dev/sr0 existed. It did with following properties:
[Here's a screenshot]("http://users.telenet.be/belgatom/ubuntu/sr0.png")

---

### Post by IntuitiveNipple on 2008-09-13
Well that is looking good. Just as a confirmation can you show the results of these commands (I've included example output for comparision):
```

ls -l /dev/scd*

brw-rw----+ 1 root cdrom 11, 0 2008-09-13 10:42 /dev/scd0

ls -l /dev/sr*

lrwxrwxrwx 1 root root 4 2008-09-13 09:42 /dev/sr0 -> scd0

```

---

### Post by IntuitiveNipple on 2008-09-13
Daft question I know, but never assume the obvious! Does the mount-point exist?
```

ls -ld /media/cdrom*

lrwxrwxrwx  1 root  999    6 2008-07-08 15:43 /media/cdrom -> cdrom0
dr-xr-xr-x 10 root root 2048 2008-07-02 11:47 /media/cdrom0

ls -l /dev/* | grep scd

lrwxrwxrwx  1 root   root           4 2008-09-13 09:42 /dev/cdrom -> scd0
lrwxrwxrwx  1 root   root           4 2008-09-13 09:42 /dev/cdrw -> scd0
lrwxrwxrwx  1 root   root           4 2008-09-13 09:42 /dev/dvd -> scd0
lrwxrwxrwx  1 root   root           4 2008-09-13 09:42 /dev/dvdrw -> scd0
brw-rw----+ 1 root   cdrom    11,   0 2008-09-13 10:42 /dev/scd0
lrwxrwxrwx  1 root   root           4 2008-09-13 09:42 /dev/sr0 -> scd0


```

---

### Post by IntuitiveNipple on 2008-09-13
This seems to be a frequently occurring but little-understood issue. From the other articles I've read the suggestion is there is an interrupt-related problem, and there might be clues in the system log when a CD or DVD is inserted.

Can you do these tests? 

Remove the current kern.log file and restart the log daemon (so we have a fresh log-file that can just capture the CD insertion events, if any), and run the udev monitor:
```

sudo rm /var/log/kern.log
sudo touch /var/log/kern.log
sudo /etc/init.d/sysklogd restart

sudo udevmonitor --environment

```
Now insert a disk you know is good into the drive. If you're lucky there should be several udev events reported. They'll look like this:
```

UEVENT[1221309031.893199] add      /module/udf (module)
ACTION=add
DEVPATH=/module/udf
SUBSYSTEM=module
SEQNUM=3137

```

Give it 30 seconds and the exit the monitor by pressing Ctrl+C.

Now copy the reports from udevmonitor to a reply here, and also attach a (compressed) copy of kern.log:
```

cd ~
pwd
cat /var/log/kern.log | gzip kern.log.gz

```

---

### Post by Belgatom on 2008-09-13
```
belgatom@chieftec:~$ sudo udevmonitor --environment
udevmonitor will print the received events for:
UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent

belgatom@chieftec:~$
```

Nothing happened, no code to paste. Inserted CDrom I first doublechecked on my wife window machine. 

Concerning the kern.log. Something must have gone wrong because it's empty. Nothing inside. 0 bytes size. 

The last three lines of code, didn't work though. 

```
cat /var/log/kern.log | gzip kern.log.gz
```

gave 

```
gzip: kern.log.gz: No such file or directory

```

As you mention, this a frequently occuring issue: how have other people solved this problem? 

(I really hope your answer to the last question doesn't have the word "format" in it. But give it to me straight, I can take it. )

---

### Post by Belgatom on 2008-09-29
Bump.

I'm really bummed out that something like this can happen. It's doing my head in. I've been working with windows for over 15 years and never had something like this happen, many other weird things that caused me to format but this, this seems so simple.

Just an "in-case" question. If I would replace my CD/DVD writer by a sata version, would it solve my problem? As I wrote in the previous posts, I've changed the CD/DVD writer with other ones, without resolve.

---

### Post by bobromeo on 2008-10-01
In my case 2 disappeared:
```
henk@mqnp:~$ ls -l /dev/scd*
brw-rw----+ 1 root cdrom 11, 0 2008-10-01 23:28 /dev/scd0
brw-rw----+ 1 root cdrom 11, 1 2008-10-01 23:28 /dev/scd1
henk@mqnp:~$ ls -l /dev/sr*
lrwxrwxrwx 1 root root 4 2008-10-01 23:29 /dev/sr0 -> scd0
lrwxrwxrwx 1 root root 4 2008-10-01 23:29 /dev/sr1 -> scd1
henk@mqnp:~$ ls -ld /media/cdrom*
lrwxrwxrwx 1 root root    6 2006-11-15 13:57 /media/cdrom -> cdrom0
drwxrwxrwx 2 root root 4096 2006-11-15 13:57 /media/cdrom0
drwxr-xr-x 2 root root 4096 2006-11-15 13:57 /media/cdrom1
henk@mqnp:~$ 
henk@mqnp:~$ ls -l /dev/* | grep scd
lrwxrwxrwx  1 root   root           4 2008-10-01 23:29 /dev/cdrom2 -> scd1
lrwxrwxrwx  1 root   root           4 2008-10-01 23:29 /dev/cdrom3 -> scd0
lrwxrwxrwx  1 root   root           4 2008-10-01 23:29 /dev/cdrw2 -> scd1
lrwxrwxrwx  1 root   root           4 2008-10-01 23:29 /dev/dvd3 -> scd0
brw-rw----+ 1 root   cdrom    11,   0 2008-10-01 23:28 /dev/scd0
brw-rw----+ 1 root   cdrom    11,   1 2008-10-01 23:28 /dev/scd1
lrwxrwxrwx  1 root   root           4 2008-10-01 23:29 /dev/sr0 -> scd0
lrwxrwxrwx  1 root   root           4 2008-10-01 23:29 /dev/sr1 -> scd1

```Why do I have 2 and 3 in my output ?

---

### Post by bobromeo on 2008-10-01
Can this maybe helped with a backport ?
If yes, which ?:)

---

### Post by bobromeo on 2008-10-01
Is upgraded firmware the answer ?
Why would I need new firmware ?
My CD-player worked fine since Edgy:)

Where to get the firmware ?
No more windows98 on this machine .....

---

### Post by bobromeo on 2008-10-04
This morning i put the 'mounting'-applet (translated) on the top-panel and tried it: Mounting error:
```
mount: special device /dev/hdc does not exist

```
This applet shows 3 devices, the 3d says
```
mount: special device /dev/cdrom does not exist

```
After this i opened the drive and closed it again, surprise the CD was there:D, the applet showed an extra device with the icon of a CD. The microhelp shows 'CD-ROM/DVD-ROM-station' but then again, it has always been this device. Conclusion: some things changed in the lat 2 years, maybe by hardy or gutsy ?

Maybe have to learn how this mounting stuff worx:(

---

