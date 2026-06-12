---
title: "Can't connect usb asus monitor to ubuntu 18.04"
date: 2019-08-28
forum: Hardware
---

### Post by pedrotainha on 2019-08-28
HI, i'm new here and i'm not very confortable with linux setup's to handle new hardware.
I'm trying to connect a usb monitor to my ubuntu laptop:


Monitor:
Monitor ASUS 15.6 Wide (16:9) 1920x1080 14 ms USB3.0 - MB169B

Modelo:
Lenovo thinkPad X1 Carbon 6th
Memory: 16GB
processor: intel Core i7-8550U CPU 1.80 x 8
graphics: Intel UHD Graphics 620

OS:
Ubuntu 18.04.3 LTS
gnome: 3.28.2
64-bit

There is a displayLink driver for ubuntu but something does not work well: https://www.displaylink.com/downloads/ubuntu[/URL]
I have found a lot of post saying how to solve this issue but i wasn't successful.
I'm from Portugal. I don't even mind to pay someone and try to setup this in Person in Lisbon

---

### Post by CatKiller on 2019-08-28
> **pedrotainha said:**
> There is a displayLink driver for ubuntu but something does not work well: 

That is not very helpful. What happened? Did you get an error message of some kind?

According to [the information I found](https://askubuntu.com/a/995450) from a quick search, you'll need to install the *dkms* package and turn off Secure Boot in the BIOS settings. That's also what [DisplayLink instructions](https://support.displaylink.com/knowledgebase/articles/684649) say.

---

### Post by pedrotainha on 2019-09-12
I did all of that and simply there is no image in usb monitor and there isn't also second monitor identified in the display settings.

---

### Post by Autodave on 2019-09-12
Just outta curiosity: have you tried another USB port?

---

