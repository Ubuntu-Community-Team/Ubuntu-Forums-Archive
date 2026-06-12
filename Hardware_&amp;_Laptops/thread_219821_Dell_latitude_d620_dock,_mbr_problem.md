---
title: "Dell latitude d620 dock, mbr problem"
date: 2006-07-20
forum: Hardware &amp; Laptops
---

### Post by bkristan on 2006-07-20
I'm running Dapper on a Dell Latitude d620. I have WinXP on sda1, Dapper on sda3, and grub installed in the default location (the mbr of sda, right?). I also have a docking station with an external LCD monitor. When I run the laptop un-docked, everything works fine on both Dapper and Windows. Twice, though, when I've used the docking station I've had the computer refuse to boot - I get the BIOS splash screen, the screen goes black, and then it reboots. The first time I could see grub try to load, the second time I couldn't. In both cases I could boot into a rescue cd and re-install grub. The BIOS splash screen stayed up for an unusually long time too.

The second time this happened (today) I had docked, booted into Windows, then rebooted. The first time I don't remember the sequence of events, but I had been trying to get X to work correctly, and I know that I had booted into Windows at least once.

Any ideas? I'm interested in figuring out what's happening, but if there's a work-around (like installing grub in a different location maybe?) I'd be willing to try it out - has anybody seen this before?

Thanks!

---

### Post by bkristan on 2006-07-25
Since I posted this message, I had the problem again, but this time without using the docking station.

So, the problem seems to be that when I boot into Windows XP, then shut down, Grub is no longer able to run, and the computer starts to repeatedly reboot until I shut it off or boot from a rescue CD.

Is there a known problem with Windows corrupting the MBR? Is there a fix or work-around?

Thanks!

---

