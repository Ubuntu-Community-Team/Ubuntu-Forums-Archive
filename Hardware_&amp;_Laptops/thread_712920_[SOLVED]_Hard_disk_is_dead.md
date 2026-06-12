---
title: "[SOLVED] Hard disk is dead"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by borobudur on 2008-03-02
I need some advise! My external USB hard drive just died :( (Maxtor)

There are still data on it which I wouldn't like to lose. What's the cheapest way to make a data recovery?

Thanks!

---

### Post by jocko on 2008-03-02
I once had an external hard drive die on me.
I read somewhere that inside the shell is a normal ata hard drive and an ide-->USB converter. A very common problem with some external drives is that the converter breaks. So I opened it up, took out the hard drive and connected it as a normal internal drive in my computer. Problem solved.
Worth an attempt, unless you have a warranty on the drive, in which case you should bring it back to the store and have them fix it for you.

---

### Post by oldsoundguy on 2008-03-02
Before you go mucking around .. unplug the drive and re-boot.  Then shut down.  Plug the drive back in and boot up.  AND change out the USB cable .. using another input on the computer if available. (also, if it is powered externally and has no pilot lite to indicate it is plugged in, re check the wall wart.  I have had several die recently (my stuff is ALL plugged into UPS units .. NO SURGES!)

ALWAYS look for a mechanical fault FIRST before you blame the software.

---

### Post by borobudur on 2008-03-02
Definitely no software problem. Unplugging from power brings no sign of life. Totally dead, no move. And no warranty  :(

Jocko how did you do this to connect it as a normal hard drive? I don't think you can use a IDE cable, can't you?

---

### Post by oldsoundguy on 2008-03-02
I have USB enclosures (Kingwin) that actually use IDE drives.  Removing from the enclosure, putting a jumper on as slave and putting it into the computer itself (setting the C drive as master), MAY get it to spin up .. but no guaranty.  Then there is the "put it in a sealed  baggie and into the freezer .. then hook it up and get your data off of it QUICKLY" trick.  That trick is about 50% effective.

---

### Post by jocko on 2008-03-02
> **borobudur said:**
> Definitely no software problem. Unplugging from power brings no sign of life. Totally dead, no move. And no warranty  :(

Jocko how did you do this to connect it as a normal hard drive? I don't think you can use a IDE cable, can't you?

yep, a normal ide cable. Just open up the cover of the external hard drive and you'll see that there's a normal ide drive inside. At least that was the case for mine (iomega). Disconnect the ide-->usb converter from the ide slot on the drive and connect it to a normal ide cable connected to your mother board. And connect a power connector from your power supply plus check that the jumper setting is correct (master/slave or cable select)

---

### Post by borobudur on 2008-03-07
So simple! I took the IDE HD 3.5'' out of its box and installed it in the desktop: voilà, ça marche!
Thanks for your help guys.

---

