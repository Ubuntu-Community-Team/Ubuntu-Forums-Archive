---
title: "User permissions for scanner on libusb - Jaunty"
date: 2009-05-24
forum: Hardware
---

### Post by fishears on 2009-05-24
OK, I'm assuming something's changed in Jaunty because I can no longer use my scanner (connected on /dev/bus/usb/005/002) as anything other than root.

I tried changing the permission of 002 so that my user account had access but that gets reset to root only as soon as I log back in.

Anyone know how I fix this? It's somewhat disappointing when an upgrade becomes a downgrade.... I mean, why isn't there a "scanner management" in admin or something?

scanimage -L gives:
device `brother2:bus2;dev2' is a Brother DCP-115C USB scanner
lsusb gives:
Bus 005 Device 002: ID 04f9:018c Brother Industries, Ltd DCP-115C

THANK YOU

---

### Post by fishears on 2009-05-24
So, I figured out a way to do this myself although it's not a good way to do it but still it might be the only way to do it. Either way, I'm less than pleased...

I did this:
sudo gedit /lib/udev/rules.d/50-udev-default.rules
change MODE="0664" to MODE="0666" on line with SUBSYSTEM=="usb"

This gives RW on all USB devices - which I may or may not want but don't seem to have a choice about.

Now I can scan as a user but so could any other user.

---

### Post by cgalpin on 2009-06-02
You can add a more specific rule that matches the device and use OWNER="fishears" to limit access to the user fishears

hth
charles

---

### Post by splint-84 on 2009-06-18
Thanks fishears

This worked for me in 9.04 as well with a Brother DCP-330C. Hopefully there will be better support for this in the next release or something.... It is slightly frustrating that with each new release we have to do something like this to make the scanners work.

---

### Post by Yellow Pasque on 2009-06-19
Maybe there's a group in /etc/group (like 'scanner' or 'sane') that you need to add yourself to.

---

