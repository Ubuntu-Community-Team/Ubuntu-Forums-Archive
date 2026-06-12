---
title: "BIOS doesn't recognize 500 GB hard drive"
date: 2008-06-16
forum: Hardware
---

### Post by TheLastAlive on 2008-06-16
I am looking to format my 500GB hard drive, but the BIOS will not recognize it.

---

### Post by nikgare on 2008-06-16
Does Ubuntu recognise it, though?
I don't belive that Ubuntu uses the bios for seeing the hd, so this should not be too much of a problem.
You will probably need to use gparted to format it, but be very carefull that you don't format the wrong drive!

Nik

---

### Post by regala on 2008-06-16
> **nikgare said:**
> Does Ubuntu recognise it, though?

Well, if the BIOS can't, "Ubuntu" will not.

> I don't belive that Ubuntu uses the bios for seeing the hd, so this should not be too much of a problem.
Indeed, the Linux kernel (unrelated to "Ubuntu") does not use the BIOS to _access_ the disks. But, if the BIOS doesn't see a disk, it will not switch it on, and make it spin. And no OS will see it at all.

By the way, you should take care of see the difference between "Ubuntu" which the packager and Linux which is the real OS. :)

---

### Post by Odrodzona-Sarmacja on 2008-06-16
Checking jumper settings on hd would be my first step.
Then I would go about checking cables again if they are firmly attached in all of their endings.
Then manually setting option for hd in bios from AUTO to the one with bigest number of cylinders and such.
Then I would use gparted livecd to find it and format it.

Good luck!

---

### Post by DerHesse on 2008-06-17
Give a try to gparted. [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
You can download a bootable Live-CD image here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by jespdj on 2008-06-17
Odrodzona-Sarmacja gives some good troubleshooting tips: (1) check that you've connected all the cables to the drive properly (interface and power cable), (2) check if there are any jumpers on the drive and make sure they are set correctly.

If it still doesn't work, try updating your BIOS to the newest version (look on the website of your computer or motherboard manufacturer for a download and tool to flash the BIOS).

It could ofcourse also be a faulty drive. If you have another computer, you could try connecting it to the other computer. If that doesn't work, then the chance is bigger that the drive is faulty.

---

