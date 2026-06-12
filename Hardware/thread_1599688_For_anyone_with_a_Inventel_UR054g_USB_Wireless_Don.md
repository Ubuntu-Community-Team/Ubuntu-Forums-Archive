---
title: "For anyone with a Inventel UR054g USB Wireless Dongle..."
date: 2010-10-18
forum: Hardware
---

### Post by arashi256 on 2010-10-18
For anyone trying to get a Inventel UR054g USB wireless dongle (the ones supplied by Orange/Wanadoo) working with Ubuntu 10.04 or higher: -

- You need either another working Internet connection or another Ubuntu machine. 

- Go into Synaptic package manager and search for "linux-firmware-nonfree", highlight it and select File->Create Download Script.

- Open the script it creates and run the wget command to download the "linux-firmware-nonfree.deb" file. Stick it on a USB stick or something and transfer it to the non-working machine. 

- Double click on the .deb file and install the drivers. Disconnect/reconnect the USB dongle. 

- Done, you now have wireless :)

Hope this helps somebody, I was stuck on Ubuntu 9.10 until last night trying to figure this one as 10.04+ didn't working with the USB wireless.

---

