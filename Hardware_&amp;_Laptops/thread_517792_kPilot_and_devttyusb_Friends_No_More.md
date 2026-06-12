---
title: "kPilot and /dev/ttyusb*: Friends No More"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by thesnowysoviet on 2007-08-05
After combing through related threads, I haven't seen a reply yet that relates to this.  Apologies if it seems repeatitive, but...

I'm having trouble syncing my Palm m125.  I'm using Dapper and kPilot 4.6 to connect it to my IBM Thinkpad T30, for all that's worth.  It used to work just fine, through several hotsyncs over several days.  After a reboot, however, I get back from kPilot an error message, something about "device not found."  Using the auto-detect tool, I get this:

> 21:38:04 Pilot device /dev/ttyusb1 does not exist. Probably it is a USB device and will appear during a HotSync.

I connect using a USB device, yes, but there's no /dev/ttyusb1?  Tail says otherwise:

> andy@TheGeneral:~$ sudo tail -f /var/log/messages
Aug  4 21:37:28 TheGeneral kernel: [17183156.844000] visor 2-2:1.0: Handspring Visor / Palm OS converter detected
Aug  4 21:37:28 TheGeneral kernel: [17183156.844000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Aug  4 21:37:28 TheGeneral kernel: [17183156.844000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB1
Aug  4 21:38:34 TheGeneral kernel: [17183222.740000] usb 2-2: USB disconnect, address 27
Aug  4 21:38:34 TheGeneral kernel: [17183222.740000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Aug  4 21:38:34 TheGeneral kernel: [17183222.740000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Aug  4 21:38:34 TheGeneral kernel: [17183222.740000] visor 2-2:1.0: device disconnected

So, there *is* a ttyUSB1 (and ttyUSB0, apparently), and it connects and disconnects predictably, but now tail reports "kernel: [17183675.320000] usb 2-2: new full speed USB device using uhci_hcd and address 29" as well.  

kPilot still returns the same error, and I'm not syncing anything at all; the Palm just times out the connection.  Help!

---

### Post by pbcartwright on 2007-08-05
you might try looking into joining the kde-pim email list, they talk about those issues alot..
KDE PIM users mailing list
[email]kdepim-users@kde.org[/email]
[https://mail.kde.org/mailman/listinfo/kdepim-users](https://mail.kde.org/mailman/listinfo/kdepim-users)

---

### Post by lasing all day on 2008-07-13
thesnowysoviet,

Hey did you ever figure out how to sync your palm m125? I have that same problem errorwise when trying to sync the device with a hot sync through usb. This is done on a dell inspiron 6000 laptop. I ask you because I don't really want to join a kde pim mailing list, because that would be more work.

lasingallday

---

