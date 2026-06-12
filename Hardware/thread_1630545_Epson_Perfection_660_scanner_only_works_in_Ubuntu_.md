---
title: "Epson Perfection 660 scanner only works in Ubuntu after having run Windows XP first"
date: 2010-11-25
forum: Hardware
---

### Post by GH68 on 2010-11-25
I'm running Ubuntu 10.10 and now have a problem with my Epson Perfection 660 scanner which used to work previously, although I cannot say in which Ubuntu version since I don't use it very often. Anyway, it must have been 8.04 or later. If I run Windows XP and restart the computer without turning off the scanner inbetween, it works perfectly in Ubuntu. If the scanner has been turned off and I run Ubuntu after having turned it on, no device is found by xsane. I can see the scanner when typing lsusb but sane-find-scanner does not show it (instead it shows some device that I have not been able to identify - I could supply this info if requested although I'm presently not at my computer). I have a firmware file, TAIL_061.bin, available with read access for all users in /usr/share/sane/snapscan, actually this file has survived my upgrades so it most likely is ok. The /etc/sane.d/snapscan.conf also points at that file, i.e. including the following line:
firmware /usr/share/sane/snapscan/TAIL_061.bin

I'm happy for any advice on how to resolve the issue or continue my troubleshooting.

Thanks!

---

### Post by GH68 on 2010-11-28
Problem solved. It turned out to be hardware related. When connecting the scanner after startup of Ubuntu I found the following through dmesg:
[  130.976133] usb 1-2.1: new full speed USB device using ehci_hcd and address 8
[  136.070810] usb 1-2.1: can't set config #1, error -32
[  136.079832] WARNING! power/level is deprecated; use power/control instead

The power level warning made me realise that I recently connected the scanner to a (powered) USB hub and by connecting it back to the computer's own USB connector everything works. The printer, that I now had to connect to the USB hub works as well as a USB web cam. It was a little strange that the scanner (nearly, it turned out during my trouble shooting,) always works in Windows though, and it seems strange to me that first running Windows to load the firmware also made the scanner almost (only almost, it turned out after more thorough analysis) always work in Ubuntu. Well, maybe my statistics on this is not sufficient. When the scanner was found, it has no problems with the data connection.

Sorry if my initial thread mislead someone, but maybe this thread could be helpful for trouble shooting for someone even if the Windows XP part now seems slightly unrelated, although in fact it reveals an interesting aspect where the actual performance of the hardware may work differently in Windows and Ubuntu. I almost ruled out hardware performance to start with since it behaved well in Windows XP.

---

### Post by GH68 on 2010-11-28
:d

---

