---
title: "Fujitsu Stylistic St4110P touchscreen driver help requested"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by TheGuv on 2007-07-06
Hi all,

I'm struggling to find the correct Xorg driver (or indeed any driver) for the PASSIVE touchscreen on my Stylistic ST4110P (which the 'P' indicates). This is _not_ the active digitiser (which I think uses the WACOM) driver) but a passive resistive touchscreen.

I've no idea who the manufacturer of the touchscreen is, but I have found the serial port it uses (at port 0x220) and it was working find in Win2k shortly before I nuked it.

Any clues as to what driver I need, or a pointer to some kind of tool to find out would be great :-)

'guv.

---

### Post by osarusan on 2007-07-07
Hi, I have a Fujitsu Stylistic ST5112, so not the same model. But I did get my tablet screen to work. Here's a link to how I did it: [http://ubuntuforums.org/showthread.php?p=2979506#post2979506](http://ubuntuforums.org/showthread.php?p=2979506#post2979506)

I'll update that thread as I go, in case anyone else uses Ubuntu on the same tablet model. Hopefully it will be helpful to some, as I've seen many people trying to use Tablets on Ubuntu, but not many people are able to answer their questions.

Good luck! Let me know if that works.

---

### Post by mcscratch on 2007-07-10
I just got mine up and running right now.  Most of the posts seem to relate to the active model, which you mentioned you don't have.  I followed most of the instructions here

[http://ubuntuforums.org/showthread.php?t=456110&highlight=fujitsu+stylistic](http://ubuntuforums.org/showthread.php?t=456110&highlight=fujitsu+stylistic)

and substituted ttyS0 instead of ttyS1, and used:  /dev/ttyS0 port 0x0220 irq 4 autoconfigure, 
instead of: dev/ttyS1 uart 16450 port 0xfd68 irq 5 low_latency baud_base 115200 spd_normal skip_test

under /etc/serial.conf.  If any of that helps.  But it does work, and pretty well for that matter.

---

### Post by nashley on 2008-05-16
For an update, I got my Stylistic 4110P working with Hardy 8.0.4 with details following from [http://ubuntuforums.org/showthread.php?t=763380]("http://ubuntuforums.org/showthread.php?t=763380") 

Needed to patch fpit driver; fixed binary posted in that thread.

---

