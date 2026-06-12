---
title: "how to detect damaged hard drive"
date: 2008-11-13
forum: Hardware
---

### Post by duffrecords on 2008-11-13
I have a new Seagate 300 GB hard drive that went bad after about a month of use.  The drive itself is under warranty but that doesn't cover data recovery (I was quoted $1700 by Seagate).  It looks like I'm on my own, so I thought I'd learn what tools are available in the open-source world.

I've read a lot of forums but all the advice I've found applies to devices that can be detected by the system--mine is not.  When the drive is powered up, it spins and makes short beeping sounds (almost like a chirp).  If I connect it directly to the SATA port on the motherboard, the system will not boot.  I tried using an external USB HDD enclosure but the system will not recognize it that way.  Nothing new appears in /dev, and lsusb only displays my mouse.  What should I do?

P.S. If your reply is "junk it," then please don't reply.  That scenario has already been thoroughly contemplated.

---

### Post by Mardoct909 on 2008-11-13
> makes short beeping sounds (almost like a chirp)

Ask the manufacturer what that means. Much like a mobo, I bet it's telling you exactly what's wrong with it.

I imagine that the needle or the transfer of info from the needle to the exterior is broken. That'd make it look like nothing's there to a mobo, and it wouldn't boot or be recognized because of it.

---

### Post by TheManzine on 2008-11-13
Mine is currently making the exact same noise and I have made a thread here for it: [http://ubuntuforums.org/showthread.php?t=981080&page=2](http://ubuntuforums.org/showthread.php?t=981080&page=2) but I haven't figured it out yet. Mine makes a chirping noise not a scratching noise the instant I plug it in but it is not recognized in either Windows or Ubuntu.

---

### Post by Mardoct909 on 2008-11-13
Bad news...

I believe [this]("http://tech.vault9.net/forums/lofiversion/index.php/t19629.html") answers today's question. The motor tries to spin but can't move properly. This means data can't be retrieved from the drive, so in short "FUBAR" will suffice. 

The data is still intact, but you can't just crack open the drive and replace the motor; this does damage the data beyond repair. The manufacturer can get the data off it for you, but the process is extremely difficult and costly for them, so it's extremely costly for you.

Either way, it's not working again... though I imagine it would be covered by the warranty.

---

### Post by duffrecords on 2008-11-14
Yeah.  Seagate says it's most likely a mechanical failure.  I can get it repaired or replaced under warranty but then I lose all my irreplaceable data.  I'm going to shop around and see what kind of quotes I can get for recovery services.

:( I can't wait 'til the future gets here and all storage becomes solid-state.

---

### Post by Mardoct909 on 2008-11-14
I'd personally recommend replacing it with two smaller hard drives and keeping critical data on both. Same amount of storage space for everything else, and an easy way to back up data.

Admittedly there might be some difficulties with getting them both to work, but probably not. Just make sure one is set up as a slave.

---

### Post by psusi on 2008-11-14
Nothing is foolproof.  If your data is irreplaceable, then you need to keep multiple copies of it, on different media, stored in different places.

Backups, backups, backups.

---

### Post by gpsmikey on 2008-11-14
On the issue of multiple drives for backing up critical data, one thing to keep in mind - if it is "critical", make sure at least one of your backup forms (which may be a drive) is not always connected to the system the data is on.  I had a power supply fail a while back and it went seriously overvoltage - I could tell by the chip on the disk drive with the crater in the top and the 3 pins melted off -- took out quite a bit of other hardware in the system too !!  Fortunately, I had an image of the system on a drive on another system (in the network) and simply replaced stuff and reloaded the system.  Use a portable drive etc and don't have it always connected.  I see quite a few posts in the windows and photography groups from people that have lost the last 7 years of pictures of their kids growing up because they never had backed it up.  Very sad to see and in most cases, they are indeed gone.

mikey

---

### Post by duffrecords on 2009-01-30
> **psusi said:**
> Nothing is foolproof.  If your data is irreplaceable, then you need to keep multiple copies of it, on different media, stored in different places.

Backups, backups, backups.

The ironic thing was that the failed drive was being used as the backup while I set up a new OS on the original drive.

---

