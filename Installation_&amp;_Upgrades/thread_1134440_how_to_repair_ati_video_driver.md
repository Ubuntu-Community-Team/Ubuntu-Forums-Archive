---
title: "how to repair ati video driver"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by scott1256ca on 2009-04-23
This is for an intrepid 64 bit install.
I had catalyst drivers installed and when I booted the resolution was wrong. I tried to fix it but when I rebooted, I lost the x display altogether. I have tried a couple of repairs but the display is just hosed. By that I mean that the display is not black, it is just kind of junk. I can make out some of the text that looks almost like I'm in the bios.

dpkg-reconfigure xserver-org has not helped.
trying to edit xorg.conf files has not helped
trying to revert to vesa as the driver has not worked.
Replacing vesa with ati has not worked.
dpkg-reconfigure does not ask anything about the resolution of my display. I'm not sure if that is the problem (bad setting) or not. I don't see where I would go to edit that to, for example, force it to open as 1024x768

I also tried to reinstall catalyst, but I can't generate the .deb packages from the recovery console. I have wireless, and it doesn't seem to be connecting. i have also run "fix broken packages" and "repair X" (or whatever the items are on the recovery menu) to no avail.

Right now, I'd be happy to remove those crappy catalyst drivers and go to the open source drivers, but I don't see how to force a repair to install that and reconfigure X. The 8.10 live cd doesn't seem to have any "repair a broken install" option. (Wow, seems like a real oversight!).

I'd rather not have to install from scratch, but I am out of other ideas.
Any suggestions?

Thanks

p.s. next video card will be nvidia. I think I'm done with ATI forever.

---

