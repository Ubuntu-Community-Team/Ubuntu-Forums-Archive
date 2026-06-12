---
title: "usb flash drive problem! need data recovery advice"
date: 2009-11-03
forum: Hardware
---

### Post by neologix on 2009-11-03
hi there. i'm at my wit's end with this problem. i have a usb flash drive that's been working well since the day i bought it (late last year or early this year) up until today. i put it in a laptop it's never been in before, and the laptop (compaq 6710b running new york public library windows build, novell i think) couldn't read the drive. i took it out using "safely remove hardware," then later that day i tried putting it in an imac (one it's worked on many times before) and the imac couldn't read it. later i plugged it into my alienware laptop (my normal comp running jaunty & xp) and xp system tray gave me the "found new hardware" balloons and said it was a "2231 PRAM" usb device.

I CANNOT READ ANYTHING FROM THIS DRIVE. it seems to be unpartitioned and i don't dare format it cuz it has/had data i need/still want. google's no help. are there any data recovery measures i can take to restore this usb drive?

drive is a kingston datatraveler 150 usb flash drive 32gb, tho from google i've read this happened to verbatim brand flash drives as well. my drive was formatted fat32 and has had no problem moving btwn linux, mac, & win b4 2day.

---

### Post by Dreamglider on 2009-11-12
You should install testdisk and photorec, it's essential for data recovery.

TestDisk is a partition recovery/manipulation tool and it is you friend.

Photorec does not care about the filesystem it look's for headers and extracts the data of lots and lots of file extensions and it is also your friend :)

---

### Post by Dreamglider on 2009-11-12
> **Dreamglider said:**
> You should install testdisk and photorec, it's essential for data recovery.

TestDisk is a partition recovery/manipulation tool and it is you friend.

Photorec does not care about the filesystem it look's for headers and extracts the data of lots and lots of file extensions and it is also your friend :)

Oh yea here is the link -> [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by neologix on 2009-11-16
testdisk is not reading the usb drive, even tho it's plugged in. also, on mac (cuz i'm not on my linux ATM) ```
testdisk /dev/disk1
``` (at least, i'm assuming it would've been mounted on disk1 since disk0 is the mac's hdd) doesn't work.

---

