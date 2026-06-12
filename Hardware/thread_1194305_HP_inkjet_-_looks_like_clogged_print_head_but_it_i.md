---
title: "HP inkjet - looks like clogged print head but it isn't"
date: 2009-06-22
forum: Hardware
---

### Post by RobertL on 2009-06-22
My HP 932c is directly connected to a USB port on my Ubuntu machine and also samba-shared with Windows machines on my home network. The printer worked fine from either platform for a few months. But now when I print from Ubuntu the text has missing horizontal lines of ink. IOW each line of text has some dark dots, some grey dots, and some missing dots in each letter and they are the same vertical position in every letter so they form horizontal dark/light bands of ink across the page. The same misprinting occurs from Open Office and Firefox.

If I print the same file on the same printer from one of the Windows machines it looks normal. Therefore I'm inclined to think the printer driver is ok (is that valid?). I've tried twiddling all the options and properties I can find, both in the printer driver and the print option in the apps, but nothing seems to affect this appearance. At first i thought the printer was out of ink or the print head was clogged, but (as I said above) the problem doesn't show up when I printer from Windows.

I'm not sure when it started, but possibly it was when I upgraded to jaunty, which caused me to have to reinstall the printer driver.

---

### Post by T.J. on 2009-06-22
Sounds like a bad printer setup.  I'd remove the printer, reinstall it, and then print a test page. You might be using a generic printer driver that doesn't take into account the differences in your printer.  

Jaunty is kind of bleeding edge.  Regular Ubuntu releases are 6 month snapshots, so there are always a few glitches.  If you prefer stability, I'd suggest using an Ubuntu LTS release or something like Debian.

---

