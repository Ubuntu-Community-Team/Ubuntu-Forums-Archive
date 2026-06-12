---
title: "old pc, not reading hard drive"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by lummoxcooties on 2006-04-07
I have an old computer that had Win95, but I think it got toasted. I receive the error on startup "Invalid system disk." This happens without a floppy in there, and I also changed the boot sequence from "A, C" to "C, A" and the same error message comes up. I assume the hard drive is not bootable or something, but I don't know how to fix that. I don't have windows 95 disks, but would rather put Ubuntu on there. What do I need to do in order to put Ubuntu on it? Can my computer even boot from the CD Drive?

---

### Post by K.Mandla on 2006-04-07
Hi! Can you tell us what kind of computer it is?

In my experience "invalid system disk" means the operating system (Windows 95 or Ubuntu or what have you) isn't accessible on the hard drive. That could be a damaged boot sector, or a damaged drive, or maybe even just a disconnected cable.

One of my favorite ways to check if the hard drive is accessible is to run Killdisk.

[www.killdisk.com](www.killdisk.com)

It's actually a utility to blank out a hard drive, which you might want to do, but it is also very trustworthy for polling drives and finding missing ones. And if you do find that it's connected and responding, you can blank it out for a new operating system ... if that's what you want.

Use that thing very carefully, especially if there's information on that drive that you want to keep. But if you just want to put Ubuntu on it, it's perfect.

---

### Post by lummoxcooties on 2006-04-07
I tried using the killdisk tool but when booting, it said "disk I/O error." And you are right, I just want to wipe the computer clean and put ubuntu on there.

The Computer says DSI 486-DX. I believe DSI is the brand/company, but I am not sure.

---

