---
title: "nVidia 6200 PCI, Ubuntu freezes on boot"
date: 2009-03-26
forum: Hardware
---

### Post by BobtheBlueBerry on 2009-03-26
Hi.

I bought a EVGA e-GeForce 6200 PCI Graphics Card and I'm not having very good luck with it.

I got it to work fine in Windows XP, but when I boot Ubuntu (8.10), then the progress bar starts to load but then stops at about 1/9 of the way and the system locks up. I tried installing nVidia drivers, but nothing changed.

I tried booting from an 8.10 Live CD and the same thing happened.

Can anyone help me? I'm running a HP Pavilion a1106n and it comes with Intel onboard graphics.

Thanks,
Bob

---

### Post by BobtheBlueBerry on 2009-03-28
Anyone?

It doesn't freeze when I set my primary video adapter to Onboard (rather than PCI), but Xorg doesn't work ("no screens found").
I couldn't find anything useful in my logs.

---

### Post by ifyc576 on 2009-03-28
I have the same video card and I have had no problems with Ubuntu.  Not yet anyway. I don't believe it is your card especially since it was running fine on windows.

---

### Post by BobtheBlueBerry on 2009-03-28
Ubuntu 8.04 LiveCD freezes, too. I seem to be getting Segmentation faults, too.
Probably my crappy BIOS that doesn't let me completely disable onboard graphics.

The onboard graphics won't even work unless I physically remove my graphics card from my machine so I can't access good graphical configuration tools and text mode is really iffy.

Any ideas? I've been trying for like 6 hours.


EDIT:
I tried my graphics card in an old junky machine running Debian (lenny) and it booted fine. (Xorg didn't work because I have it configured to work with a Voodoo3 and there's no nVidia drivers installed.)

Could it perhaps be the Intel onboard graphics?

---

### Post by BobtheBlueBerry on 2009-03-28
By blacklisting the intel_agp module I fixed Ubuntu freezing at boot and I had to uninstall some nVidia debs because I was using the installer from nVidia's website.

Works great now I'm happy my 8 hours of fiddling didn't go to waste.

In case you're getting this too, here's how to blacklist the intel_agp module:

**1.**
$ sudo vim /etc/modprobe.d/blacklist

**2.**
Navigate to the bottom of the file with your arrow keys or using the Page Down key.

**3.**
Press the 'i' and add another line to the end of the file.
Then add "blacklist intel_agp" and then another blank line (it's always good to add a blank line to the end of a file).

**4.**
Press the Esc key, then type the following, including the colon ":wq".

**5.**
Reboot your computer.

---

