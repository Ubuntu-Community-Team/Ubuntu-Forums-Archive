---
title: "Webcam Not working... please help! (driver issue?)"
date: 2009-12-31
forum: Hardware
---

### Post by jacksonfarley on 2009-12-31
My Dell Inspiron Mini has a built in webcam. It works in Windows, but in Linux, there is no 'preview'. I can take a picture, and it will turn out fine, but the screen is blank. I think I might need a driver for it? I did 'lsusb', and found the vendor id and product id for my webcam.

Bus 001 Device 004: ID 064e:a129 Suyin Corp. 

If someone could direct my to where I can get a driver for that (if thats what I need), thatd be great.

If something else needs to be done, let me know.

thanks :)

---

### Post by jacksonfarley on 2009-12-31
anyone? pleasee?

---

### Post by ogromano on 2010-01-01
Hi...

I had a similar thing happen to me. My webcam worked fine on 8.04 Hardy, and after installing Karmic it worked for a couple of days and suddenly stopped working the day before yesterday...

This morning I looked at this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459586") report and was reading it when I decided to check my webcam again using the Skype test button and it was working fine again... I don't have a solution for you, but maybe it has something to do with how the webcam is handled at shutdown or Suspend that maybe leaves it in tilt when you turn the comp on again... 

Believe me I am complete linux noobie.. but I saw that noone answered you and I figured I'd try to give back a little of all the help I've received here.

Hope it works. Cya.

---

