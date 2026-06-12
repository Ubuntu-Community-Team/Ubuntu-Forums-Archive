---
title: "Please Help a newbie! ,Ubuntu Persistent on USB"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by sangup on 2009-07-16
Hi, I am trying to use Ubuntu persistent on a 16 GB USB flash drive on a Thinkpad T43. I get the error : :"Buffer I/O *error* on device [I]FD0" . 

[/I]I have been reading extensively on internet about but yet to find something that works. I know that it is not problem with the boot sequence since Thinkpad Bios setup was changed to boot from USB ( verified working by Ubuntu boot from USB if I select the "non persistent" option in the boot menu )
So it has to be something wrong with the Persistence mode. I have no idea what could be the issue

Ubuntu 9.04
16 GB flash drive formatted in windows

Edit: I tried this on my friend's dell laptop and the USB can boot in persistence mode without any issues.

---

### Post by Mighty_Joe on 2009-07-17
That's just crazy.  It works on your friend's computer but not on yours?  I've run into some bugs with the USB creator.  [large persistent partitions]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544") and [not having a partition table]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865") seem to screw it up, but in those cases I'd expect the USB drive would not work on ANY computer.
We've collected some alternatives to the USB creator [in this post]("http://ubuntuforums.org/showthread.php?t=1193680").  Try a full install, that's my preference.

---

