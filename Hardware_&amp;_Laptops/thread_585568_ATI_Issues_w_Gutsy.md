---
title: "ATI Issues w/ Gutsy"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by kulturloseramerikaner on 2007-10-21
Ok, for various reasons I decided to wipe the slate clean and do a fresh install of Gutsy after attempting the upgrade.  When running the livecd, the native monitor res. is detected perfectly (Samsung Syncmaster 226BW @ 1680x1050.)  After first login, of course, Update Manager squawks about the availability of the proprietary ATI driver.  Trouble is, after installing it and logging back in, I get nothing.  No image whatsoever, except for the monitor firmware flashing about recommended settings.  How do I resolve this?
Thanks in advance.

---

### Post by wareagle on 2007-10-21
Please post the contents of your /etc/X11/xorg.conf file.

---

### Post by kulturloseramerikaner on 2007-10-21
I went in w/ Synaptic and installed the "Radeon" driver as opposed to the diver that Restricted Devices Manager wanted to apply, and all seems to be working for now.
Thanks though.

---

