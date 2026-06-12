---
title: "Mp3 player not detected"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by Andrej_BB on 2007-03-30
I have a problem with my USB mp3 player.
In edgy it has been automatically detected and automounted, in feisty beta it's simply not detected.

Other USB related hardware works ( USB camera, USB drive ).

What should i do ?

---

### Post by teaker1s on 2007-04-02
possibly It's just not mounting,
```
lsusb
``` see if we can see it
```
fdisk -l 
``` find out what it's called

you could try mounting it manually or you could add "disk mounter" to your desktop panel by right click on panel and select add to panel

---

### Post by Andrej_BB on 2007-04-17
The output of lsusb is not useful at all

```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 004: ID 03f0:020c Hewlett-Packard Multimedia Keyboard
Bus 001 Device 003: ID 03f0:010c Hewlett-Packard Multimedia Keyboard Hub
Bus 001 Device 001: ID 0000:0000  

```

So there is no sign of my mp3 player

When i do fdisk -l it only shows hda hdc - my harddrives, no sign of mp3 player.
What should i do ?
Someone suggested me to upgrade firmware, but i cannot do that, cause i cannot mount it.

---

