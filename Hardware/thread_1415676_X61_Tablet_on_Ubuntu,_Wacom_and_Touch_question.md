---
title: "X61 Tablet on Ubuntu, Wacom and Touch question"
date: 2010-02-25
forum: Hardware
---

### Post by ais4me on 2010-02-25
Hello, I've installed Ubuntu 9.10 on my Lenovo X61T and am having trouble with the touchscreen configuration,
The touchscreen works but is not calibrated right, I don't know where I can calibrate it, I checked some sites, one of them recommended TouchCal, which didn't work for me, ./touchcal e /dev/ttyS0 didn't respond to the touch ( ./touchcal m /dev/ttyS0 gave me a buffer overflow)
I'm sure /dev/ttyS0 is the touchscreen device.

I need some help for calibrating it.

plus I don't know how to activate the right click on the wacom pen, I tried wacomcpl but it doesn't give me anything (no devices in the list)

I saw on some sites I had to make changes in the xorg.conf, but in Ubuntu 9.10 I don't find the xorg.conf in /etc/X11/

Could someone help me calibrating my touchscreen & enable my right click on my wacom pen ?

Thanks !

---

### Post by Favux on 2010-02-25
Hi ais4me,

Welcome to Ubuntu forums!

You can see why wacomcpl isn't working by entering in a terminal:
```
xinput -list
```
and see what X server is calling your tablet.  If:
```
xsetwacom list
```
is blank, that's why wacomcpl isnt working.

You could try one of the two modified .fdi's attached to the bottom of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Read "Jaunty (9.04) & Karmic (9.10)" near the top for an explanation.  Instructions for installing the .fdi's are in Section 2 b).  Instructions for setting up wacomcpl in Section 3.

Hope this helps.

---

### Post by ais4me on 2010-03-03
Thank you for your reply, I managed to have the wacom pen in wacomcpl with the fdi's from your link. I can now configure the right click.

But I still didn't find anything on calibrating the touchscreen...
anyone has a clue ?

Thanks

---

