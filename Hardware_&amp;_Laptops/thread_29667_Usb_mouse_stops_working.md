---
title: "Usb mouse stops working"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by ZiZe on 2005-04-25
Some times my usb mouse just disconnects, and i have to go around the back of my pc, unplug it and plug it back in to bring it to life again.
I just cant figure out whats wrong. i had the same problem when i ran plane debian and warthy to. KDE and gnome.
i'm running 2.6.10-5-686-smp kernel on a p4 prescott 3ghz with 2gb ram.
The mouse is an Microsoft Intelliexplorer 3.0

And this i found in my /var/logs/user.log
```
Apr 25 13:22:34 localhost hal.hotplug[32123]: DEVPATH is not set
Apr 25 13:22:36 localhost hal.hotplug[32194]: DEVPATH is not set
Apr 25 13:22:36 localhost input.agent[32195]:      tsdev: already loaded
Apr 25 13:22:36 localhost input.agent[32195]:      mousedev: already loaded
Apr 25 13:22:36 localhost input.agent[32195]:      evdev: already loaded
Apr 25 13:22:36 localhost input.agent[32195]:      evbug: blacklisted
Apr 25 13:22:36 localhost usb.agent[32207]:      usbmouse: blacklisted
Apr 25 13:22:36 localhost usb.agent[32207]:      usbhid: already loaded
Apr 25 13:22:37 localhost input.agent[32306]:      evdev: already loaded
Apr 25 13:22:37 localhost input.agent[32307]:      evdev: already loaded
Apr 25 13:22:37 localhost input.agent[32330]:      evdev: already loaded
Apr 25 13:22:37 localhost input.agent[32306]:      evbug: blacklisted
Apr 25 13:22:37 localhost input.agent[32330]:      evbug: blacklisted
Apr 25 13:22:37 localhost input.agent[32307]:      evbug: blacklisted
Apr 25 16:46:09 localhost hal.hotplug[3953]: DEVPATH is not set
Apr 25 16:46:12 localhost hal.hotplug[4027]: DEVPATH is not set
Apr 25 16:46:12 localhost input.agent[4028]:      tsdev: already loaded
Apr 25 16:46:12 localhost input.agent[4028]:      mousedev: already loaded
Apr 25 16:46:12 localhost input.agent[4028]:      evdev: already loaded
Apr 25 16:46:12 localhost usb.agent[4039]:      usbmouse: blacklisted
Apr 25 16:46:12 localhost input.agent[4028]:      evbug: blacklisted
Apr 25 16:46:12 localhost usb.agent[4039]:      usbhid: already loaded
Apr 25 16:46:12 localhost input.agent[4144]:      evdev: already loaded
Apr 25 16:46:12 localhost input.agent[4144]:      evbug: blacklisted
Apr 25 16:46:12 localhost input.agent[4140]:      evdev: already loaded
Apr 25 16:46:12 localhost input.agent[4140]:      evbug: blacklisted
Apr 25 16:46:12 localhost input.agent[4160]:      evdev: already loaded
Apr 25 16:46:12 localhost input.agent[4160]:      evbug: blacklisted

And this when i tailed /var/log/messages:
Apr 25 16:46:09 localhost kernel: usb 2-1: USB disconnect, address 3
Apr 25 16:46:11 localhost kernel: usb 1-2: new low speed USB device using uhci_hcd and address 6
Apr 25 16:46:12 localhost kernel: input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-2
Apr 25 16:46:12 localhost input.agent[4028]:      tsdev: already loaded
Apr 25 16:46:12 localhost input.agent[4028]:      mousedev: already loaded
Apr 25 16:46:12 localhost input.agent[4028]:      evdev: already loaded
Apr 25 16:46:12 localhost usb.agent[4039]:      usbmouse: blacklisted
Apr 25 16:46:12 localhost input.agent[4028]:      evbug: blacklisted
Apr 25 16:46:12 localhost usb.agent[4039]:      usbhid: already loaded
Apr 25 16:46:12 localhost input.agent[4144]:      evdev: already loaded
Apr 25 16:46:12 localhost input.agent[4144]:      evbug: blacklisted
Apr 25 16:46:12 localhost input.agent[4140]:      evdev: already loaded
Apr 25 16:46:12 localhost input.agent[4140]:      evbug: blacklisted
Apr 25 16:46:12 localhost input.agent[4160]:      evdev: already loaded
Apr 25 16:46:12 localhost input.agent[4160]:      evbug: blacklisted

``` 

Anyone who had the same problem and know what i could do to fix it?

---

### Post by xtreem on 2005-04-25
Try this, Im not sure it will work tho.

**sudo gedit /etc/hotplug/blacklist**

Find the 'usbmouse' and hash like '**#usbmouse**'.

Restart ubuntu

---

### Post by ZiZe on 2005-04-25
ok, i've commented it out now and did a /etc/init.d/hotplug restart, only thing now is that my mouse is quite random on when it freezes.
so i will have to wait and see :p

But thanks for the reply, I hope this might work :)

---

### Post by ZiZe on 2005-04-26
Nope  ](*,) 

mouse stopped working as usual.

same errors in the logs.  :-?

i found
sudo /etc/init.d/hotplug restart
is a better way to connect my mouse again instead of unplug and plug in the usb cable, but i'm wondering what the problem is :p

---

