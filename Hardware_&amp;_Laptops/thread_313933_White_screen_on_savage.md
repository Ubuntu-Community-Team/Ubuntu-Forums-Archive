---
title: "White screen on savage"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by donkyhotay on 2006-12-06
I recently installed savage (which is now a free download) however when I attempted to play the game I simply got a white screen with a blocky mouse and was unable to get out of the game. Researching around in other forums I found out that many linux graphics drivers (like the radeon driver I use) isn't compatible the video compression used on some textures and needs to be turned off. This is easily done by simply adding
setsave vid_compressTextures 0
to the end of the
./game/startup.cfg 
file which makes the game startup perfectly. Savage unfortunately thinks it's REALLY neat to have compression on so upon exiting the game it will reset 
./game/startup.cfg
and lose the changes. The solution to this of course is to edit the loading script itself so that it will continually edit the startup.cfg file before actually loading savage itself. So if you have been having this problem with savage open up the savage loading script (located in the main savage directory). Add the following line 
echo "setsave vid_compressTextures 0" >> game/startup.cfg
right above the line that says
LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin `pwd`
Occasionally the very first time you run savage after making this change you will still get the white screen. If so do NOT reboot or turn your computer off. Simply hit tilde (~) and type exit. Then go ahead and run the savage script again and it will work perfectly this time around.

---

### Post by Gen2ly on 2007-05-27
Thanks for the tip.  I fortunately dont' have to do the loading script addition. :)

Fun Game!

---

### Post by defec8ing on 2007-08-21
When I do as you suggest I get a black screen with login and quit written on it- really blurred as if someone drew them in old MsPaint.  My mouse is square-shaped and leaves a permanent white trail.....ARGH!

How to sort this out anyone?

---

### Post by defec8ing on 2007-09-05
bump

---

### Post by defec8ing on 2007-09-09
I fixed it by installing Nvidia drivers- anyone with the same problem as I had should try searching the forum for a Howto and do the same.

---

### Post by Vadi on 2007-09-22
Hm, I don't even have a startup.cfg anywhere on my system.

---

### Post by hey_mrs_tee on 2007-11-15
> **donkyhotay said:**
> I recently installed savage (which is now a free download) however when I attempted to play the game I simply got a white screen with a blocky mouse and was unable to get out of the game. Researching around in other forums I found out that many linux graphics drivers (like the radeon driver I use) isn't compatible the video compression used on some textures and needs to be turned off. This is easily done by simply adding
setsave vid_compressTextures 0
to the end of the
./game/startup.cfg 
file which makes the game startup perfectly. Savage unfortunately thinks it's REALLY neat to have compression on so upon exiting the game it will reset 
./game/startup.cfg
and lose the changes. The solution to this of course is to edit the loading script itself so that it will continually edit the startup.cfg file before actually loading savage itself. So if you have been having this problem with savage open up the savage loading script (located in the main savage directory). Add the following line 
echo "setsave vid_compressTextures 0" >> game/startup.cfg
right above the line that says
LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin `pwd`
Occasionally the very first time you run savage after making this change you will still get the white screen. If so do NOT reboot or turn your computer off. Simply hit tilde (~) and type exit. Then go ahead and run the savage script again and it will work perfectly this time around.



yeh ..same here, i do not have the startup.cfg file in my ./game~file

and i have downloaded the most recent savage 2 game which is the NFE version - standalone for my linux

any suggestions?

---

### Post by hey_mrs_tee on 2007-11-15
> **defec8ing said:**
> I fixed it by installing Nvidia drivers- anyone with the same problem as I had should try searching the forum for a Howto and do the same.

i tried searching for it but i'm lost, can you please post link here if you can and have got time on how to fix my driver up by installing the Nvidia drivers?

---

### Post by Geek506 on 2008-05-01
> **donkyhotay said:**
> ... open up the savage loading script (located in the main savage directory). Add the following line 
echo "setsave vid_compressTextures 0" >> game/startup.cfg
right above the line that says
LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin `pwd`
Occasionally the very first ...

**LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin `pwd`** isn't in the startup.cfg file anywhere ???

Need help ... rather new to Linux and Ubuntu .... but if I can get Guild Wars and WoW to work fine, how come Savage doesn't work? It loads but then goes to a white screen (sound works) but I have to ~ and exit out. I noticed that after I ~ out it says it's up to date but just above that it says "attempt to compress texture failed" (and lists several TGA files).

Any thoughts?

---

