---
title: "Touchpad doesn't work but USB mouse does"
date: 2009-02-19
forum: Hardware
---

### Post by flipsside on 2009-02-19
I'm completely green with Ubuntu so bear with me. I installed for the first time Ubuntu in a Sony VGN-S480B laptop. Everything installed fine except the touchpad does not respond. I know it works since it was running in XP. I've read about editing xorg.conf and managed to find it by searching the file Places/Computer but after editing, it won't let me save it. It says something to the effect that I don't have permission or authorized. If someone doesn't mind, could someone give me a "blow-by-blow" on how to edit this? Is this something that needs to be done at the root in "DOS mode". Sorry, I know nothing of Ubuntu nomenclature or syntax. Thanks.

---

### Post by geraldm on 2009-02-19
I think a simple answer would not do.  
Always back up that file by copying it to a new location before making any changes, so that you can restore it if you make a mistake.
For older systems, the system file was found at /etc/X11/xorg.conf.  You would normally copy that file to your own home directory and make the changes there.
Then restart the X server and see if your changes worked.  The local copy is preferred to the system copy. (I do not recall whether it should be ~/xorg.conf or ~/.xorg.conf at the moment. 
You may also need to know that newer systems are not necessarily using either the system copy or the local copy; both may be ignored.  Monitor devices provide a methods of conveying the information from the device to the system, and there is much less need to provide the configuration file such as xorg.conf because the system can know what specifications are needed.

Gerald

---

