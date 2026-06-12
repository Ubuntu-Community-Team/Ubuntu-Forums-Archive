---
title: "Ubuntu 9.04 random fast beeps at startup"
date: 2009-05-25
forum: Hardware
---

### Post by dreamonb on 2009-05-25
Hi,

Since I upgraded to Ubuntu 9.04 I started experiencing random fast beeps  at startup. The only way I can stop them is by rebooting and if I am lucky ( 70%-80% ) the reboot solves the beeping. The beeps are not coming from sound card they are from speaker connected to main board.

I looked in /var/log and i didn't see any errors. I looked at the coolers and cpu/gpu temps are all working correctly. Any clue how i can troubleshot this?

Mainboard: IP34Pro
CPU: q6600 @3G:3G 
Ram 4G  4/4/4/12
Vid Card: 8800GT 512Mb
HDD 1 Raptor and 1 750G segate barracuda.

Thanks

---

### Post by Steelmourne on 2009-05-25
There might be an option in your BIOS to disable sounds relating to POST and boot up. Just make sure you don't disable the sound card by mistake.

---

### Post by PurposeOfReason on 2009-05-25
Find out the maker of your BIOS, and look for the bios beep code for that maker. Those beeps are not random and it is never good.

---

### Post by rob2uk on 2009-05-26
Just to clarify, are the beeps happening during POST (before Ubuntu starts to load) or after it starts?

---

### Post by dreamonb on 2009-05-26
After POST. Is usually couple seconds after Ubuntu starts loading ( before the GUI with username/pass screen). I have a windows XP and is not doing that beeping. Also I remember encountering same issue with Ubuntu 8.04 beta but after release i didn't encounter same problem.

I also tried installing/uninstalling lm-sensors and anything associated with them without any change in behavior.

---

