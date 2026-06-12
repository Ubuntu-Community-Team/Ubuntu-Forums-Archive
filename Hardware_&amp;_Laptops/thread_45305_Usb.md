---
title: "Usb"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by musicman2059 on 2005-06-29
I've been trying to figure out what in god's name my USB ports are listed as under /dev.  So far I haven't found any signs of an sda, uba, usb, ttyUSB, or anything related.

My device manager shows that my USB controller is there under the device name "usbhug'. 

What the heck am I supposed to do?

---

### Post by alastair on 2005-06-29
I wouldn't worry about the actual devices - they should get created for user use when a USB device "appears" e.g. when you plug in a disk etc. i.e. check the log (/var/log/syslog) and a /dev/sda1 device is created (for instance).

What problem are you having exactly?

---

### Post by musicman2059 on 2005-06-30
[QUOTE=alastair]I wouldn't worry about the actual devices - they should get created for user use when a USB device "appears" e.g. when you plug in a disk etc. i.e. check the log (/var/log/syslog) and a /dev/sda1 device is created (for instance).

What problem are you having exactly?[/QUOTE]
 Well, the actual problem is that I have a PalmOne handheld that I'm trying to synchronize via pilot-link to jpilot.  I've downloaded all the required packages to do so AFAIK (pilot-link, libpisock8, jpilot, all acquired from Ubuntu's repositories) but so far all my attempts have failed because I can't figure out what neither the device nor the port is.  I will take a look at my logs, though.  I took a look at /dev with it plugged in, though, but I haven't seen an sda1 or whatever added.  ](*,) 

Is it also somewhat possible that a handheld could be considered by the system as more of a USB drive, and may have the same problems?

---

### Post by alastair on 2005-06-30
You really need to check the logs. The best thing to do is probably :

Open a shell and :

  tail -f /var/log/syslog

Then plug whatever in and see what messages appear. I think plenty people sync Palm's etc. with Linux.

---

### Post by musicman2059 on 2005-07-01
I checked my syslogs, but so far there is nothing regarding a USB device being plugged or unplugged.  I tried both plugging/unplugging just the handheld and plugging/unplugging both the handheld and the hotsync cable.  (My model uses a cable, not a cradle.)

lsusb seems to list something, too, but I'm not sure if it's listing a port or a device, because it's there whether or not anything is inserted.  Maybe only one of my ports are working?

---

### Post by musicman2059 on 2005-07-06
Bah, I was able to figure this one out.  I followed the instructions in ubuntuguide and also discovered that I have to open the connection between the handheld and the system FIRST (ie. Starting the hotsync) before telling jpilot to sync.

---

