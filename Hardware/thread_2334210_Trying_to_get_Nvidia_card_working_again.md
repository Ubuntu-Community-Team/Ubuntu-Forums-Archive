---
title: "Trying to get Nvidia card working again"
date: 2016-08-17
forum: Hardware
---

### Post by wintermute115 on 2016-08-17
I have a desktop machine that I recently upgraded from Kubuntu 14.04 to 16.04. It has an Nvidia GT610 graphics card running three monitors, using the proprietary drivers. Last week, I was noodling around in the settings and noticed there was a newer driver available, so I upgraded it. On Monday morning, I discovered one of the monitors wasn't working, which I attributed to the driver upgrade. I tried to roll it back, or find new drivers, but nothing seemed to help, and I eventually got it to the point where it would not boot at all with the Nvidia card in there.

I've since figured out that the monitor itself was bad, and if I'd thought to swap it out before diving into the drivers, everything would probably have been fine.

I'm currently making do with an old Radeon card that can only drive two monitors, but I really want to get the Nvidia card working again. I've tried downloading the proprietary driver again, but it won't install unless the card is installed, and then it won't boot.

Any help would be greatly appreciated. Thanks.

[This is what it looks like when it stops booting]("https://www.dropbox.com/s/e61xe8rew4zwktv/2016-08-16%2013.16.09.jpg?dl=0")

---

### Post by CatKiller on 2016-08-17
I can't read the text in your photo, but the best bet would be to uninstall all the proprietary drivers, since the open source ones play nicely with any hardware. The proprietary ones mess with both the kernel and the X server. You should undo any tweaks that you've done while fiddling, too.

Then install the NVidia card and see where you are. You should be free of any contamination then, so it should boot, although potentially it will only display on one monitor.

You should then be in a better place to get to where you started from.

---

