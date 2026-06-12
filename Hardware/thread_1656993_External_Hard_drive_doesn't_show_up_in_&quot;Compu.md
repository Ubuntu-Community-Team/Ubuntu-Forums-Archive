---
title: "External Hard drive doesn't show up in &quot;Computer&quot; or Desktop"
date: 2010-12-31
forum: Hardware
---

### Post by TobiasRipper on 2010-12-31
Hi, I have a perfectly functioning 500GB external hard drive. It functions perfectly on our windows based computers.

well. first of all. I'm not sure where it is supposed to show up... I know that my usb flash card shows up in "Computer" and desktop. But when I plug in the drive... nothing happens. 

BUT when I open System > Administration > Disk Utility, it show my drive as:
Preripheral Devices:
[USB, Firewire and other peripherals]
   Hard Disk
   [JMicron USB to ATA/ATAPI Bridge] (which I take is the usb boxing    throught which my HDD is connected)

This hard drive has some important to me data which I can't afford to lose.
My ultimate goal is to make Linux see that contents of the hard drive.

Thank you in advance

---

### Post by Tamrac on 2010-12-31
Look at your fstab config.... comment out entry with an SDA that's mounted to /. For some reason, sometimes when installing from a LIVE CD via USB stick. It leaves this entry. And therefore conflicts with your internal hardrive's mount points.

---

### Post by TobiasRipper on 2010-12-31
Hmm... I don't know what happened, but I left the drive connected and restarted the os and the drive shewed up... 

I apologize if I sound cocky but I'm a total noob in Linux and your explanation doesn't really give me a clue of what I have to do... sorry again if I sound rude. Maybe it's the very basics of linux but I don't even know that...

---

