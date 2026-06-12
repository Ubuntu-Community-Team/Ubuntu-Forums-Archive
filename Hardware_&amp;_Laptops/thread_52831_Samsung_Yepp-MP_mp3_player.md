---
title: "Samsung Yepp-MP mp3 player"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by f76 on 2005-07-29
Hi all!
 I tried connecting a Samsung Yepp-MP player. It wasnt automatically detected. Well maybe its not supposed to be. I tried the "mount" line but i wasnt able to identify the correct unit. 

I tried the "Grep vendor=" trick but i only saw some hex values.. (maybe im supposed to..) 

I looked around and it seems like Samsung needs encoded mp3:s. I want to use the player as a player and not a pure storage device...

Anyone managed to mount and play mp3:s on a Yepp-MP?

Thanx people...
 (ps please state if any print-outs would be of help)

---

### Post by jasmuz on 2005-07-29
Hello there:

With the yepp disconected, type in a terminal tail -f /var/log/messages
Now connect the Yepp, what does it say?..it must tell you if its doing SCSI emulation for the device.

Did you try with the following software?

sulu - File Mananger for Samsung Uproar and YEPP
yepp - Samsung YEPP MP3 loader

Hope this helps

---

### Post by f76 on 2005-07-29
result tail -f /var/log/messages:

Jul 29 20:38:06 localhost kernel: usb 2-2: new high speed USB device using ehci_hcd and address 3
Jul 29 20:38:12 localhost kernel: usb 2-2: khubd timed out on ep0in
Jul 29 20:38:12 localhost kernel: usb 2-2: new high speed USB device using ehci_hcd and address 4
Jul 29 20:38:17 localhost kernel: usb 2-2: khubd timed out on ep0in
Jul 29 20:38:17 localhost kernel: usb 2-2: new high speed USB device using ehci_hcd and address 5
Jul 29 20:38:22 localhost kernel: usb 2-2: khubd timed out on ep0in
Jul 29 20:38:22 localhost kernel: usb 2-2: new high speed USB device using ehci_hcd and address 6
Jul 29 20:38:27 localhost kernel: usb 2-2: khubd timed out on ep0in
Jul 29 20:38:28 localhost kernel: usb 2-2: new high speed USB device using ehci_hcd and address 7
Jul 29 20:38:33 localhost kernel: usb 2-2: khubd timed out on ep0in
Jul 29 20:38:33 localhost kernel: usb 2-2: new high speed USB device using ehci_hcd and address 8
Jul 29 20:38:38 localhost kernel: usb 2-2: khubd timed out on ep0in
Jul 29 20:38:38 localhost kernel: usb 2-2: new high speed USB device using ehci_hcd and address 9

---

### Post by jasmuz on 2005-07-30
It seems not recognized to the machine, are you plugging it to the usb ports in the back or in the front? (sometimes the front ones are hosted by a secondary hub and arent working properly)

---

### Post by f76 on 2005-08-02
In the back. I use the ports successfully with other hardware. Hmm. Good ting this is my sister inlaws mp3 player. if i ever get one it isnt going to be so hard to use on linux.

---

