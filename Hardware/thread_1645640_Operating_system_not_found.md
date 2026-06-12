---
title: "Operating system not found"
date: 2010-12-14
forum: Hardware
---

### Post by racie on 2010-12-14
(I posted this previously in the general forum on accident)

So I was casually using Ubuntu with Google Chrome and Transmission open. I closed my laptop lid and walked away for maybe twenty minutes. I came back and my laptop appeared to be in sleep mode even though I have it set NOT to sleep. The LED light by the caps lock button was blinking and it was stuck so I had to shut it off via the power button. When I tried to turn my laptop back on, the laptop hung at the Compaq BIOS screen for longer than usual before it came to "Operating system not found." I tried re-starting the laptop again and received the same error. I waited ten minutes (as this happened twice before), but still, the same result.

Right now I am using a USB to boot into SliTaz. I cannot view any of the files on my hard disk.

Did my hard disk just commit suicide? Is there any hope of restoring it?

This has happened a few times before, but after re-starting it usually worked.

I don't have a CD drive either because it was broken and causing my boot to be very slow (like the speed it is now while it is searching for an operating system).

Thanks.

---

### Post by mr clark25 on 2010-12-14
sounds like it is probably just a grub issue, but the partition table may have been corrupted.

try using the grub-fixing script in my signature.

I'm not familiar with SliTaz, but if it is another linux distro, it should be able to run that script just fine.

---

### Post by racie on 2010-12-15
Hmm... I can't really do it properly in SliTaz, so I'll have to find a USB large enough to boot Ubuntu.  But I'll try it and post back when I can! Thanks.

---

### Post by racie on 2010-12-17
Okay so I was able to get a USB big enough to fit a LiveUSB of Ubuntu on it, but for some reason I am getting errors when I try to boot from it.  Is there some sort of md5 I can check my .iso file with?

Also, my hard disk doesn't show up in the BIOS any more.  Should I just give it a rest then?  :/

Meh... good thing I just picked up a desktop for $30.  :)

---

### Post by racie on 2010-12-20
Here's an update:

My brother and I took it out of my laptop and connected it as a secondary drive to a desktop.  I could access all of my files and backed them up onto an external hard drive.  We then wiped it and we were going to put it back in the laptop to test it when we realized we had misplaced the adapter for it.  :/  As of now it is chilling in my desktop computer.

---

