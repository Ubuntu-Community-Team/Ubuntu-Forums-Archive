---
title: "drive recovery using ubuntu (need to save brother's work computer)"
date: 2008-09-17
forum: General Help
---

### Post by sou_agua on 2008-09-17
Hello All,

I'm very new to the community and just got Ubuntu Studio (8.04) working on my home-built machine.  I'm insanely happy with it and am hoping to delve into the programming world soon.

I am running a dual-boot with XP64 for gaming, but am trying to transition to Ubuntu for everything else.

Here is my current situation:

My brother's work computer went down.  Rather, his computer's hard-drive stopped working.  I placed the non-working drive into an external hard drive case and connected it via usb.  XP64 noticed that an external drive was added, but the drive did not show up under 'my computer'.

So, I  went into Ubuntu and I was able to access the drive.  I know I can pull the files off of the drive now, which is nice, but I would like to be able to repair the disk of any errors.  Would running Wine with say o+o defrag possible fix the problem?  Or any other suggestions?

I searched sourceforge for a program, but didn't turn up anything yet.

Thank you for your help.

~Agua

---

### Post by iaculallad on 2008-09-17
Try to use the [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") Utility.

---

### Post by mb_webguy on 2008-09-17
First thing, back up the hard drive while you can read from it.

Second, this sounds to me like it might be a power supply problem, in which case you can't really do much with it.  It may continue to work if it's slaved to another drive or (as you discovered) as an external USB drive (though I'm surprised that works in one OS and not another), but its days as a primary drive may be over...

After you've backed up the drive (possibly by cloning it with something like Partimage), scan for problems with fsck.  If it checks out, stick it back into the original computer and (if it's detected by the BIOS) try to install Ubuntu to it.  If you can, and can then boot from the drive, then... well, I don't think that's going to work, but if it *does*, then you should be able to restore the original data to the drive (which should be easy enough if you image it) and go about your business.

---

### Post by sou_agua on 2008-09-17
Thank you very much.

I just got done running the program, and it didn't seem to detect any errors.  I'll see if my brother just needs the pictures off of the drive (he's an auto-body guy).  If he needs more, then I will bug you all some more.

Be well.

---

### Post by sou_agua on 2008-09-17
@webguy

When you say power supply issues, do you mean on the hard drive itself, from the motherboard, or from the PSU?  I'm not sure I follow why that would result in this symptom.

I will back up the drive ASAP and try your solution next time I am out at their shop.

---

### Post by mb_webguy on 2008-09-17
It sounds like a problem I've had before, and it was that the power controller on the drive itself was bad.  It wouldn't do anything as a primary drive, though it would sometimes be detected.  I figured out that if I slaved it to another drive it would work fine (because, if I'm not mistaken, the master drive controls power to the other drives on the cable).

---

### Post by sou_agua on 2008-09-17
Okay, I understand now.  Thanks for the clarification. :)

---

