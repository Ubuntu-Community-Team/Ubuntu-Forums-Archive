---
title: "ipw2200 and wpa"
date: 2004-12-04
forum: Hardware &amp; Laptops
---

### Post by fromtheflames on 2004-12-04
Hello everyone...
I'm Thomas from Italy.

My problem...
Just unpacked a new notebook (acer tm3202xci) and tried to get this wireless card up with WPA support.
Spent about 2 hours without result, anyone had success with it?

Tried with wpa_supplicant 0.2.5 and an updated (via ethernet) Warty installation; followed [this](http://www.ubuntulinux.org/wiki/WPAHowto) howto...  :-(

---

### Post by Nano on 2004-12-09
> **fromtheflames]Hello everyone...
I'm Thomas from Italy.

My problem...
Just unpacked a new notebook (acer tm3202xci) and tried to get this wireless card up with WPA support.
Spent about 2 hours without result, anyone had success with it?

Tried with wpa_supplicant 0.2.5 and an updated (via ethernet) Warty installation said:**
> this[/URL] howto...  :-(
 As far as I know Acer laptops (same as my Medion) need to be enable-flagged from one of the Hot-keys in the keyboard.
Check this out: 
[http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/)
[http://home.conceptsfa.nl/~revdmeer/md40100/#specialkeys](http://home.conceptsfa.nl/~revdmeer/md40100/#specialkeys)

---

### Post by fromtheflames on 2004-12-09
[QUOTE=Nano]As far as I know Acer laptops (same as my Medion) need to be enable-flagged from one of the Hot-keys in the keyboard.
Check this out: 
[http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/)
[http://home.conceptsfa.nl/~revdmeer/md40100/#specialkeys](http://home.conceptsfa.nl/~revdmeer/md40100/#specialkeys)[/QUOTE]
 I didn't specify that working with wep or no encrypt on my access point, is well supported...

---

### Post by jneal on 2004-12-21
This should help, it's from README.ipw2200 for the current driver (Release 0.19):

TODO
------------ -----   -----       ----       ---       --         -
- Fix statistics returned by iwconfig and /proc/net/wireless
- Add firmware restart backoff algorithm (see ipw2100 project)
- Look into (and hopefully enable) Monitor/RFMon mode
- Add WPA support

Also see this post:

[http://sourceforge.net/mailarchive/message.php?msg_id=10030082](http://sourceforge.net/mailarchive/message.php?msg_id=10030082)

- Joshua Neal

---

### Post by fromtheflames on 2004-12-21
So, we have to wait!? :cry:

---

### Post by toleacezar9117 on 2007-05-15
> **jneal said:**
> This should help, it's from README.ipw2200 for the current driver (Release 0.19):

TODO
------------ -----   -----       ----       ---       --         -
- Fix statistics returned by iwconfig and /proc/net/wireless
- Add firmware restart backoff algorithm (see ipw2100 project)
- Look into (and hopefully enable) Monitor/RFMon mode
- Add WPA support

Also see this post:

[http://sourceforge.net/mailarchive/message.php?msg_id=10030082](http://sourceforge.net/mailarchive/message.php?msg_id=10030082)

- Joshua Neal


[magnets build Britney Spears Ebay Girls](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

