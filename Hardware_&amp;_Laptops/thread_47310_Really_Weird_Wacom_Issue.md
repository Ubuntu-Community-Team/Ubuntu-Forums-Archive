---
title: "Really Weird Wacom Issue"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by watchitman on 2005-07-08
My Graphire 2 works great! The weird part is, every time I restart, it changes which device event it's on. It bounces back and forth between event3 and event4. So I have to manually edit my xorg.conf and restart X. And no, I haven't added any new mice or any hardware at all. Anyone have any thoughts on what could be causing this?

---

### Post by watchitman on 2005-07-08
*bump*

---

### Post by watchitman on 2005-07-09
*bump*

Why isn't anyone answering this?

---

### Post by watchitman on 2005-07-12
*bump*

---

### Post by jonatin on 2005-07-25
[QUOTE=watchitman]*bump*[/QUOTE]

This happens to me with a Graphire 2 when I use my KVM switch on occasion.  Still haven't figured the wacom out completely.

My suggestion is to make sure the tablet isn't installed on a USB hub... I don't get this problem at all when I'm plugged in directly to the back of the machine.

What's really nagging me is the "dancing" cursor.  And it's not my screen refresh rate because the same hardware in winxp doesn't have any jumpiness.  <sigh>

HTH, and if I figure it out I'll post more.


PS:
For what it's worth, this tablet is the only "quality of life" issue that's keeping me from using Ubuntu more often.  I get fed up with the horrible cursor handling, and no one really seems to have any ideas.  That's what happens with esoteric hardware that developers don't use much...:-|

---

### Post by megamads on 2006-08-04
My graphire2 works fine GDM, then I get the dancing cursor problem once XFCE loaded. 

Found a workaround by tuning the mouse acceleration in the XFCE Settings Manager (I can't see any reason why this shouldnt work in Gnome or KDE). 

Is there any way to prevent the tablet from beeing "mouse accelerated" ?

---

### Post by ola on 2007-05-25
Hi!

I'm having the same problem with changing /dev/input/events when using a Wacom (Graphire4) table via a KVM switch. The tablet works but I can't change it to mouse mode which I prefer. I get the following output in the log file.

Fresh boot and the Wacom tablew works as supposed:
```

May 25 13:46:53 olacomputer kernel: [  839.828000] input: Wacom Graphire4 6x8 as /class/input/input27
May 25 13:46:53 olacomputer logger: device 1-4.2.4:1.0 is bound to the wacom driver
May 25 13:46:53 olacomputer logger: no need to rebind

```

When I flip the KWM - switch I get the following output instead:
```

May 25 13:48:23 olacomputer kernel: [  929.632000] usb 1-4.2: USB disconnect, address 21
May 25 13:48:23 olacomputer kernel: [  929.632000] usb 1-4.2.3: USB disconnect, address 23
May 25 13:48:23 olacomputer kernel: [  929.632000] usb 1-4.2.4: USB disconnect, address 24
May 25 13:48:23 olacomputer kernel: [  929.772000] usb 1-4.3: USB disconnect, address 22

May 25 13:48:30 olacomputer kernel: [  937.260000] usb 1-4.2: new high speed USB device using ehci_hcd and address 25
May 25 13:48:30 olacomputer kernel: [  937.364000] usb 1-4.2: configuration #1 chosen from 1 choice
May 25 13:48:30 olacomputer kernel: [  937.364000] hub 1-4.2:1.0: USB hub found
May 25 13:48:30 olacomputer kernel: [  937.364000] hub 1-4.2:1.0: 4 ports detected
May 25 13:48:31 olacomputer kernel: [  937.676000] usb 1-4.3: new low speed USB device using ehci_hcd and address 26
May 25 13:48:31 olacomputer kernel: [  937.784000] usb 1-4.3: configuration #1 chosen from 1 choice
May 25 13:48:31 olacomputer kernel: [  937.788000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input28
May 25 13:48:31 olacomputer kernel: [  937.788000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.1-4.3
May 25 13:48:31 olacomputer kernel: [  937.992000] usb 1-4.2.3: new low speed USB device using ehci_hcd and address 27
May 25 13:48:31 olacomputer kernel: [  938.100000] usb 1-4.2.3: configuration #1 chosen from 1 choice
May 25 13:48:31 olacomputer kernel: [  938.104000] input: PS2 to USB as /class/input/input29
May 25 13:48:31 olacomputer kernel: [  938.104000] input: USB HID v1.10 Keyboard [PS2 to USB] on usb-0000:00:0b.1-4.2.3
May 25 13:48:31 olacomputer kernel: [  938.112000] input: PS2 to USB as /class/input/input30
May 25 13:48:31 olacomputer kernel: [  938.112000] input: USB HID v1.10 Mouse [PS2 to USB] on usb-0000:00:0b.1-4.2.3
May 25 13:48:31 olacomputer kernel: [  938.316000] usb 1-4.2.4: new low speed USB device using ehci_hcd and address 28
May 25 13:48:31 olacomputer kernel: [  938.420000] usb 1-4.2.4: configuration #1 chosen from 1 choice
May 25 13:48:31 olacomputer kernel: [  938.424000] input: Wacom Graphire4 6x8 as /class/input/input31
May 25 13:48:32 olacomputer logger: device 1-4.2.4:1.0 is bound to the wacom driver
May 25 13:48:32 olacomputer logger: no need to rebind

```

Every time I flip the KVM-switch I get another device number. Like:
```

May 25 13:49:33 olacomputer kernel: [ 1000.288000] usb 1-4.2: USB disconnect, address 25
May 25 13:49:33 olacomputer kernel: [ 1000.288000] usb 1-4.2.3: USB disconnect, address 27
May 25 13:49:33 olacomputer kernel: [ 1000.288000] usb 1-4.2.4: USB disconnect, address 28
May 25 13:49:33 olacomputer kernel: [ 1000.416000] usb 1-4.3: USB disconnect, address 26
May 25 13:53:55 olacomputer kernel: [ 1261.856000] usb 1-4.2: new high speed USB device using ehci_hcd and address 29
May 25 13:53:55 olacomputer kernel: [ 1261.948000] usb 1-4.2: configuration #1 chosen from 1 choice
May 25 13:53:55 olacomputer kernel: [ 1261.948000] hub 1-4.2:1.0: USB hub found
May 25 13:53:55 olacomputer kernel: [ 1261.948000] hub 1-4.2:1.0: 4 ports detected
May 25 13:53:55 olacomputer kernel: [ 1262.256000] usb 1-4.3: new low speed USB device using ehci_hcd and address 30
May 25 13:53:55 olacomputer kernel: [ 1262.352000] usb 1-4.3: configuration #1 chosen from 1 choice
May 25 13:53:55 olacomputer kernel: [ 1262.356000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input32
May 25 13:53:55 olacomputer kernel: [ 1262.356000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.1-4.3
May 25 13:53:56 olacomputer kernel: [ 1262.556000] usb 1-4.2.3: new low speed USB device using ehci_hcd and address 31
May 25 13:53:56 olacomputer kernel: [ 1262.668000] usb 1-4.2.3: configuration #1 chosen from 1 choice
May 25 13:53:56 olacomputer kernel: [ 1262.672000] input: PS2 to USB as /class/input/input33
May 25 13:53:56 olacomputer kernel: [ 1262.672000] input: USB HID v1.10 Keyboard [PS2 to USB] on usb-0000:00:0b.1-4.2.3
May 25 13:53:56 olacomputer kernel: [ 1262.680000] input: PS2 to USB as /class/input/input34
May 25 13:53:56 olacomputer kernel: [ 1262.680000] input: USB HID v1.10 Mouse [PS2 to USB] on usb-0000:00:0b.1-4.2.3
May 25 13:53:56 olacomputer kernel: [ 1262.880000] usb 1-4.2.4: new low speed USB device using ehci_hcd and address 32
May 25 13:53:56 olacomputer kernel: [ 1262.992000] usb 1-4.2.4: configuration #1 chosen from 1 choice
May 25 13:53:56 olacomputer kernel: [ 1262.992000] input: Wacom Graphire4 6x8 as /class/input/input35
May 25 13:53:56 olacomputer logger: device 1-4.2.4:1.0 is bound to the wacom driver
May 25 13:53:56 olacomputer logger: no need to rebind

```

I guess that's the problem is that it doesn't realize that it should rebind it.

Any ideas?

---

### Post by watchitman on 2007-05-25
I haven't had the problem with the last couple versions of Ubuntu. As you can see from the date, the original post is nearly 2 years old. I imagine the KVM switch is throwing a wrench into the works. If at all possible, you should simply plug the tablet directly into the machine you use the tablet on the most. I don't know what any of that output gibberish means, sorry. I wish I could be of more help.

---

### Post by mukiex on 2007-05-28
I believe the trick is not to link it to event3 or event4 in your xorg.conf, but to install wacom-tools (multiverse? I know it's not in the default repos) and link to like, /dev/wacom or /dev/input/wacom , I forget which one. wacom-tools automatically syncs that up for you.

---

### Post by electrofox on 2007-05-30
Try this:  [http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151)
Make sure to read the first reply as well.
Good Luck.

---

