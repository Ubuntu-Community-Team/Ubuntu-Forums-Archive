---
title: "usb hub &amp; webcam/bluetooth dongle ?"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by peyu on 2007-11-19
I'm using a Toshiba Satellite Laptop and it has only 3 usb ports, so I bought a conceptronic usb hub with its own power supply to increase the port number.

I've got a Logitech Webcam for Notebooks and a Conceptronic bluetooth dongle.

In the case of the webcam, It works with Skype 2.0 and camorama if I plug it directly on the computer, but camorama and skype don't detect any device if I plug it through the hub.

In the case of the bluetooth dongle, I'm using Blueman to manage a bluetooth headset connection. It works when I plug directly on the computer (I can hear mp3 using xmms to play in the headset), but doesn't if I use the usb hub. In fact, it seems to work, it connects to headset, but when I push play, It refuses to play.

Of course, other devices work with this usb hub (external hard drive, mouse, keyboard)

Do you have any idea about this problem ?

Thanks in advance.



Peyu

---

### Post by oneiota on 2007-12-28
I can't help but wanted to say that I also have the same issue - my Logitech Notebook webcam works nicely when plugged into a direct USB socket but it fails to work when plugged into a USB hub, even though other devices work in the USB hub such as external drives, card readers etc.

I won't bother trying my bluetooth dongle in the USB hub now that you've mentioned your experience.  It works well plugged in directly.

I can only guess that the hub (even with a single device plugged in) must have a lower 'capacity' of some type because the channel is split in two (or more).  This might be fine for transferring data about but in real time (such as streaming video/audio demands of a webcam or bt headset) perhaps a dedicated usb port is required.

If this hunch is incorrect, it would be good if someone could advise of any fix as it must be terribly limiting for a laptop user with only two usb ports.

---

### Post by shonisan on 2008-01-05
You will find that this is true for Windows too.

Many devices draw power from the USB port itself and can't do so through a hub.

---

### Post by oneiota on 2008-01-05
Thanks - was hoping someone could confirm the reason.  

If it is a power issue, then it makes some sense that we can see the devices are present but they simply fail at the point of putting them into active operation.

Hold on - Peyu's hub has it's own power supply.  So what is the problem in *this* case?

---

### Post by peyu on 2008-01-07
I don't think it's a usb problem but more ubuntu problem, beacause in my case the usb hub has its own power supply, and also because in windows (i have a dual-boot) everything works well: I can use the bluetooth dongle and the webcam though the hub.

May be we can fill a bug in launchpad ?

---

### Post by oneiota on 2008-01-07
Yes, agreed!

---

### Post by peyu on 2008-01-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/181202](https://bugs.launchpad.net/ubuntu/+bug/181202) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Bug report created, the bug number in launchpad is #181202.

---

