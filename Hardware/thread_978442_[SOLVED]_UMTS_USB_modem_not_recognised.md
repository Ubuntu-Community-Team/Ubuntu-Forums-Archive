---
title: "[SOLVED] UMTS USB modem not recognised"
date: 2008-11-11
forum: Hardware
---

### Post by The Foz on 2008-11-11
I have a new Huawei E220 UMTS USB modem. It is intended to be connected to my server, but I am trying to test the configuration on my laptop (because my server is currently at a different location, until I get the UMTS Internet connection debugged).

On the server the USB modem is recognised when I plug it in, and I can access it using /dev/ttyUSB0. On the laptop it is not: there is no /dev/ttyUSB*; also the lsusb command hangs (no output, and no possibility of interrupting it with <CTRL>C) until/unless I remove the stick. I have tried different USB ports (in case one of the ports is not working properly). I have also tried inserting the USB modem before boot (boot seems to hang in this case).

Both machines have the same OS (Hardy Heron, and the same updates), although the server has a different OS history (it began at an older version than the laptop, and thus has had more OS upgrades).

---

### Post by The Foz on 2008-11-13
In case anyone has a similar problem, I will explain how I solved the problem.

The basic problem with the laptop was that it was constantly trying to load/configure the gspca driver for the built-in web-cam (which is broken), also connected by USB. This was interfering with the detection of new USB hardware, and causing the lsusb command to hang.

I finally got around to implementing the fix ([http://ubuntuforums.org/showpost.php?p=5436761&postcount=2]("http://ubuntuforums.org/showpost.php?p=5436761&postcount=2")); blacklisting the gspca driver. After that, my UMTS USB modem was recognised automatically. I then managed to get online using wvdial.

My laptop also now boots much faster, and runs faster (no attempts to configure the gspca driver constantly running in the background).

---

