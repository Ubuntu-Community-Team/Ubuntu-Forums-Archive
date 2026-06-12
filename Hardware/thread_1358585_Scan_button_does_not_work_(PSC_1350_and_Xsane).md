---
title: "Scan button does not work (PSC 1350 and Xsane)"
date: 2009-12-18
forum: Hardware
---

### Post by Fitch on 2009-12-18
Xsane always comes up "scanning devices" when I call it up from Applications > Graphics.
It then finds the HP PSC 1350 scanner (so far so good) and the PCTV Rave video card (not so good).

When I press the scan button on the printer/scanner, nothing happens.  I believe it to be because Xsane finds both devices and doesn't know what to do next.

How can I test this theory and not have the video card seen by Xsane?

And yes, I have checked the HP settings and "xsane -V %SANE_URI%" is in the right place.

I do about 60 or 70 receipts in at a time, so it would be advantageous.

Thank you in advance....

And if nobody answers before next week, Merry Christmas anyway.

P.S.  Have I put this thread in the right Forum?

---

### Post by ellgor on 2009-12-23
Hi,

Try Imagescan from Avasys, worked first time for me after trying to get Xsane to recognise the scanner, all the details are on their site, for each and every scanner.

And a merry Christmas to you.

Regards, Ellgor.

---

### Post by Fitch on 2009-12-23
It's a shame to go that far, i.e. uninstalling Xsane and installing Scanimage (which seems to be only for Epson printers), when I just think there's a tweak in there somewhere...

On second thoughts,
I tried this on the command line:
scanimage -d hpaio:/usb/psc_1300_series?serial=HU46NDP2J79F --format=tiff > hello.tiff
and it worked.

I put the same line into the HPLIP device manager, pressed the scan button, and it didn't.

I can't use Xsane for this experiment as all I get is several lines of:
(xsane:3995): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

---

