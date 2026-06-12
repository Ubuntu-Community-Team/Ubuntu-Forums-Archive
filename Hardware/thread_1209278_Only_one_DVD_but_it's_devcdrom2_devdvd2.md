---
title: "Only one DVD but it's /dev/cdrom2 /dev/dvd2"
date: 2009-07-10
forum: Hardware
---

### Post by funkydan2 on 2009-07-10
Hi,

I've only got one DVD drive connected to my system, but it's called /dev/dvd2!

The output of lshw is
```

*-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-H12N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom2
                logical name: /dev/dvd2
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: UL02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open

```

I think this has happened because I used to have two DVD drives in this machine (called /dev/dvd and /dev/dvd1) which I have taken out and replaced with the current drive. For some reason HAL must remember that other devices used to be called dvd and dvd1 and therefore has assigned the name dvd2 to this drive. How can I get HAL to forget about the previous drives and give this drive a more sensible name.

Daniel

---

### Post by agruman on 2009-07-14
Hi,

Check '/etc/udev/rules.d/70-persistent-cd.rules', it should have 3 different drives present and their appropriate rules.

You can probably remove all lines referencing your old rives, and remove the '2' after cdrom, dvd aso to get the symlinks right.

BR agru

---

### Post by funkydan2 on 2009-07-14
thanks for that.

---

### Post by funkydan2 on 2009-07-15
For those who might come here via a search, what I did in the end is
```
sudo mv 70-persistant-cd.rules 70-persistant-cd.rules.old
```
and then rebooted. A script automatically made a new persistant file which reflected the current hardware.

Daniel

---

