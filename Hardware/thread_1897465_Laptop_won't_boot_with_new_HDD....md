---
title: "Laptop won't boot with new HDD..."
date: 2011-12-19
forum: Hardware
---

### Post by Moozillaaa on 2011-12-19
It's an HP dv 9000, twin 120 Gig HDD's, #1, #2.

I bought a 2.5" USB enclosure, with a SeaGate 250 Gig inside. It works when attached to a USB port.

So I tried to swap the secondary drive with the SeaGate, and it is a struggle to get it even to BIOS SetUp, to see if BIOS does recognize the drive. It does.

It once STARTED to load GRUB, but stalled before the menu posted.

I HAVE swapped one of the Samsung 2.5's for a Hitachi 2.5.

Help?

---

### Post by Mark Phelps on 2011-12-19
sometimes, when you replace drives, the BIOS automatically switches booting order from one drive to the other.

Have you checked the BIOS to confirm that you're STILL trying to boot from the original drive?

---

### Post by Moozillaaa on 2011-12-19
Good thinking there Mr P...

I did not check for BIOS auto-reconfigure, but I did try the drive in the Primary bay, after doing a cp task 

cp /dev/original  dev/SeaGate

It worked, but strangely, some FF settings, including log-in info for some forums, did not load once the drive DID boot successfully.

Built-in security features???

---

