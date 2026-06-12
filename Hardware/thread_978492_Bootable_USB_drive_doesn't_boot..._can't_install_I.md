---
title: "Bootable USB drive doesn't boot... can't install Intrepid"
date: 2008-11-11
forum: Hardware
---

### Post by yeehi on 2008-11-11
I have tried some tutorials but I have run into problems launching the Ubuntu installation.

I have a wired network connection into the eeePC. I have a USB pen drive. I downloaded the 8.10 alternate ISO of Intrepid Ibex for i386. I tried creating a bootable USB key using the HP utilitiy and also the UnetBootin one:

[http://ubuntu-8-1.blogspot.com/2008/07/create-bootable-usb-pen-with-unetbootin.html](http://ubuntu-8-1.blogspot.com/2008/07/create-bootable-usb-pen-with-unetbootin.html)

Both applications seemed to work well and did what they wanted to do to my USB key; however, during the bootup the eeePC never enters the Ubuntu installation dialogue. The closest I get is the light on the USB key flashing  for a long time, as though data is being read.

What might be the problem?

Thank you for your interest! :)

---

### Post by C.S.Cameron on 2008-11-11
Have you set your flash drive as first drive in boot drive priority in BIOS?

---

### Post by mylo9000 on 2008-11-11
I'm not sure if I fully understand.
you got your flash drive setup ok but it won't boot when plugged in to you eeepc?

have you tried pressing the <esc> key when the the eee starts up (shows gray eee bios screen)?

pressing <esc> at the bios screen should give you a one time boot select menu.

you should be able to select you usb pendrive from that menu.

if you select the usb pendrive and it still doesn't boot then you may have a messed up pendrive.

---

### Post by yeehi on 2008-11-11
Thank you people! It was two problems:

1) not holding down the escape key
2) the pen drive wasn't properly configured

Now I have the installation going, however I can't reach a functioning mirror of the Ubuntu archive, for some strange reason.

---

### Post by mylo9000 on 2008-12-18
i too have been getting intermittent connections to the Ubuntu Archives. a fix i keep going with is to <alt><f2>:
```
gksudo gedit /etc/apt/sources.list
```
then i use <ctrl><h> to find and replace
change:
```
us.archive.ubuntu.com
```
to:
```
archive.ubuntu.com
```
save > close
Opend a terminal:
```
sudo apt-get update
```
then run your update manager and all should be fast and shiny. :biggrin:

i used to use the ca.archive.ubuntu.com but that is crazy slow now so if i go directly to the main archive everything is fast and good.... so far that is.

---

