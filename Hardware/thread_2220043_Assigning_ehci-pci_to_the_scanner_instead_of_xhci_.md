---
title: "Assigning ehci-pci to the scanner instead of xhci_hcd"
date: 2014-04-26
forum: Hardware
---

### Post by geral-k on 2014-04-26
I have recently installed Xubuntu 14.04 on two computers.  Computer A is a DELL Aptitude E5430 laptop, whereas Computer B is a  home-mounted desktop, with an ASUS H87-Plus motherboard. I have been  trying to make an EPSON Perfection V33 scanner work with both computers,  with mixed results.
  First of all, I downloaded the appropriate programs from the Epson site and installed all three of them on both computers.


  My DELL has 4 USB connectors: one at the right-hand side (USB2), one  at the back (USB2) and two at the left-hand side (one USB2 and one  USB3). If I plug the scanner into the connector at the right-hand side, I  can run Image Scan! and Simple Scan without any problem. However, if I  use either one of the other two USB2 connectors, the problems start: the  sane-find-scanner utility finds and identifies the scanner; and scanimage -L  works OK as well; but when I try to run Image Scan! the scanner  produces the customary humming noises, the ON lamp blinks for a few  seconds, but the Image Scan! screen never appears, and after a while the  program disconnects and sends the following message:
  Could not send command to scanner. Check the scanner's status.
  If I run Simple Scan, the initial screen appears, but I cannot make it scan anything.


  It turns out that when I plug the scanner into connector 1, the Linux kernel assigns ehci-pci to it; when I use connectors 2 or 3 it assigns xhci_hcd.  I have no idea why this happens. Anyway, I think it explains why  scanning cannot occur when connectors 2 or 3 are used, because the Epson  drivers for this scanner are known to be incompatible with USB3.


  To confirm this, I then plugged the scanner into one of the USB2  connectors of computer B (the ASUS desktop). As with my laptop, sane-find-scanner and scanimage -L showed no problem. But, sure enough, xhci_hcd was assigned to the scanner, and scanning failed, despite the humming and blinking.  I then disabled USB3 via BIOS; this time ehci-pci was assigned to the scanner, and scanning proceeded normally.


  I want to keep the scanner plugged to the ASUS desktop in my office,  but disabling USB3 on this computer every time I need to scan is  obviously inconvenient. So here is my question: could I make the kernel  assign ehci-pci to the scanner instead of xhci_hcd (maybe through a udev rule)? So far I have been unable to find a clear answer or a good solution, so any help will be appreciated.

  Many thanks in advance.

---

### Post by pdc on 2014-04-28
I think this is a nice guide [http://hintshop.ludvig.co.nz/show/persistent-names-usb-serial-devices/](http://hintshop.ludvig.co.nz/show/persistent-names-usb-serial-devices/)

and for more general background on udev; here is a primer [http://wirespeed.xs4all.nl/mediawiki/index.php/Figuring_out_udev_rules](http://wirespeed.xs4all.nl/mediawiki/index.php/Figuring_out_udev_rules)

do let us know how it goes;

---

### Post by geral-k on 2014-04-28
@pdc: Thank you for your pointers. It seems that the first reference is unreachable now, but I'll try later on. I did download the second reference and will study it, along with other udev materials I've been collecting. Will keep you all informed on my progress (or on the lack of it).

---

### Post by geral-k on 2014-04-29
At last I managed to download the first reference cited by pdc. Unfortunately, I can't see how it could help me; it deals with a popular topic, that is, giving USB plug-in devices a permanent name. My problem is trying to understand how and why the Linux kernel attaches xhci_hcd to certain USB connectors and ehci-pci to another connector in my laptop, even though they are all USB2. If I can understand this, then maybe I'll be able to figure out how to control this behavior. I am having a hard time trying to understand some udev tutorials I have downloaded; isn't there something more detailed and didactic? Furthermore, I am not sure the solution really lies in some udev rule.

Out of curiosity, yesterday I ran xsane on my desktop. To my surprise, it worked perfectly. Then I closed xsane, turned the scanner off and back on and restarted xsane. This time, the scanner hummed, the ON lamp blinked, but no scanning occurred. I now remember that this erratic behavior has happened once or twice before, with Image Scan! and Simple Scan. Disabling USB3 via BIOS worked as before.

---

### Post by geral-k on 2014-05-02
No progress. I'm not sure whether this is bug in the xhci_hcd module (which, by the way, is built in the kernel) or in the Epson driver. I thought of creating a udev rule that would temporarily unload xhci_hcd when the scanner is turned on and load it back on when the scanner is turned off, but this would require a recompilation of the kernel source, in order to make the USB modules loadable and unloadable. This does not seem to be worth the hassle. Furthermore, since my desktop already has Win XP running on Virtual Box, it would be easy to install the Epson drivers for Windows.

---

### Post by geral-k on 2014-05-02
As expected, the Windows drivers and programs for this scanner are fully functional when I use WinXP running on Virtual Box.

---

### Post by geral-k on 2014-05-04
Vuescan 6494 (trial version for Linux) also works with my Epson v33 scanner. It seems to be entirely compatible with xhci_hcd.

---

