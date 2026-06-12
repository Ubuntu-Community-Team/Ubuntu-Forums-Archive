---
title: "Connecting a Nokia 6265i via USB in Edgy"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by LinLenLap on 2006-10-30
Hi all,

I'm trying to connect my brothers Nokia 6265i cell phone to my Ubuntu Laptop running Excellent Eft (2.6.17-10-generic). At this point, I don't think my computer is even seeing the phone. 

With cable (CA-53) & phone plugged in lsusb returns:
LinLenLap:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 1241:1166 Belkin 
Bus 001 Device 001: ID 0000:0000  

Unplugging my mouse gets rid of device 004.

Nothing shows up under /mnt /dev /media that is the phone or could be the phone.

Running tail -n 20 /var/log/messages while cable is unplugged, then plugging in cable already connected to the phone returns:

LinLenLap:~$ tail -n 20 /var/log/messages
Oct 30 22:35:57 LinLenLap kernel: [17180737.688000] input: HID 1241:1166 as /class/input/input3
Oct 30 22:35:57 LinLenLap kernel: [17180737.688000] input: USB HID v1.00 Mouse [HID 1241:1166] on usb-0000:00:1d.0-1
Oct 30 22:36:30 LinLenLap kernel: [17180770.424000] usb 1-1: USB disconnect, address 5
Oct 30 22:36:37 LinLenLap kernel: [17180777.272000] usb 1-1: new low speed USB device using uhci_hcd and address 6
Oct 30 22:36:37 LinLenLap kernel: [17180777.460000] usb 1-1: configuration #1 chosen from 1 choice
Oct 30 22:36:37 LinLenLap kernel: [17180777.504000] input: HID 1241:1166 as /class/input/input4
Oct 30 22:36:37 LinLenLap kernel: [17180777.504000] input: USB HID v1.00 Mouse [HID 1241:1166] on usb-0000:00:1d.0-1
Oct 30 22:36:58 LinLenLap kernel: [17180798.944000] usb 3-1: new full speed USB device using uhci_hcd and address 2
Oct 30 22:36:59 LinLenLap kernel: [17180799.504000] usb 3-1: new full speed USB device using uhci_hcd and address 3
Oct 30 22:36:59 LinLenLap kernel: [17180800.064000] usb 3-1: new full speed USB device using uhci_hcd and address 4
Oct 30 22:37:00 LinLenLap kernel: [17180800.584000] usb 3-1: new full speed USB device using uhci_hcd and address 5
Oct 30 22:38:15 LinLenLap kernel: [17180876.004000] printk: 1 messages suppressed.
Oct 30 22:38:29 LinLenLap kernel: [17180889.412000] usb 3-1: new full speed USB device using uhci_hcd and address 6
Oct 30 22:38:29 LinLenLap kernel: [17180889.972000] usb 3-1: new full speed USB device using uhci_hcd and address 7
Oct 30 22:38:30 LinLenLap kernel: [17180890.532000] usb 3-1: new full speed USB device using uhci_hcd and address 8
Oct 30 22:38:30 LinLenLap kernel: [17180891.052000] usb 3-1: new full speed USB device using uhci_hcd and address 9
Oct 30 22:39:02 LinLenLap kernel: [17180922.676000] usb 3-1: new full speed USB device using uhci_hcd and address 10
Oct 30 22:39:03 LinLenLap kernel: [17180923.236000] usb 3-1: new full speed USB device using uhci_hcd and address 11
Oct 30 22:39:03 LinLenLap kernel: [17180923.872000] usb 3-1: new full speed USB device using uhci_hcd and address 12
Oct 30 22:39:04 LinLenLap kernel: [17180924.392000] usb 3-1: new full speed USB device using uhci_hcd and address 13

You can probably see where I unplugged my mouse there and plugged it back in. I should add that under Windows XP the phone is recognized and setup (no problems in devmgmt.msc), although it is never actually able to connect to the phone via any software suite.

I'm stumped at this point. Any help is appreciated.

Best,

LLL

---

### Post by LinLenLap on 2006-11-06
Hey, I'm still looking for a solution. Any help is appreciated, even if it's not a total fix.

Best,

LLL.

ps. Yes...bump, bump.

---

### Post by richardq on 2007-03-26
I just bought this phone. I am thinking about buying a mini-SD card and the USB cable reader for that card rather than the USB data kit. I'm only interested in moving the pictures and movies off of it, not necessarily connecting it directly. Unless of course the problem has been solved. Did you ever end up solving it?

---

### Post by [Alsharifi] on 2007-09-02
yea i have the same problem,when i plug it in USB.ubuntu see's it.i can see it in my home folder list

but i cant mount it..it says cant read super block

---

### Post by thinkdez on 2007-09-03
I don't use a cable to connect to my phone but use the bluetooth connection.  It works perfectly and i can transfer data back and forth between my PC and the phone.  It may not be a cable connection but it does work.  I will see what I can do with my DKU cable later this evening.

---

