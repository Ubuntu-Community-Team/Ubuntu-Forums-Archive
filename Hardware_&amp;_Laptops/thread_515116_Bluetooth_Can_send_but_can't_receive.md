---
title: "Bluetooth: Can send but can't receive"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by ElliottMarlow on 2007-08-01
Using Bluetooth OBEX Client, I can send files to my Motorola v557, however, I cannot send files from my phone to my laptop. Of course, when I search for devices with my phone, it finds my laptop, but when I attempt to connect, it simply says "Service Not Supported." 

Any ideas?

---

### Post by jet2230 on 2007-08-01
i had this problem as well, i found the fix somewhere in the ubuntu forums. install this: sudo apt-get install gnome-obex-server

there should be a 'Bluetooth File Sharing' application in Applications > Accessories > Bluetooth File Sharing - run this and you can save files from any bluetooth hand held device to your bluetooth pc/laptop

---

### Post by ElliottMarlow on 2007-08-02
> **jet2230 said:**
> i had this problem as well, i found the fix somewhere in the ubuntu forums. install this: sudo apt-get install gnome-obex-server

there should be a 'Bluetooth File Sharing' application in Applications > Accessories > Bluetooth File Sharing - run this and you can save files from any bluetooth hand held device to your bluetooth pc/laptop

I tried that command, but the terminal told me I needed to first run: "sudo apt-get install gnome-bluetooth" which I did, but still couldn't install gnome-obex-server. After a reboot, gnome-bluetooth ran at start-up. My phone connected perfectly and sent/received like a charm. I guess maybe the obex-server is included with gnome-bluetooth? Anyway, thanks for the help!

---

### Post by jet2230 on 2007-08-02
try this: sudo apt-get install gnome-bluetooth bluez-gnome python-bluez python-libbtctl bluez-utils bluez-gnome

that file sharing option under applications > accessories should appear after that.

---

### Post by jrevillini on 2007-12-29
Hey, thanks!  This worked awesome for me.

---

