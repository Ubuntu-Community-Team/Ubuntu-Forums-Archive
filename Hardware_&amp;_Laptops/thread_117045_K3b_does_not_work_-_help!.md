---
title: "K3b does not work - help!"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by debernardis on 2006-01-14
Trying to burn dapper iso image... no joy.
Here's the output from k3b:

```

System
-----------------------
K3b Version: 0.12.7

KDE Version: 3.5.0
QT Version:  3.3.4
Kernel:      2.6.12-9-k7
Devices
-----------------------
MATSHITA UJ-840D 1.02 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R sequenziale; DVD-RW a riscrittura limitata; DVD-RW sequenziale; DVD+RW; DVD+R; DVD+R a doppio strato; CD-ROM; CD-R; CD-RW] [SAO; TAO; Riscrittura limitata]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-9-k7
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
/usr/bin/X11/cdrecord: Device or resource busy. Cannot open '/dev/hdc'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=10 -dao driveropts=burnfree -data /home/debernardis/Desktop/dapper-live-i386.iso 

```

I understand that it has difficulties opening /dev/hdc, plus it doesn't like my kernel. Right?

---

### Post by curuxz on 2006-01-14
Have you tried running as root?

That can sometimes bypass access errors

---

### Post by debernardis on 2006-01-14
Sudo su and then k3b were worse if possible:

```

debernardis@zv6:~$ sudo su
Password:
root@zv6:/home/debernardis# k3b
Link points to "/tmp/ksocket-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-8475' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

k3b: cannot connect to X server :0.0
ERROR: KUniqueApplication: Registering failed!
ERROR: Communication problem with k3b, it probably crashed.
root@zv6:/home/debernardis#

```

sudo k3b gives this:

```

debernardis@zv6:~$ sudo k3b
ERROR: Communication problem with k3b, it probably crashed.
debernardis@zv6:~$ k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
Error: "/var/tmp/kdecache-debernardis" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-debernardis" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
Error: "/tmp/ksocket-debernardis" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"

```

---

### Post by debernardis on 2006-01-14
[Nerolinux]("http://www.nero.com/en/nerolinux-prog.html") Just Worked (TM).

---

### Post by newuser111 on 2006-01-14
run k3b-setup and click apply

---

### Post by debernardis on 2006-01-14
Been there, bought the t-shirt, but no results. One thing that I tried, is selecting the first item (translating from Italian, should be "use writing group: burning". When I select that, k3bsetup complains there's no 'burning' group.
Should create it some way? (Thanks for responses)

---

