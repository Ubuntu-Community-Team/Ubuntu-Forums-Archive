---
title: "Prevent ACPI from dimming screen when switching console?"
date: 2009-02-14
forum: Hardware
---

### Post by eater on 2009-02-14
I'm running Intrepid on a Thinkpad x200s. When I switch from X to a virtual console, or vice versa, the screen's brightness drops to very dim. I then have to manually boost it back to normal with the brightness keys.

This problem does not occur if I "modprobe -r video", but doing that removes my ability to adjust the brightness at all.

Additionally, often switching from X to a console and back makes my HAL-based trackpoint scrolling -- configured as seen at [ThinkWiki]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#TrackPoint_under_Xorg-7.4.2B_using_HAL") -- stop working; switching again, or a few times back and forth, brings it back.

Where is this behavior controlled? What's the best way to solve these very annoying glitches?

Thanks!

---

