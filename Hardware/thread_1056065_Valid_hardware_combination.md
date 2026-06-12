---
title: "Valid hardware combination?"
date: 2009-01-31
forum: Hardware
---

### Post by garbetjie on 2009-01-31
Hey all.

I have a small question to ask. I have searched on Google for a while now, and I haven't been able to find a forum post or news article that satisfies my question.

To start with, here is a basic hardware outline that I have:
Dell Optiplex GX150 (PIII 950MHz I think with IDE connectors)
Intel 815 chipset
128MB RAM
500GB SATA HDD

I've read about there being some issues with limits being imposed on HDD capacity available to the operating system. Currently, I'm having issues with the motherboard being able to detect the HDD.

My question is this:
Is there any possibility that there could be a limitation placed on the drive size by the motherboard. Could this limitation also have something to do with the HDD not being picked up by the motherboard? And finally, I'm pretty sure that this sort of setup *should* be possible whilst running Ubuntu Server 8.04. Can anyone dispute this?

I'd really appreciate the help, and I'm sorry if this post seems a bit scattered. Let's just say my concentration span has diminished :D

---

### Post by nixscripter on 2009-01-31
The only thing I could see is that the HDD wants to use a faster ATA speed than the motherboard supports. I don't know about SATA speeds (I've had trouble with such drives myself), but that is probably the source of the problem. If you can boot the computer off a CD, you can tell what the speed of the SATA bus is by looking through **/var/log/messages**.

---

### Post by garbetjie on 2009-02-01
Thanks for the suggestions Nixscripter. It seems like it could actually be the motherboard that's giving me issues. I even replaced the shiny new HDD with the original 10GB IDE HDD, and it still doesn't recognise it.

Big, big sadface, but I'm going to try some more things to make sure that it isn't the converter :)

---

### Post by CREEPING DEATH on 2009-02-01
Many older mobos won't recognize >138 GB drives.  You can purchase a controller card that will allow the lagre SATA drive for not much money though.

CD

---

### Post by garbetjie on 2009-02-03
I would think that a PIII mobo would be able to pick up drives that size though. Not that I know at the moment. It doesn't even pick up the original 10GB drive that the PC came with. I might have been sold a dud :(

---

### Post by nixscripter on 2009-02-03
I suppose you could always netboot.... ;-)

Like Creeping Death said, try an expansion card. I would assume that BIOS is new enough to allow booting the primary HD from one.

---

### Post by garbetjie on 2009-02-07
See, the annoying thing is that it doesn't seem to be an issue with the motherboard incorrectly detecting the size of the drive.

It actually doesn't pick it up at all. Keeps giving a "disk not found" error. Not even the CDROM installer picks it up. I stuck the drive in another PC, using the same disk and SATA -> IDE converter, and everything was picked up just fine.

I even placed the original harddrive (10GB) that came with the PIII back in the original machine, and it didn't pick that up either. So, to me, it sounds like that the actual motherboard itself is bust. It doesn't seem to pick up any harddrive at all, no matter the size.

*sigh*. Was really looking forward to this...

---

