---
title: "ndiswrapper for an Orinoco card?"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by NTolerance on 2005-06-06
Well, after months of trying and failing to get scan support working for my Orinoco card I'm wondering if using ndiswrapper is an option.  Will I lose performance or eat more CPU cycles by doing this?  It sounds like it's got to be easier than trying to install the 0.15rc2 Orinoco drivers which nobody seems to know how to get working.

---

### Post by sebw on 2005-06-10
You can safely follow the following guide [http://ubuntuforums.org/archive/index.php/t-12340.html](http://ubuntuforums.org/archive/index.php/t-12340.html)  where you have posted a message by the way..

I have compiled the drivers (0.15rc2) today following that guide and scan was working.. I've been able to use wifi-radar (which works pretty well once you get scan working   :smile: )..

Unfortunately, Kismet was running so-so, it was only able to monitor a specific channel and not all.. from what is being said here [http://lists.samba.org/archive/wireless/2005-March/002854.html](http://lists.samba.org/archive/wireless/2005-March/002854.html) , the drivers needs to be patched to work fine with Kismet..

Trying to find the patch..

---

