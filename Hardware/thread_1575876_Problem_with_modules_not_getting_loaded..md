---
title: "Problem with modules not getting loaded."
date: 2010-09-16
forum: Hardware
---

### Post by razzmataz on 2010-09-16
Howdy,
This morning I encountered a problem after booting up my laptop. The mouse did not work and none of the wireless modules were loaded.  I was able to Ctrl-F1 and get to the console and load the psmouse driver, log in thru the graphical interface and eventually figure out the order in which to load modules to get the wireless working (modprobe was not loading the wireless module and its dependencies).

Hardware: Dell Latitude D610, stock broadcom b43 wireless, 2Gb RAM, 60GB harddisk.
Software: Ubuntu 10.04.1


After installation, I ended up running the b43-fwcutter stuff to grab the firmware and place it in the normal spot. Everything seemed to work fine yesterday. One thing I did notice after getting the wireless firmware working, was that plugging in a usb harddrive that's worked on numerous other linux boxes did not even register.  And this morning, my usb mouse did not get noticed either.

I'm guessing that getting the b43 firmware set up yesterday messed up some of the module dependencies in a less than favorable way.  Any quick suggestions to fix that?  Meanwhile, I'll try to google the symptoms and post updates.

Thanks in advance!

---

