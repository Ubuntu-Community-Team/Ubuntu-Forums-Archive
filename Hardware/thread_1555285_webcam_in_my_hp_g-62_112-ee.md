---
title: "webcam in my hp g-62 112-ee"
date: 2010-08-17
forum: Hardware
---

### Post by kr_wn20 on 2010-08-17
well im all new to ubuntu and the linux thing and i've been crawling through it since i started and i could find a solution to most of the problems that I came across 
the problem is that im using ubuntu 10.04 and i cant access my webcam i installed cheese but it comes with an error message that it cant connect to my device (/dev/video0)


im really out of choices here so if anybody can help me i'll be very grateful;)

---

### Post by IcarusR on 2010-08-18
We need more info. To identify your webcam please post the output of the following terminal command...

```
lsusb
```

---

### Post by mannyweb.ca on 2010-08-21
Hi I also have a HP-G62 and it's webcam worked for like a week, but then it went to hell and now it'll just hang and mess up my audio settings aswell.

Here is my lsusb.

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b1aa Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Many thanks.

---

### Post by IcarusR on 2010-08-22
Can not find any info on how to get it to work sorry.

---

### Post by mannyweb.ca on 2010-08-30
Got my Webcam to work after I disabled this thing:

> **Avahi will always start even if a .local domain is present**

 The avahi-daemon package, which implements the mDNS "zeroconf" standard, formerly included a check to avoid running when a conflicting .local DNS domain is present, as it was reported that some ISPs advertise such a .local domain on their networks, leaving Ubuntu hosts unable to see names advertised on the local network ([327362]("https://bugs.launchpad.net/bugs/327362")).  In Ubuntu 9.10, avahi-daemon is started regardless. 
It  is possible that this may cause other problems.  If your network is  configured this way, you can disable mDNS using the following command: 

sudo stop avahi-daemon
sudo sed -e '/^start/,+1s/^/#/' /etc/init/avahi-daemon.conf

Got this from this website.  

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

---

