---
title: "Dell xps m1330 eject button..."
date: 2009-01-23
forum: Hardware
---

### Post by joedeal on 2009-01-23
Hello, I followed the instructions to enable the eject button and it works BUT....is there a way to make it so the disc unmounts berfore it ejects? otherwise I have to manually unmount...which kind of defeats the purpose....TIA!!

BTW I am a new Windows Vista convert.....using Ubuntu 8.10

---

### Post by x C0MMAND0 x on 2009-01-23
I also experience this same issue and am wondering if there is a workaround...

---

### Post by sdennie on 2009-01-23
What method did you use to get it work?  The dev.cdrom.lock=0 method?  If so, there is no workaround for that.  You are letting the hardware directly control the drive and the kernel has no idea anything has been done.  I just checked on my XPS m1330 (using xev) and the eject button doesn't generate an event on linux.  I don't think it's possible to get it to work "correctly".

---

### Post by nwadams on 2009-03-08
well there is the software unmount/eject function right? Mine will eject properly wiht the button if the disk is unmounted. So we should be able to write a script or something to map the eject key to unmount and eject. I'm not 100% sure how that would be done but I will look into it.

---

### Post by sdennie on 2009-03-09
Yes, there is software to eject the disk.  The problem is that the eject button on these machines is 100% hardware and doesn't generate any software events.  Without some sort of kernel support or BIOS change, it's literally impossible to make the eject button work properly.  All CD drives have the ability to "lock".  Windows doesn't use it because, well, it's Windows.  Linux does because it makes the CD drive a transparent part of the filesystem.  The reason the eject button works when the CD is unmounted is precisely for that reason: Linux has removed the lock and so the hardware key is able to eject the disk.

---

### Post by nwadams on 2009-03-09
hmm. And why doesn't the dev.cdrom.lock=0 fix not work? Is it possible to make an app that locks/unlocks the drive via software on command?

---

### Post by Karolis on 2009-09-23
Any progress on this? I personally don't use the DVD that much and when I do, I'm fine with unmounting it via context menu, but I'm a bit of a neat-freak and I want stuff to work on my machine.

---

### Post by nwadams on 2009-09-23
No. I don't think it can work. Because of the hardware limitations of our laptop where the eject button doesn't talk to the is. It only talks to the cd drive. Faildoze doesn't lock the cd drive so it works in windows but Linux locks the drive by default when it is spinning. So the only fix is to tell it to not lock the drive.

Sorry.

nwadams

---

