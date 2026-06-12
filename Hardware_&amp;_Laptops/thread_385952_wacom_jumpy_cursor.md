---
title: "wacom jumpy cursor"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by Dr.Who on 2007-03-16
Hello, I have an old serial Wacom tablet and it works almost under current Ubuntu inclusive pressure with the standard Ubuntu Wacom drivers. But the cursor acts jumpy, twitching all the way. What can be done about that?

Thanks in advance

---

### Post by Scunizi on 2007-03-16
I have a newer wacom usb graphire 4.  In getting that to work I did a lot of reading and seem to remember something about your issue.  I think it stems from the computer recognizing the wacom as a HID device and because of that it thinks it's a mouse more than a tablet.  You may need to install the wacom drivers and configure your xorg.conf correctly.  You'll find a lot of information at [http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/) and also by searching wacom on [http://wiki.ubuntuforums.org](http://wiki.ubuntuforums.org).  You should be able to work this our fairly easy.

---

