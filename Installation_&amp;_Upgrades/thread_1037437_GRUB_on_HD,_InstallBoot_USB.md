---
title: "GRUB on HD, Install/Boot USB?"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by Unparallelogram on 2009-01-11
In an attempt to use old hardware, I am trying to set up a server on a potentially faulty machine with a questionable disk. I have had the hard drive crash on me, and gotten bad sectors reported. As such, I cannot expect to store data on it. I also have an external USB hard drive which I assume is reliable. What is the largest amount of my system I can move off to this external drive? Ideally I would only leave GRUB on the machine's disk. How would I go about setting this up? Thanks.

EDIT: To clarify, my system is unable to boot directly from USB.

---

### Post by caljohnsmith on 2009-01-11
You could maybe install the [PLoP]("http://www.plop.at/en/bootmanager.html") boot manager to the questionable HDD, and then it sounds like it would be best to put your entire Ubuntu install on the USB drive since you can't trust the HDD. That way you are just using the HDD only to boot Ubuntu on the USB drive, so Ubuntu should be safe. Let me know how that goes if you decide to try it.

---

### Post by Unparallelogram on 2009-01-11
I just finished trying a mock install onto a smaller usb device I had lying around. The Ubuntu installer doesn't seem to give me any choice as to where it puts its bootloader, and wants to use the hard disk.

---

