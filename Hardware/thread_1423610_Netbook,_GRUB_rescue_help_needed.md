---
title: "Netbook, GRUB rescue help needed"
date: 2010-03-06
forum: Hardware
---

### Post by henners91 on 2010-03-06
Hi, my netbook (no optical drive) boots straight into grub rescue, leaving no time to load my live disk (on usb) in order to reinstall ubuntu, it allows me to put in grub rescue commands but i can't find the original grub file and i don't know how to tell it to boot using the live disk from grub rescue. 
 Any help is appreciated.

---

### Post by Arkitekt on 2010-03-06
Either set your BIOS to boot from USB before HDD or if you have the option of pressing say F1 for boot options when you start your pc then do that and select USB, this will load your live USB before GRUB

---

### Post by henners91 on 2010-03-06
No i can't do that, it doesn't seem to load the BIOS, it just loads straight to GRUB rescue even with the usb stick in it. is there a grub rescue command to tell it to boot from or run the usb live image?

---

### Post by henners91 on 2010-03-06
Solved by spamming esc, f1, f2, f11 and f12 to get to BIOS then setting hard drive priority to usb. Bit more luck than anything else. Windows 7 seems to have nailed my original ubuntu install.

---

