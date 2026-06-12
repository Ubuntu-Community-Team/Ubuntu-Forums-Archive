---
title: "Plantronics Headset"
date: 2008-09-09
forum: Hardware
---

### Post by StriderK on 2008-09-09
I recently bought a Plantronics Audio 300 headset (the "Gaming" version). I knew immediately that I needed to unmute my headphone/mic sound. Unmuted everything in alsamixer and turned the volume up fully. The headphones works fine; I can hear sounds with no difficult, but I can not get the mix to work.

I messed around with sound recorder trying to record anything and all I ever get is this high pitched screeching sound. 

It's a standard headset that plugs directly into the soundcard (not bluetooth or USB).

---

### Post by StriderK on 2008-09-09
Update: The mic seems to be "working," but it's only making a static noise now.

---

### Post by StriderK on 2008-09-10
Surely someone knows something about this?

---

### Post by Crafty Kisses on 2008-09-10
I'd like to see the results of this command:
```
lsusb
```

---

### Post by StriderK on 2008-09-10
> Bus 008 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 0461:4d42 Primax Electronics, Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 152e:2507 LG (HLDS) 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05dc:a575 Lexar Media, Inc. 
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  


Thanks for any help you can offer.

---

### Post by StriderK on 2008-09-17
Still having problems with this headset.

---

### Post by StriderK on 2008-10-17
I played around with this some more to the same results. Everything in both alsa-mixer and pulseaudio is turned up and unmuted. The headphones play fine, but the microphone only puts out a static noise (not even any audible voice). With the Pulse audio Volume Meter (recording) it is constantly showing some type of activity even when there is nothing going on (and the mic is off).

---

