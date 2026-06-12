---
title: "Disable faulty NVIDIA graphics card?"
date: 2010-11-27
forum: Hardware
---

### Post by ThomWilhelm on 2010-11-27
My NVIDIA graphics card on my laptop I am sure is busted. I get the following messages in the syslog as it crashes and have found many other users reporting this on other linux OS'es without common resolution:

Nov 27 20:20:53 laptop1 kernel: [195667.933095] NVRM: Xid (0001:00): 6, PE0001 
Nov 27 20:21:01 laptop1 kernel: [195676.010738] NVRM: Xid (0001:00): 6, PE0001 
Nov 27 20:21:01 laptop1 kernel: [195676.077658] NVRM: Xid (0001:00): 6, PE0001 0100 00000000 00000000 00000000 00000000

These happen randomly and the screen flashes wildly before locking completely, then when I reboot I get the BIOS screen and further ones split into 6 sections (do not ask!). I have to restart about 10 times or more before it works correctly.

I have logged in and I have disabled the NVIDIA drivers from System -> Administration -> Hardware Drivers, but does this still mean my laptop will be making use of the dodgy card?

Is there any way I can disable the card completely from Ubuntu (10.10)? I cannot do this from the BIOS and would like to not take the laptop apart.

Thanks!

---

### Post by ThomWilhelm on 2010-12-29
Fixed by going to:

/lib/modules/2.6.32-26-generic/kernel/drivers/gpu/drm/nouveau

And renaming "nouveau.ko" to "nouveau.ko.backup", preventing the nouveau driver being loaded. My screen is still messed up (split into 6 identical parts), but at least the server doesn't crash because of this driver and I can VNC in to administrate.

Hope this helps someone!

---

### Post by b2ag on 2011-03-27
This thread helped me to confirm what i already suspected.
Thanks a lot.

PS: Card was broken short after Dell service. Already wondered what happens this time. Everytime they open my laptop to fix something breaks another. 6 times in a row...

---

