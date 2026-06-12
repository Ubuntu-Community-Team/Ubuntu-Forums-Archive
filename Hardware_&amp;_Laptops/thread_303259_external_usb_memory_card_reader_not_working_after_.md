---
title: "external usb memory card reader not working after upgrade"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by kentb on 2006-11-20
My usb based external memory card reader from SanDisk stopped working after upgrading from Dapper (6.06) to Edgy (6.10).

lsusb output for this device is successful (and unchanged from the upgrade):
[FONT="Courier New"]Bus 004 Device 016: ID 0781:8919 SanDisk Corp.[/FONT]

If I unplug the device (card reader) and then re plug it in, the following dmesg statements are outputted:
[FONT="Courier New"][17185589.500000] usb 4-3.1: USB disconnect, address 15
[17185593.556000] usb 4-3.1: new high speed USB device using ehci_hcd and address 16
[17185593.676000] usb 4-3.1: no configuration chosen from 1 choice[/FONT]

No devices are created in the dev directory when the memory card is inserted. (Before the upgrade a /dev/sd[a-z][1-5] would be created). The "card inserted" light on the device itself also does not illuminate when the card is inserted (only since the upgrade). Nothing is logged (like an error) in /var/log or dmesg when the card is inserted.

When plugged into another PC, running another operating system. the card reader works without error.

Any advise about further diagnostics or pointer to a similar solution would be very much appreciated.

---

### Post by kentb on 2006-11-22
I just figured this out, and it has to do with power management checks that are new to kernel 2.6.16 and above (Edgy is currently 2.6.17). A relevant piece of information is that the usb device that I cannot make work is plugged into a usb hub which is not externally powered (it uses internal usb power). 

Prior to 2.6.16, no "budget" checks were done for usb power, but now if a device will bring it over budget (usually with usb hubs), the device will not be configured. The only clue this has happened was a line found in dmesg:
[FONT="Courier New"][17360832.528000] usb 4-3.1: no configuration chosen from 1 choice
[/FONT]
This warning states the system chose not to configure the device, but does not indicate the reason. I believe future kernel versions will have a more user friendly error message.

A temporary override of this deconfiguration (use at own risk):
[LIST=1]
[*]find the error line in dmesg (or messages or syslog or...) and extract the device number for the usb device you need to activate. The number is directly after the "usb" and directly before the colon. From the example above, the device number would be "4-3.1"
[*]type [FONT="Courier New"]lsusb -v | less[/FONT] and scroll to the device you are wanting to activate and note its configuration number (the value it will be when it is active or configured) signified by "bConfigurationValue"
[*][FONT="Courier New"]cd /sys/bus/usb/devices/x-y.z[/FONT] and then type  [FONT="Courier New"]echo -n  "a" > bConfigurationValue[/FONT] where a is the configuration value taken from the [FONT="Courier New"]lsusb[/FONT] output (typically 1) and x-y.z is the device number from the [FONT="Courier New"]dmesg[/FONT] output.
[/LIST]
This will need to be done every time you unplug/plug the device until you "fix" the power budget problem.

A couple of bug references from other distros:
[http://lists.debian.org/debian-kernel/2006/07/msg00506.html](http://lists.debian.org/debian-kernel/2006/07/msg00506.html)
[https://bugs.gentoo.org/show_bug.cgi?id=132721](https://bugs.gentoo.org/show_bug.cgi?id=132721)
[http://marc.theaimsgroup.com/?l=linux-usb-devel&m=114781479530376&w=2](http://marc.theaimsgroup.com/?l=linux-usb-devel&m=114781479530376&w=2)

---

### Post by secundar on 2006-11-27
Um, can someone write a script for this? For a desktop this wouldn't be a problem but I am usin a laptop an often need to plug/un-plug my mouse and other devices.

---

### Post by WirelessMike on 2007-02-16
Any chance this could be addressed/corrected in the next release (Feisty)?

There are MANY of us having this problem and it is extremely aggravating!  As far as I know from reading these boards, the old method of detection disregarding external power never caused a system to crash.  Changing it has only had a negative effect on users.  There is no logical reason to keep it this way.

---

