---
title: "Can Ibex upgrade affect the mobo BIOS?"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by kernelsanders on 2009-01-02
I recently just tried to upgrade from Heron to Ibex and everything seemed to go smoothly. Once the installation process was done it came time to reboot. I clicked OK, thinking in just a few minutes I'll be salivating over my new Ibex install, and how many chicks I'm gonna get for using it...but I digress.

Anyway, after clicking OK the monitor went blank like a normal shutdown but the PC never booted back up. I waited 20 minutes or so just to be safe, but no boot. There is no GRUB menu, and get this, not even an BOIS menu appears?! I've disconnected all peripheral devices (except the wifi card), and the CD drive. 

It seems highly coincidental that something would fail at the exact moment the system was rebooting. Can any experts out there fill in the blanks on why the system isn't booting?

Hardware:
Intel D945GCCR Mobo
Western Digital 80GB HDD
Intel Core 2 Duo processor

---

### Post by jbrown96 on 2009-01-02
Most machines also beep when they POST (power-on self-test). Is your machine beeping, any lights (especially the network card), or can you make it make any reply by pressing lots of random keys?

It would have to be something really, really crazy for Ubuntu to fry the BIOS.

You might also try reseting it, but it will involve opening the case. Look for the small battery (it's about the size of a quarter) on the motherboard, gently remove it, and replace after about 30 seconds.

---

### Post by kernelsanders on 2009-01-03
I tried hitting keys but there weren't any beeps. Removing the BIOS battery didn't help either. 

I removed the RAM to see if the system would at least indicate that the POST did not detect any RAM, however, it did not even beep for that. 

When power is connected there is a power LED indicator on the board that lights up, also the CPU fan whirs and lights up. There are two leds on the wifi card, "ACT" and "PWR". The power led does not light but the ACT light will slowly blink.

Any ideas?

---

### Post by kernelsanders on 2009-01-05
Just an FYI in case anyone runs across this thread I would up being able to sidestep this problem by just replacing the motherboard...so I'm still not sure what happened to the original motherboard.

---

