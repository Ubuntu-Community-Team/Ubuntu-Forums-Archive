---
title: "Bluetooth mouse"
date: 2014-04-07
forum: Hardware
---

### Post by AussieGuy on 2014-04-07
I have never used bluetooth before.  My laptop (an old, but perfectly working Thinkpad T500) supports bluetooth; indeed the bluetooth icon light is glowing steadily.  However, this appears to be a BIOS/hardware thing, I can't get a software communication with it.

For example: 

"sudo hciconfig hci0 down"

just hangs,  and the command

"bluetoothd -d -n"

produces various messages including

  bluetoothd[16150]: Bluetooth daemon 4.98
  bluetoothd[16150]: src/main.c:parse_config() Key file does not have key 'DeviceID'
  D-Bus setup failed: Connection ":1.55" is not allowed to own the service "org.bluez" due to security policies in the configuration file
  bluetoothd[16150]: Unable to get on D-Bus

which I find very mystifying.  I've been hunting about the web, trying various things, but I can't seem to be able to manage my bluetooth settings.  If I run

"sudo bluetooth-wizard"

then it searches for devices with no success (the bluetooth mouse is turned on, with new batteries, about 3 inches from the laptop).

Any advice would be very gratefully received!

Thanks.

---

### Post by AussieGuy on 2014-04-07
Oops - got it working!  My bad - I just needed to keep pressing the bottom bluetooth button on the mouse to make it discoverable.  

Please ignore this post, and hit me over the head in effigy.

Ahem.  I'll go and crawl back under my rock now.

---

### Post by mörgæs on 2014-04-07
First please mark the thread 'solved'.

---

