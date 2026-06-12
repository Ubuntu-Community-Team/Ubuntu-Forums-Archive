---
title: "sata wont boot now ide is plugged in"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by stinger30au on 2009-08-29
i believe this fault will be easy to fix, but i dont know how to do it

i have a desktop pc with a 160 gig sata drive in it
i have setup 9.04 on it and it will boot from the sata drive and run and do everyhting it needs to just fine


untill i plug in a ide hard drive

now what happens is grub tried to start and gives error 22


i reckon it has something to do with it trying to boot from hd 0,0
it says its booting from that device on start up

i think that hd 0,0 is the ide hdd and thats why it is failing

anyone with any ideas how to fix so the ide and sata drive live in harmoney and it boots from the sata drive?
if i unplug the ide drive and leave the sata, everything is just fine
thanks

---

### Post by prshah on 2009-08-29
> **stinger30au said:**
> i think that hd 0,0 is the ide hdd and thats why it is failing

You can find an option in most BIOSes to allow SATA HDDs to take precedence over IDE.

The exact option varies from BIOS to BIOS, so I cannot be more specific. 

If you feel you have found the correct option, but want confirmation, post a (camera) screenshot of the relevant BIOS screen.

To enter the BIOS (aka CMOS setup), during startup (but before GRUB) you have to press (usually) Del =OR= F10 =OR= F12 (or look for a message on the screen during bootup).

---

### Post by stinger30au on 2009-08-29
i have been hunting and i have found this

[http://ubuntuforums.org/showthread.php?t=1036962](http://ubuntuforums.org/showthread.php?t=1036962)

im going to get around this by purchasing an [ide 2 sata adaptor and fix it ]("http://www.jaycar.com.au/productView.asp?ID=XC4841&keywords=ide+sata&form=KEYWORD")

---

### Post by stinger30au on 2009-08-29
bought and fitted ide 2 sata adaptor, all is well again

boots nicely off the sata hdd now

---

