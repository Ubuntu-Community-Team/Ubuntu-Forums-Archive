---
title: "Adding Filetypes to CUPS"
date: 2011-11-22
forum: Hardware
---

### Post by aciddesir on 2011-11-22
After a decent amount of researching, I finally got my HP Deskjet 3050A J611 printer working on 11.10.  However, when looking through the device manager for it, I came across the list of file types it will print... which basically amounts to JPEG's, GIF's and PDF's.  I understand not printing .odt but really, no .doc files is absurd.  Is there a manual way I can add .doc and .odt files to CUPS printable files?

---

### Post by emilywind on 2011-11-22
Firstly, .doc is a Microsoft format, not a widely known open one so the surprise should not be that shocking. MS may have a near monopoly with its Office suite, but that does not mean everything should kneel to support it.

However, I am not sure of why you are having your issue as even that tidbit should not impact your ability to print .doc files. Furthermore, CUPS should be able to print anything a program throws at it. Are you not just printing via File -> Print in LibreOffice or w/e?

---

### Post by aciddesir on 2011-11-23
Considering .doc is the most commonly used file extension and that the driver doesn't include, that's the irritating part.  True, but if they want users to come over from other distro's, namely Windows and Mac, they need to include that because (a rough) estimate would be over 90% of businesses and enterprises use MS so considering I need to be able to print my files both on my printer at home, at the printers at school (that are exclusively MS unless it's the media labs then it's Mac OSX) and at work (again, exclusively MS) and likely many other's like me, need that MS integration.  It's a little silly from a marketing and advertising standpoint to leave out the biggest file type out there. Damn you MS for having such a monopoly.

Anyways, no, I tried.  It reroutes it through Ocelot's device manager, which won't recognize the driver's and for whatever reason, I can't stop it from doing that.  The only way I can print anything at all is to manually go through the HPLIP Toolbox app, where I encounter this 'Not having any usable extensions available' problem.  A minor pain in the **** to go the long way around, but it would be nice not to have to convert all my papers to pdf's to print them.

---

