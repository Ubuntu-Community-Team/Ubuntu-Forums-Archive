---
title: "Synchronizing jpilot and palm in Jaunty 9.04"
date: 2009-05-20
forum: Hardware
---

### Post by pennygov on 2009-05-20
In case someone else has a problem with this I'm posting my solution, which is extremely easy (if you know what to do).

The past couple of upgrades (Hardy and Intrepid) had built-in support (visor module) so nothing was needed, as I recall.

This version (Jaunty 9.04) doesn't have the visor module built-in. You DON'T need to add any special rules ... JUST add "visor" (without quotes) to the bottom of your /etc/modules file (run sudo modprobe visor to load it now without having to reboot) and your jpilot should then sync with no problem. That's all.

This worked on my Kubuntu 9.04 machine and my aspire-one running Eeebuntu 3 base with kubuntu-desktop added.

---

### Post by albertazzo on 2009-06-17
I tried that but what I got is:
(I translate from my Ubuntu 9.04 Italian version):

"Warning (gdpilotd)
Failed connection using device "Cable" on <<usb:>> port.
Check configuration as the new synchronization style libusb <<usb:>> was required,
but the old style kernel module <<visor>> was loaded

What can I do?

Thunderbird (with extension) is not synchronizing with my Palm TX, 
Evolution doesn't sync neither the Calendar nor the Activities (it syncs my Contacts only),
JPilot is not working at all....

---

### Post by mdwy62 on 2009-06-18
I am also trying to sync with jpilot, after evolution failed completely to pick up my calendar from my Treo755p. I am using Jaunty.

I removed gnome-pilot and gnome-pilot-conduits because I believe these are designed to work with evolution, not jpilot.

I added visor to end of /etc/modules and ran 
sudo modprobe visor.

In terms of Jpilot settings, I'm using usb: and a reduced serial rate of 19200.

I started the sync on my Treo, and then hit the sync button in jpilot. 

This worked!

I have since been able to raise the serial rate to 57600 and sync still seems to work.

---

### Post by treesurf on 2009-06-20
Thanks so much, this worked perfectly for me, syncing with gnome-pilot.  I can't believe they include gnome-pilot with the operating system but then neglect to include the visor module.  It just doesn't make sense.

---

### Post by crlbeijing on 2009-08-16
Big thanks for the tip on adding "visor" (without the quotes) to /etc/modules.  Synchronization now seems to work perfectly, but I get the following message each time I synchronize or plug in my Treo 680:

Warning (gpilotd) - Failed to connect using device 'Cradle', on port 'usb:', Check your configuration as you requested libusb 'usb:' syncing, but have the old-style 'visor' kernel module loaded.  You may need to select a 'ttyUSB...' device.

As I said, the synchronization still seems to work so I guess I shouldn't be concerned about the warning.

Many thanks.

---

### Post by johneh on 2009-10-17
thanks [mdwy62]("http://ubuntuforums.org/member.php?u=459388") for the info
works with my palm tx like a dream

---

