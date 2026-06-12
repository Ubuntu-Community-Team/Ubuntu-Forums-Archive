---
title: "Not finding any hardware drivers?"
date: 2009-10-29
forum: Hardware
---

### Post by cdkee on 2009-10-29
Hey did a clean install of 9.10 today, and have my computer temporarily connected to my laptop, and am bridging internet.

In 8.10 and 9.04 when I would connect it to the internet after install, I would run hardware drivers it would find the drivers (wifi-card, and video) automatically.  I've got it connected to the internet now but when I open up System->Administration->Hardware Drivers nothing shows up.

Any way to do this manually? My wifi-card is model WMP54GS and I have a nVidia FX5200 for video.  These both worked fine with the previous two versions of Ubuntu.  Ran system testing, so it detects it but for some reason doesn't see wireless networks.  And the tell-tale sign it hasn't updated gfx driver is that there is a big black vertical bar on the left side of my monitor.

Thanks for any help.

---

### Post by cdkee on 2009-10-29
Okay sorry for the double post but I got it.

For anyone else:

Go to System->Administration->Update Manager and check for updates regardless of whether or not it says it has.

Then go to hardware drivers and it will detect them.

---

