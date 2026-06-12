---
title: "Logitech USB microphone isn't working"
date: 2008-12-16
forum: Hardware
---

### Post by BuntuFirstTimer on 2008-12-16
I just bought a new Logitech USB microphone and I do not know how to install this into my Ubuntu Hardy Heron (sorry, I still use 8.04).

Any ideas?

---

### Post by Queue29 on 2008-12-16
I have to reboot every time I plug in my Logitech USB headphone/microphone. Then again, I have to reboot every time I plug something into the Audio jack as well. 

Run **lsusb** and see if you see it listed.

Edit:
I should also add that I have to go into the settings menu of whatever app I'm using and manually guess which device is the USB speakers as opposed to the built in ones of a laptop.

---

### Post by BuntuFirstTimer on 2008-12-18
Well I use a desktop btw.

Here's my lsusb:

Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000

---

### Post by BuntuFirstTimer on 2008-12-19
Bump

---

### Post by BuntuFirstTimer on 2008-12-19
I don't know much about Logitech hardware compatibility for Ubuntu.

[http://ubuntuforums.org/showthread.php?t=434169](http://ubuntuforums.org/showthread.php?t=434169)

This might be a 7.04 tip, is it applicable for 8.04?

---

### Post by BuntuFirstTimer on 2008-12-20
Forgive me for being rude. I'm going to bump this thread until somebody figure out what is wrong with my Logitech USB microphone.

---

### Post by BuntuFirstTimer on 2008-12-20
Does it have to do with **alsamixer** by the way?

---

### Post by BuntuFirstTimer on 2008-12-20
Bumping again.

---

