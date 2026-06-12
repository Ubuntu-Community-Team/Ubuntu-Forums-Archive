---
title: "Drive configuration - Masters &amp; Slaves. 4 drives."
date: 2009-05-25
forum: Hardware
---

### Post by desm on 2009-05-25
I have two IDE channels, two hard disks, a cdrom drive and a dvdrom drive.
The two hard disks occupy a channel, one master and the other slave. They work fine.
But when I put the cdrom and dvdrom drives on the other channel, with one master and one slave, the BIOS cannot detect them. I've also tried having them both master, or having them both slave. Or using each one individually as a master, or each one individually as a slave. The BIOS just can't see them!
The drives both work if I plug them in as slaves on the channel with my master HDD.

Ideas as to how I may get the bios to recognise them? It's set to Auto detect the secondary master and the secondary slave.

---

### Post by logos34 on 2009-05-25
you're forgetting one thing: to set the **jumper** on the back of each drive (Master, Slave, Cable-Select).  Sometimes only CS will work (in which case remember to set all the drives the same).

---

### Post by desm on 2009-05-26
I hadn't forgot to set the jumper. The problem is that the BIOS simply cannot detect the secondary master and slave (dvd and cd drive). It does not know they're there.

I just set all four drives to cable select. The computer could detect the hard drives, as before, but not the cd and dvd drive.

I'm very confused about what there is left to do.

---

### Post by logos34 on 2009-05-26
hmm, thought for sure it was the jumpers cause you didn't mention it...strange it's not seeing the secondary ide channel...Could this be a faulty cable? Broken/missing pin?  Have you tried manually specifying the detect settings on the secondary?

Personally, I have this weird niggle on my board where it refuses to boot up with a certain sata hdd attached...the machine won't even power on, which has really mystified me. It's not a power overload issue because it boots fine with second ide hdd connected...But if I remove the main ide hdd then it will power up and boot the sata (???)

---

### Post by dandnsmith on 2009-05-26
> **desm said:**
> I hadn't forgot to set the jumper. The problem is that the BIOS simply cannot detect the secondary master and slave (dvd and cd drive). It does not know they're there.

I just set all four drives to cable select. The computer could detect the hard drives, as before, but not the cd and dvd drive.

Since you've established that the drives can be detected on the primary IDE, you need to isolate the secondary IDE problem - try with just one drive (try CD/DVD and HDD), and try with a different cable.
I don't imagine that the cable has the wrong end plugged to the motherboard (I did that once, and spent a long time working out how the drive could be recognised but not work).

---

### Post by desm on 2009-05-26
It was the cable!
Which I cannot believe. It worked so recently as well, and I'm not entirely sure why it would just stop working. But I managed to find another one.
I also managed to kill my PSU. But I found another one of those as well.

Thanks for your help!

And yes, your problem does sound very peculiar.

---

### Post by logos34 on 2009-05-26
> **desm said:**
> It was the cable!

I also managed to kill my PSU. But I found another one of those as well.


ouch.  anyways, good luck

---

