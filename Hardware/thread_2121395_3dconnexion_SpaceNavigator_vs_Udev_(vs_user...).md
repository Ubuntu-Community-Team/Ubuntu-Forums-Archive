---
title: "3dconnexion SpaceNavigator vs Udev (vs user...)"
date: 2013-03-01
forum: Hardware
---

### Post by nwillis on 2013-03-01
Out of pure masochism, I started trying to get my SpaceNavigator 6-axis controller working today.  On 12.04; I'm not interested in using it for SecondLife or GoogleEarth or anything like that -- I just want it running as an input device (which I can then map to generic functions like pan-and-zoom in GIMP or other image editors).

Thing is, most of the docs out there about setting it up are from other distros and ~3 years old.  Several of them recommend adding a udev like so:

KERNEL=="event[0-9]*", SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c626", MODE="0664", GROUP="plugdev", SYMLINK+="input/spacenavigator"

...which should set up a persistant symlink at /dev/input/spacenavigator ... except it doesn't.  Any ideas what's wrong with it?  dmesg reports that the ids are both correct; the device is showing up as event4 so that should match.  I've got the rule saved as /etc/udev/rules.d/90-spacenavigator.rules.  I'm not sure what else there is that could be going wrong.

Any suggestions?

Thanks,
N

---

