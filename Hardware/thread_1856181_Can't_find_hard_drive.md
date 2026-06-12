---
title: "Can't find hard drive"
date: 2011-10-07
forum: Hardware
---

### Post by darthenstein on 2011-10-07
Hey everyone,

Home-built Intel Core2Duo 2.4 2gb ram, running 2 SATA hard drives (attached to the motherboard) and a DVD-RW drive (SATA, attached to the motherboard).  Ubuntu 11.04

Usually, I would mount my second hard drive by going into places, computer, and clicking on the hard drive.  Now, with no changes at all, I can't find it at all!  I have tried going to System Settings > Disk Utility and I can't find the drive in there!  My system hard drive and DVD drives are there but I can't even find the drive to boot.  Bummer.

Can anyone tell me what I need to do to recognize the drive?  All I have tried doing so far is shutting down the computer, restarting the computer, and opening the case to unplug and replug wires.

Thank you all very much!

---

### Post by papibe on 2011-10-07
Could you post the result of this command?
```
$ sudo fdisk -l
```
Regards.

---

### Post by darthenstein on 2011-10-07
/dev/sda1   *           1       30141   242103296   83  Linux
/dev/sda2           30141       30402     2093057    5  Extended
/dev/sda5           30141       30402     2093056   82  Linux swap / Solaris


I have tried swapping the SATA connections on the motherboard, with no luck (except my dvd drive disappears sometimes), I should also add the Hard Drive activity light on my computer's case (red led light) is continuously lit

---

### Post by papibe on 2011-10-07
Well, it looks like a hardware problem. Some ideas:

- Check your BIOS to see if you can see the hard drive there, or if something got mis configured.
- Change the another motherboard connector.
- Try another cable.

Just some thoughts,
Regards.

---

### Post by darthenstein on 2011-10-08
Yeah the drive was toast...did not expect it to happen so suddenly!

Fortunately I got another 500gb for $60 and I had most of my data backed up.

Thank you all very much for your help!

---

