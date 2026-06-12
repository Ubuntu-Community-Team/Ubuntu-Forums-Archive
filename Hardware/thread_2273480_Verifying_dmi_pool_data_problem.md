---
title: "Verifying dmi pool data problem"
date: 2015-04-13
forum: Hardware
---

### Post by Grooby_AL on 2015-04-13
Hi everybody this is my first time using ubuntu and trying to install it we'll i will write my story here

Bought an new pc and tried to install ubuntu server with USB, i've entried BIOS and made it to start from usb everything were good but i accidentally select to install on usb i had to wait around 30 minutes and at 95% got an error after it tried to reboot and install from first but verifiying dmi pool data stuck here and cant install anything or boot 

Ps i had debian server installed and i forgot his pass now i cant install anything please help me

Sorry for my bad english

---

### Post by Mike_Walsh on 2015-04-13
Hallo there.

'Verifying DMI pool data...'; hmm, THAT sounds familiar. I've just done a CPU upgrade, and needed to upgrade the BIOS in order to accommodate it. Everything went well, up to a point. The machine started, with a new POST screen, courtesy of the upgraded BIOS. However, I, too, got to a screen full of PCI data, with, at the bottom,'Verifying DMI pool data...'

The fix that I ended up carrying out involved clearing all the CMOS data, by means of the 'Clear CMOS data' jumpers on my motherboard; in essence, re-setting everything back to defaults. As I understand it, this allows the machine to re-initialise itself, with the available information from a 'clean start' on the hardware that is present at power-up. By so doing, I was able to regain access to GRUB (Grub4DOS in my case, or 'legacy Grub', if you like..... I run 'Puppy', and Grub2 refuses to recognise it; at least, not without major editing of the grub.conf file!)

Do you happen to know what motherboard your machine is using? IF it's a laptop, I don't know if it's even possible to do this; however. I know it can be accomplished on most desktop PC's relatively easily.

If you can do this, then you should be able to go into your BIOS, make sure that the boot priority is set to allow booting from CD/DVD, and then boot from a LiveCD .iso. You should then be able to either find out what's happened to your server install, or if you so wish, to re-install again on the partition of your choice. You may need to install GParted to accomplish this.


Regards,

Mike. :)

---

