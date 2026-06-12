---
title: "Sound works in Ubuntu; in Vista not so much"
date: 2008-06-18
forum: Hardware
---

### Post by sithguy on 2008-06-18
I recently installed Ubuntu on my computer so now I am dual-booting Ubuntu Studio 8.04 and Windows Vista Ultimate. I had some problems with my sound in Ubuntu but I fixed them, however, now my Vista sound doesn't work. I am using a SoundBlaster 24-bit External. 

I will be happy to provide anymore details, about either Vista or Ubuntu.

Thanks in advance,
-Sithguy

---

### Post by Fire_Chief on 2008-06-18
The functionality of the sound card in Vista should be totally unrelated to the operation in Ubuntu. You may want to try reinstalling the Creative drivers for your sound card in Vista.

Cheers!

---

### Post by soccerboy on 2008-06-18
make sure you properly shut down ubuntu before booting into vista.  There are some device locks that don't get released if the entire shut down is not finished (i.e. you boot to another os after putting the computer in hibernate or suspend).

---

### Post by sithguy on 2008-06-18
Thank you. I will try both of these solutions and get back to you.

---

### Post by sithguy on 2008-06-19
First I shut down ubuntu completely and restarted my computer but my sound still doesn't play anything. I also reinstalled the creative Vista drivers but once again my sound doesn't work. I even tried a different usb cable but nothing. The only thing i notice is that speakers make a loud popping sound when ever when sound card turns off or on, or when I plug it in. Even when I try my headphones no sound still comes out.

I'm really confused and wish to know if there is anyway other way for me to diagnose my sound problem?

-Sithguy

---

### Post by sithguy on 2008-06-19
OK. Somehow I solved by cycling through the defualt devices in Vista. In the sound panel, selecting each device as defualt until I returned to my original card.

---

### Post by sithguy on 2008-06-20
OK, turns out my problem was not solved as I accidentally booted up into Ubuntu Studio, completely shut down, and booted to Vista to found that my sound doesn't work again. I tried cycling through my default devices but I still not receiving any sound. The volume is still moving in my mixer and Vista says all the devices are working properly, tried disable and then renabling the device but to no avail. I'm to try reinstalling the drivers but I don't want to reinstall my drivers everytime I want to start up Vista

Is their something I'm missing because I would really like to know?

Thanks in advance,
-Sithguy

---

### Post by sithguy on 2008-06-20
I've contacted creative but I don't know if they'll be able to fix the problem.

---

### Post by Fire_Chief on 2008-06-20
Have you tried power cycling the device itself while in Vista? I only mention it since soccerboy mentioned the device locks during shutdown possibility. It should cause the device to re-initialize in Vista and start working. Just a thought.

---

### Post by sithguy on 2008-06-20
Ok I think I may have figure out the problem. The power cycling may have worked but I believe the answer really to be when I said I completely shutdown, I meant I restarted. I think this is o
because i accidentally started up ubuntu and then shutdown it and now the sound works. Sorry for the inconvience I may have cuased by not saying that in the first place.

Thanks for all your help
-Sithguy

---

