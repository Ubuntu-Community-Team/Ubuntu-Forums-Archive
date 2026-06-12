---
title: "This Hard Drive Is Driving Me Mad!!!!!!!!!!!!"
date: 2008-05-23
forum: Hardware
---

### Post by jamieh on 2008-05-23
A pin is missing!
Can this be fixed?
Thanks for all your help!

EDIT:
I pulled up the pin with pliers, but that made no difference!

PLEASE help me!!

---

### Post by sergim on 2008-05-23
well it seems to me that you have skipped the detection of hard drives.
Try not doing it and let BIOS detect all drives.
Or use ubuntu live cd to check your hard drives

---

### Post by Yellow Pasque on 2008-05-23
According to the IDE pin-out, it is normal for pin 21 to not be connected. The "missing" pin is the key (so you don't plug it in upside down)
[http://pinouts.ws/ata-ide-pinout.html](http://pinouts.ws/ata-ide-pinout.html)

Sounds like a bad disk.

---

### Post by sergim on 2008-05-23
oh sorry didn't notice that image
...and no, it's not normal
It should be like this:
[http://en.wikipedia.org/wiki/Image:ATA_on_mainboard.jpg]("http://en.wikipedia.org/wiki/Image:ATA_on_mainboard.jpg")

---

### Post by Yellow Pasque on 2008-05-23
That pin is not used
```
21  	n/c  	Not connected
```

---

### Post by Steve413z on 2008-05-23
try spinrite
[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

it really does work,  hopefully there is nothing wrong with the drive, and it's just not mounting properly... try using a ubuntu live CD to look through the drive

---

### Post by Steve413z on 2008-05-23
actually, that pin does do something, i believe thats pin 17, the one thats kinda too short... i think it got messed up when you plugged in the cable, i think if you get some tweezers, you can pull that pin out gently and it will work normal again....  i don't think it would be tooo expensive to have data recovered from that drive professionally if thats the problem

---

### Post by Yellow Pasque on 2008-05-23
> **Steve413z said:**
> actually, that pin does do something, i believe thats pin 17

No, it's pin 21 in the diagram I linked to. Remember, the image is the connection at the hard disk and the diagram is the cable. The pin in question is to the center-left of the key on the hard disk, so it will be the center-right pin on the diagram, which is pin 21.

---

### Post by Steve413z on 2008-05-23
> **Temüjin said:**
> No, it's pin 21 in the diagram I linked to. Remember, the image is the connection at the hard disk and the diagram is the cable. The pin in question is to the center-left of the key on the hard disk, so it will be the center-right pin on the diagram, which is pin 21.

i'm not sure, but i think one of us has the connector reversed the wrong way

---

### Post by Steve413z on 2008-05-23
check all your BIOS settings....

i know some dell boxes do this really weird thing...
if you disconnect a hard drive, and connect it later, you need to reactivate the drive in BIOS...

---

