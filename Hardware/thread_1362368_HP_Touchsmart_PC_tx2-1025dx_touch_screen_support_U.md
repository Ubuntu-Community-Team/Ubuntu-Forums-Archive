---
title: "HP Touchsmart PC tx2-1025dx touch screen support Ubuntu 9.10"
date: 2009-12-23
forum: Hardware
---

### Post by chris tallman on 2009-12-23
I just recently switched over to Ubuntu from Vista and am very impressed. I have gotten everything to work except the touchscreen. The touchscreen can use either a finger or a digitizer. Is there anyone who knows were a driver for this may be. I have the windows drivers on a driver restore dvd that I got from HP if there is any way to get the windows driver to work in Ubuntu, like the Ndiswrapper works for the wireless windows drivers. Please, if you guys fail me, I'll be forced to switch back to Vista, and I know nobody wants that. Thanks =]

---

### Post by Ayuthia on 2009-12-23
You can start with this thread:
[http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492)

It is for the tx2z laptops and the Dell XT2 and it should work fine for your laptop because it is the same as mine.

---

### Post by chris tallman on 2009-12-23
Wow thats confusing
I just did everything [http://linuxfans.keryxproject.org/?page_id=23](http://linuxfans.keryxproject.org/?page_id=23) told me to do
Its still not working

---

### Post by Favux on 2009-12-23
Hi Chris,

The next step is to patch linuxwacom.  If you want you could try tekknokrat's xserver-xorg-input-wacom deb at [post #317]("http://ubuntuforums.org/showpost.php?p=8079237&postcount=317").  Just download it and double click on it and the Debian installer will install it.  If it works for you you won't need to patch and compile linuxwacom 0.8.4-4.

---

### Post by javier_8r on 2010-03-10
Thanks very much for the information!! one question: Does this drivers work fine on jaunty? and I used to have karmic but since I had a lot of problems including that when it recognizes my touchscreen it wasn't calibrated and i couldn't calibrate it at all also every time it recognizes my touchscreen it won't recognize my video card so every kind of effect was disabled. that's disgusting haha so if every one could answer me please thanks in advance and regards!

---

### Post by Ayuthia on 2010-03-10
You will have to build a custom kernel for Jaunty so that it will work.  This is because there are several parts of the kernel that needs to be built.

Do you have a tx2-1025dx?  The calibration issue is because the touchscreen is either using the evdev or synaptic driver instead of the wacom driver.  As for the graphics driver, did you do anything else beside installing it though Hardware Drivers?

Also which was the last version of Windows on your laptop and are you using 32 or 64-bit?

---

