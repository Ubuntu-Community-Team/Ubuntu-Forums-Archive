---
title: "USB ports broken?"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by JMO707 on 2006-06-10
I got this problem since Dapper.

My webcam doesnt work, nor my digital camera.
I was able to make them work on Breezy, but no clues here.

With the digital camera (Canon Powershot A510) I used to "plug-n-play". Some thing in Gnome detect it and thats it.
With the webcam (¿?) I only had to follow this guide: [http://www.ubuntuforums.org/showthread.php?t=75284&highlight=spca5xx]("http://www.ubuntuforums.org/showthread.php?t=75284&highlight=spca5xx")
And it worked.

Now it seems that the only two things that I got in USB ports arent being detected at all :(
Tried the well-mentioned:

*sudo tail -f /var/log/messages*

But I get no messages. May be the kernel?, I use a 2.6.16-ck12, not the Ubuntu one.

Well. Im pretty desperated. Please, help me.

Thanks.

---

### Post by reech on 2006-06-10
Are the ports usb 1.1 or 2?

PLs post the output of :

* dmesg | grep usb*

---

### Post by JMO707 on 2006-06-10
They are 2.0

[I]usbcore: registered new driver usbfs
usbcore: registered new driver hub
usbmon: debugfs is not available
usb usb1: configuration #1 chosen from 1 choice
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
usbcore: registered new driver usb-storage
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver[/I]

---

### Post by JMO707 on 2006-06-11
Please? :(

---

### Post by steevc on 2006-06-11
I'm also having USB problems. I have a USB 2.0 card that I added whilst using Breezy and it was working fine. It has worked under Dapper as my external hard drive is plugged into it and has worked, but currently I am not seeing any devices plugged into that card (disk, camera and scanner). lsusb shows nothing.

What can I check?

UPDATE 28/08/06: My problem seems to have been resolved by re-seating the USB PCI card. Looks like it was a bad connection.

---

### Post by nexu56 on 2006-07-08
steevc, I had the same problem. Turned out to be a usb bluetooth driver I'd installed. Removed the files from /lib/firmware and restarted and my usb devices started working again.

---

### Post by mchojrin on 2006-07-11
I'm also having problems with a usb digital camera. I have just installed XUbuntu 6.06 and when I plug in my camera nothing happens. Where should I see the files from the camera?

---

### Post by TheCaptain200x on 2006-07-11
I have the same problem. I am using an Acer Travelmate8204WLMI and Ubuntu Dapper 6.0.6. I just did a reinstall over just my / directory because I messed it up. Then I ran all the updates so I'm running the newest kernel

When I booted it back up, my USB ports would not detect a thing. 
I removed all my devices a while ago and just gave up. I figured it would work later. But I just ran lsusb and I get

Bus 005 Device 002: ID 046d:0892 Logitech, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

Despite the fact that there are no devices plugged in, it still shows my logi keyboard mouse set as being inside. Eerie. When I plug it in, it of course doesn't work.

dmesg | grep usb 

reveals

[17179573.400000] usbcore: registered new driver usbfs
[17179573.400000] usbcore: registered new driver hub
[17179574.316000] usb 5-8: new high speed USB device using ehci_hcd and address 2

Once again, nothing is plugged in. Is there any way to purge it and get my USB to recognise devices?

Thanks.

---

### Post by wcbaker on 2006-07-17
I am getting problems with my Thinkpad T42 as well. I can plug in the mouse and it powers on, but doesn't function. When I plug in my external hard drive, it doesn't mount. When I just plug in my USB hub, nothing happens...

Hopefully someone figures this out.

Edit: Actually it turns out, when I plug my mouse in, the light comes on for a second and then goes right back off.

---

### Post by Belyel on 2006-08-25
> **TheCaptain200x said:**
> I have the same problem. I am using an Acer Travelmate8204WLMI and Ubuntu Dapper 6.0.6. I just did a reinstall over just my / directory because I messed it up. Then I ran all the updates so I'm running the newest kernel

When I booted it back up, my USB ports would not detect a thing. 
I removed all my devices a while ago and just gave up. I figured it would work later. But I just ran lsusb and I get

Bus 005 Device 002: ID 046d:0892 Logitech, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

Despite the fact that there are no devices plugged in, it still shows my logi keyboard mouse set as being inside. Eerie. When I plug it in, it of course doesn't work.

dmesg | grep usb 

reveals

[17179573.400000] usbcore: registered new driver usbfs
[17179573.400000] usbcore: registered new driver hub
[17179574.316000] usb 5-8: new high speed USB device using ehci_hcd and address 2

Once again, nothing is plugged in. Is there any way to purge it and get my USB to recognise devices?

Thanks.

Hi 'cap, I'm running the same laptop with dapper and have no problems with my usb ports.  The top device that's recognized isn't a logitech kb/mouse, but is the video camera built in to the system.  I'm in the process of trying to get it to work in the ol Ubuntu, and when I figure it out, I'll post a how-to.

---

