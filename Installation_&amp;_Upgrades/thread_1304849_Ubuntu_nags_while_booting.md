---
title: "Ubuntu nags while booting"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Mereep on 2009-10-29
Hi there,

I've just downloades Ubuntu and tryed to install it at my 
external USB HDD I've bought for this reason.
I've done this because our university works with some linux programs
and to try things at home I need an own installation.
So far so good, I've installed Ubuntu at the external drive.
Restarted and after some waiting, there came the bootloader. I've chosen to
start Ubuntu. The boot logo came up. A short message about the chosen
display mode showed. And then... it got black, Ubuntu just did nothing anymore.
It stopped loading data from disk. After some time even the loading-cursor got frozen.


the second problem I have: If I unplug the USB Drive an start the System,
the boot loader tells me that there were no such drive and switches in some
rescue mode. my guess is that the bootloader installed there at the USB drive
and overwrote the boot entry of the internal
harddisk with somewhat like a pointer to the USB Drive
loader (only a guess I never worked with linux/ubuntu before)




What did I do wrong? What can I do to fix the problems

Please help :(


P.S.: I'm running an acer aspire 7720G if this helps.
If you need more data, just say.

---

### Post by Mereep on 2009-10-29
2 the :KS

---

### Post by RJARRRPCGP on 2009-10-29
Sounds like what happened to me a while ago, the Ubuntu installer decided to go ahead and overwrite the boot loader on the HDD and when I unplugged the USB drive and wanted to boot Windows Vista from the HDD, GRUB gave me error 22, IIRC. It would then act strange, could not boot that Windows Vista install without the USB drive plugged in, GRUB would error on me, IIRC, if I tried to boot Windows Vista without the USB drive plugged in!

The option to change the location of the boot loader, GRUB, is tucked away!

---

