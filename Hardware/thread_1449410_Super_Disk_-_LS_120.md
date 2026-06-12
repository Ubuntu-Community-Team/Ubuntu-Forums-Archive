---
title: "Super Disk - LS 120"
date: 2010-04-07
forum: Hardware
---

### Post by chipchop on 2010-04-07
I have tons of super disks (120MB) that I need to transfer the data from to a more space efficient tool, usb hard drive. Has anyone had an experience with a usb super disk floppy drive or even a traditional ide super disk drive?  I see that most of them are made for mac.  Right now it is a slow and tedious process with the ide super disk drive I installed on a newish computer with karmic32, and several files are returning errors.

---

### Post by srs5694 on 2010-04-07
I've never used LS-120 disks, but I have used both Zip disks and magneto-optical (MO) disks. Zip disks are similar technology to LS-120 disks; MO disks are a bit different technologically but they're similar in use. It sounds like you've got your system configured correctly but you're running into speed and reliability issues. Concerning speed, LS-120 and similar devices were not renowned for their speed even when they were current technology (ten or fifteen years ago), so unless you can quantify the speed issues and suggest why it's substandard in Linux (say, better performance in Windows or drive specs suggest you should get something better), I'm inclined to chalk that up to limitations of the hardware design.

Concerning reliability, it seems unlikely that Linux is to blame for that. Chances are the media are simply old enough that they've started to develop errors. That said, you might try ddrescue if a simple cp doesn't work: "ddrescue /path/to/origfile /another/path/to/destfile". Type "man ddrescue" for more options. If you get a "command not found" error when you try to run it, type "sudo apt-get install gddrescue". The ddrescue command isn't guaranteed to create a perfect copy, but it may rescue enough of a file to be useful. OTOH, many file types are very sensitive to damage, so if there's a bad byte early in the file, the whole file may end up being useless.

It's also conceivable that a different drive would have better luck with your specific disks. If your files are important enough, maybe it would be worth picking up another drive. I bet they go pretty cheaply on eBay.

---

### Post by chipchop on 2010-04-08
It not substandard in Lunix specifically, it's merely substandard.  I was hunting on ebay a bit, the imation M3 should work, i'll let the forum know if it does or does not work.

---

