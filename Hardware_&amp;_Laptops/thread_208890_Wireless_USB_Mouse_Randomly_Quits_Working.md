---
title: "Wireless USB Mouse Randomly Quits Working"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by captain_bogus on 2006-07-04
Hi, every 2 to 20 minutes my wireless USB mouse just quits working. No motion, no button clicks, nothing. It's a Kensington pocket mouse, the USB plugin looks like a pen drive and has a red light that blinks when I move the mouse. The light will continue to blink when it freezes up and I move the mouse so I don't think it's a hardware problem. Plus, in windows, this never happens. And no, it's not the batteries .

I'm using a Toshiba Satellite L25 with a touchpad so when my mouse freezes up I can start using my touchpad, thankfully.

The only thing that's works is rebooting.

I've tried unplugging the little pen drive looking thing and replugging it, that doesn't work. Nor does plugging it in a different USB port.

I've also tried a couple of solutions I found here:
[http://www.ubuntuforums.org/showthre...quit+w](http://www.ubuntuforums.org/showthre...quit+w) orking
They don't work either. 

Output of lsusb
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 047d:1035 Kensington
Bus 002 Device 001: ID 0000:0000

Output of dmesg | grep usb
[17179578.008000] usbcore: registered new driver usbfs
[17179578.008000] usbcore: registered new driver hub
[17179579.828000] usb 2-4: new low speed USB device using ohci_hcd and address 2
[17179580.048000] usbcore: registered new driver hiddev
[17179580.060000] input: USB HID v1.10 Mouse [Kensington Kensington USB Mouse] o n usb-0000:00:13.1-4
[17179580.060000] usbcore: registered new driver usbhid
[17179580.060000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

Any ideas?

--bog

---

### Post by NorthCoast on 2006-11-11
I have a similar problem with a Targus wireless mouse.  Have you done the "sync" option of the mouse?  That does it for me although it isn't acceptable so I'll be sending this back.  I have to resync the mouse at every reboot.

Can you dual boot to Windoze and have the same problem?  My Targus acts the same under any OS which tells me it is a mouse or USB device problem.  My Logitech wireless doesn't have this problem.

---

### Post by webdr on 2006-11-29
I have this problem with all usb devices. When I first boot up, everything works fine. At some point during the day, all usb devices will just stop, all at once, and nothing seemingly related to immediately prior activity... in other words I can't find a way to consistently reproduce the failure.

Someone please take pitty on us and help...

---

### Post by webdr on 2006-11-29
Try this...
On startup... hit 'E' for EDIT
Then scroll down to kernel line hit 'E' again
at the end of the line type "noapic" "irqpoll" "pci=routeirq"

of course no quotes should be used.. then hit 'enter'
and last hit 'b' to boot with these options active.

If all goes well, then you'll need to add those options to your menu item to have it stick.

Hope this helps, It seems to have cured my usb failures.

-Racerx

---

