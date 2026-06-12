---
title: "Toshiba 'xD card' reader not working"
date: 2010-05-16
forum: Hardware
---

### Post by Aqlor on 2010-05-16
Hello everyone,

I own a Toshiba A300 and for some reason I am failing to read xD cards.
I've looked on the web but I can't find a good solution, anyone else having the same problem?
**lspci** shows the controller but **dmesg** gives the *same result before and after* inserting the card 


**lspci | grep xD**:
*0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)*


I _think_ it was working before on ubuntu 9 but I am not really sure of that...

---

### Post by Quirkuntu on 2010-05-17
Yes, it appears I've got a similar problem, but with an M2. 

I just installed 10.04 in a Toshiba M2 laptop. Everything is working fine indeed, except for the built in SD card reader.

I'm relatively new to Ubuntu, so I don't know if this is a hardware issue or an Ubuntu issue. Looks like a camera with an SD card mounts just fine via USB, but neither the same SD card nor an unused one mounts when inserted in the SD card slot in the laptop. Nothing happens, as if there was no card reader present. 
I don't know whether or not it works with previous Ubuntu versions, because I haven't used any other Linux version in this M2.

So, in case someone with a Toshiba (or some other similar) laptop with a  built-in SD card reader has managed to get it to work and is able to mount and read SD cards with the Lynx,  please let me know how you did it.

---

### Post by Aqlor on 2010-05-17
Like you, I have tested the card. I did it with an external card reader with no problems.

I am still to find out how to get the reader working correctly.

---

