---
title: "USB failed to enumerate. ALL distros? Please help!!!"
date: 2010-04-06
forum: Hardware
---

### Post by trixx on 2010-04-06
Hi,I'll try to give as much detail as possible here. I recently tried installing Linux to use to recover some files lost on a crashed Windows drive, but to no avail. At first, my installers always froze for some reason, remedied by Safe Graphics Mode. I also kept getting errors, once past that, that I/O APIC was doing something wrong, so I had to add  "noapic" to the command line to boot the installers. This made it successful, and so I installed Ubuntu. 

Done, I figured, great. The LiveCD worked fine, and so I booted into the freshly installed Ubuntu, only to find that my keyboard and mouse weren't responding and so I couldn't log in or do anything. Not only that, but they weren't even receiving power (the laser on the wired mouse, and the lights on the usb receiver for the keyboard weren't even lighting up, they flicker when you unplug and replug them back in, but only for a fraction of a second.

Now, I tried booting into recovery console or whatever it was called, and repeatedly get the error: usb failed to enumerate, for the ports my keyboard and mouse are plugged in. It seems as though as soon as the Linux kernel is loaded from my hard drive, my usb mouse/keyboard die.

Now, for the weird part: I installed Kubuntu and Ubuntu two to three times each, trying different things, and neither worked. So I downloaded the OpenSuSE net install cd, and that worked but was taking far too long, so I downloaded the full 4.2 GB dvd. Boot that up, and what do you know, the EXACT same thing happens with the keyboard and mouse only I can't see the error messages. And that's after I get past the 'what would you like to do: boot from hard disk, install, repair...' menu, because the keyboard works there.


PLEASE help, I don't understand why I'm getting this problem or why it's in both SuSE AND *buntu's.


EDIT: I just tried booting SuSE dvd with 'brokenmodules=ehci_hcd" and the mouse (plugged in front USB port) came back on after the loading screen made it to the actual installer, and it worked, but then I unplugged it and replugged it in and it stopped working again... tried with uhci_hcd instead, no dice.

EDIT EDIT: I plugged the wireless receiver for the keyboard into the front USB port, got the wireless mouse that goes with it, and booted SuSE with nolapic and brokenmodules=ehci_hcd and they both work, but the usb mouse in the other port that isn't the front one does not work.

Keep in mind, I'm using the OpenSuSE dvd because it's easier to boot that than to install Ubuntu or Kubuntu, then boot it and try to find out, seeing as how the problem is the same. Preferred end result for this is that I end with Kubuntu installed.

---

### Post by trixx on 2010-04-06
Alright this is just too weird... Now, going through the SuSE installer (if it works with these settings, will install Kubuntu to other partition and if successful, will overwrite SuSE with Win7) the USB mouse that wasn't recognized before, is all of a sudden recognized and working o.o wtf-mait?!

---

