---
title: "HP LaserJet P1102w"
date: 2014-01-17
forum: Hardware
---

### Post by History Teacher on 2014-01-17
I'm trying to set up an HP LaserJet P1102w.  I've run the sudo hp-setup command and executed the python command.  It launched the GUI but then I get this:

[ATTACH=CONFIG]249557[/ATTACH]

It appears that the printer is not recognized.  The printer is connected via USB and is turned on.  Is there a way the printer can be recognized and set up?

Thanks!

---

### Post by tgalati4 on 2014-01-18
If this printer has a network jack, make sure it is unplugged.  Many HP printers can't support both USB and Ethernet.  Does the printer work under Windows or Mac?  Print the status page to make sure there are no internal errors.

---

### Post by History Teacher on 2014-01-18
Thanks for the helpful post.  It is running only in a USB connection I don't use the Ethernet function.  It was working fine with Windows.  How do I print the status page?

I'm also trying to figure out if this is a driver issue or not?

Thanks again.

---

### Post by unixpcguy on 2014-01-18
Hi,

I found a How To for you. I hope this helps.

[URL="http://ubuntuforums.org/showthread.php?t=184838"][COLOR=#ff9933]_[http://ubuntuforums.org/showthread.php?t=184838](http://ubuntuforums.org/showthread.php?t=184838)_[/COLOR]
[/URL]

---

### Post by History Teacher on 2014-01-18
Thanks!  I've followed the directions on the HPLIP site, downloaded the software and began the installation.  However, I can't get past step two of the wizard because it does not seem to recogonize the printer:

[ATTACH=CONFIG]249574[/ATTACH]

Suggestions?

---

### Post by unixpcguy on 2014-01-18
Did you reboot your pc? It may not have detected the drivers yet.

---

### Post by History Teacher on 2014-01-18
Oddly enough I ran sudo hp-setup again it worked perfectly.  Perhaps you are right, it just didn't detect the drivers right away.  Thanks for all your help!

---

### Post by unixpcguy on 2014-01-18
:)  Not a problem! Mark as solved.

---

