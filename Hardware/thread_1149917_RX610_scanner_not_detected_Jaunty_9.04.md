---
title: "RX610 scanner not detected Jaunty 9.04"
date: 2009-05-05
forum: Hardware
---

### Post by charonred on 2009-05-05
SANE is not detecting the scanner in my brothers Epson RX610 printer/scanner/copier - No Device Found

The scanner just won't work, yet the printer does (as outlined in quote).

How do I get SANE to detect the scanner ?

> I setup my brothers rx610 and it wouldn't print in Intrepid.

When I tried the Jaunty live CD it printed, so I installed/upgraded to Jaunty (with printer connected and on).

Once upgrade was complete, I deleted previous rx610 printer, Jaunty then found a 'new printer' and presto it now prints in both Gnome and KDE, as well as XP in VirtualBox.

read last post
[http://ubuntuforums.org/showpost.php?p=7862621&postcount=5]("http://ubuntuforums.org/showpost.php?p=7862621&postcount=5")

---

### Post by freonchill on 2009-05-05
the following are supported by sane
RX-600 USB
RX-700 USB

nothing is said about the 618
[http://www.sane-project.org/man/sane-epson2.5.html](http://www.sane-project.org/man/sane-epson2.5.html)

---

### Post by charonred on 2009-05-05
thanks freonchill,

I just went there myself; RX600 refers to the whole series I think, so RX610 should work with sane-epson2.

I'll revisit the page when I'm over my brothers next - for the moment he's happy that the printer is now working. I've only just switched him & his PC over to Ubuntu from Windoze XP 2 weeks ago; him and his wife love it already, but the printer/scanner threw a spanner in the works, so once that is fixed they'll be very happy refugees :)

---

### Post by CorosiveFrog on 2009-05-05
I'm having the same problem, my all-in-one is an epson stylus CX4450. The printer works, but the scanner isn't detected.

It's kind of a bummer because I am a cartoonist and I have to scan my comic strips to put them online.

---

### Post by charonred on 2009-08-28
fixed it; after reading lots of posts and trying some other packages that wouldn't install for various reasons, I thought I'd look in Synaptic Package Manager.

Searched for Sane, then marked 'libsane-extras' for installation and applied it.

libsane-extras package includes some backends that are not yet included into the official SANE distribution. Currently, they are :
  * epkowa (some EPSON scanners)
  * geniusvp2 (Genius ColorPage-Vivid Pro II)
  * hp_rts88xx (HP ScanJet 4400C, HP ScanJet 4470C)
  * hp3900 (HP ScanJet 3970C, HP ScanJet 4070, HP ScanJet 4370)
  * ls5000 (Nikon LS-5000 ED, Coolscan 5000 ED) 

'epkowa' detects the RX610 scanner and lists it as a RX5 flatbed scanner, choose this as it works fine; brother and wife are happily scanning photos and docs now.

---

