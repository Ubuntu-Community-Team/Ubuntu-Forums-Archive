---
title: "Razer Orochi bluetooth mouse issues"
date: 2010-07-05
forum: Hardware
---

### Post by ViperKnight on 2010-07-05
Hi guys,

I'm having some serious issues with trying to pair my Razer mouse.
I've installed blueman as the default bluetooth manager in 10.04 is pretty vague on errors.

Basically, my bluetooth adaptor can see my devices, but it keeps dropping in and out constantly.  I tried with my phone as well just to be sure.

Heres what dmesg spits out:
```
[ 1188.489683] input: Razer Orochi as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/bluetooth/hci0/hci0:42/input7
[ 1188.489835] generic-bluetooth 0005:1532:0014.0005: input,hidraw2: BLUETOOTH HID v5.01 Mouse [Razer Orochi] on 00:15:83:0B:13:C0 (NOTE: At this point the mouse works for a short time)
[ 1192.540076] usb 3-1: USB disconnect, address 5 (dies here)
[ 1192.540893] btusb_intr_complete: hci0 urb ffff880053e69480 failed to resubmit (19)
[ 1192.540911] btusb_bulk_complete: hci0 urb ffff880053e69f00 failed to resubmit (19)
[ 1192.540923] btusb_bulk_complete: hci0 urb ffff880053e69540 failed to resubmit (19)
[ 1192.542304] btusb_send_frame: hci0 urb ffff88006cecccc0 submission failed
[ 1193.070031] usb 3-1: new full speed USB device using uhci_hcd and address 6
[ 1193.246021] usb 3-1: configuration #1 chosen from 1 choice


```

I can get the mouse to work for anywhere between 10 seconds and a minute or so, then the bluetooth drops out.  Both the normal bluetooth icon and the blueman icons in the status bar disapear then reappear.  Then after 30 seconds or so the mouse will work again, then die again after another minute!

I've tried a number of things, resetting the dongle, using different usb ports.  Might try another dongle tomorrow when I've got some more time.  It was one of those $2 bluetooth dongles so it probably dodgy....but what puzzles me is it detects and pulls drivers correctly and everything.

Cheers

---

### Post by benmoran on 2010-07-05
I've also got a Razer Orochi, and it has worked perfectly in both Karmic and Lucid. I didn't use bluman though, just a vanilla install of KK and LL.

However, I couldn't get it to work using a different cheap dongle, so perhaps you're right about that being the problem.

---

### Post by gtr_golf on 2012-04-06
My Orochi works fine in 10.04 without blueman installed. Doesn't need to install any addition. Just use a bluetooth applet in a taskbar to manage pairing.

---

