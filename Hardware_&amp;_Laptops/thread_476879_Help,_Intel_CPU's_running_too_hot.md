---
title: "Help, Intel CPU's running too hot?"
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by 67GTA on 2007-06-17
I have had my motherboard replaced by Best Buy(warranty). It is an Intel Pentium D dual proc. D945GCZ board. I am sure it is not a Ubuntu problem, because it also happens with XP after the motherboard switch. As far as I can tell it is the exact model,step,frequency,etc. Ever since that the CPU fans go crazy when something graphic/memory intense is started such as Synaptic manager,Firefox,3D game,etc. You can not even hear the PC running after a cold boot, just like it should be. After about 10-15 min. it gradually gets worse. I wonder if it is going to take flight(lol). The fans run too loud even if nothing is being ran(idle).  While running PCLinuxOS I got several errors about my CPU being over the threshold? I can't find any errors about this in Ubuntu system logs, and my board does not support temp sensors. Can someone help point me towards finding a solution? I have had this PC at Best Buy for repairs 7 times in two years, and do not wish to go back even though I have some warranty left. It is always worse in some way when it comes back. I would rather fix it myself.

---

### Post by steveneddy on 2007-06-17
Is this a desktop or laptop?

---

### Post by 67GTA on 2007-06-17
Sorry, it is a desktop. Forgot to mention that.

---

### Post by IntuitiveNipple on 2007-06-17
It sounds very much as if the heatsinks aren't making efficient thermal contact with the CPUs. I would make sure I've got a small tube of good-quality thermal paste and then remove the heatsinks from the CPUs, clean both until they sparkle, and then apply a ***thin*** film of thermal paste to the CPUs and spread it evenly (with a box-cutter blade or similar) so that the CPU printed markings can just be seen but the entire surface is covered.

The trick with thermal paste is to put on just enough to get the thermal conductivity without making it thick whereby thermal transfer is reduced.

Make sure the heatsinks are replaced evenly. Secure them firmly without dragging them around on the CPUs - you don't want to move the thermal paste about too much.

Start the PC go into the BIOS immediately and monitor the temperatures from the BIOS hardware monitor page until you are satisfied the job has been successful. If you see one or both of them getting overhot or the fans get anxious shut it down and check your work.

I managed to reduce temperatures on a dual-Athlon mobo from average of 62C to 52C simply by redoing the thermal paste. I then added a couple of monster-sized heat-pump coolers and now even when both CPUs are running at 100% for hours (compressing digital video) the CPUs never go above 54C and the fans don't increase speed past 1,500 rpm.

---

### Post by 67GTA on 2007-06-17
I never thought of that. Actually, every time they work on it I have to "fix" something. It would not suprise me. I just got it back two weeks ago with a replacement cd drive. Both OS's said the drive did not exist. I looked and saw that they left the cable off the back of the drive.

---

### Post by 67GTA on 2007-06-17
I just checked the temps in BIOS and it said 

proc. temp 86C
internal temp 34C
remote temp 44C
proc fan speed 2520
rear fan speed 3840

I'm not sure what the second and third temps are for, but I know the proc temp is way too hot. 
I'm going to shut it down until I can look at the paste. Thanks for the tip. Maybe I'll be back tomorrow a little cooler(if I can find some thermal paste).

---

### Post by 67GTA on 2007-06-17
I couldn't help myself. I looked and saw there was too much thermal paste between the heatsink and the proc per your description. I scraped some off and rebooted. It is half as loud as it was and the BIOS said the temp was 7 degrees cooler. You were on the right track. I will shut it off again and try to repaste it tomorrow. Thanks for the help.

---

### Post by southernman on 2007-06-18
FWIW, The first thing (if I were you) I'd do in the monring... after best buy opens at what 1 in the afternoon *rolls eyes* is call the store and get the manager on the phone. Let him know what was done and get on his **** about it too!

I wouldn't let bb work on anything of mine... even if I wasn't a do-it-yourself kinda guy.

I've had clients tell me horror stories related to bb. Been tempted to go in and put a stack of my business cards on the service counter! Bahahaha! Hey... I'd pay them (bb) a finders fee of course. *wink*

---

### Post by 67GTA on 2007-06-18
I'm not a PC expert, but I prefer to do my own repairs. The only reason I went back so many times is because I bought an extended warranty. I am researching to build my own next time. I don't want to even look at them again.

---

### Post by steveneddy on 2007-06-18
One trick I used to do when I was modding all the time was to polish the bottom of the heat sink to get a little more heat transfer out of it.

---

### Post by 67GTA on 2007-06-23
Finally got the thermal paste. Polished the heat sink and reapplied the paste. CPU temps are about 20 degrees cooler. I can barely hear the fans now. Thanks for the help.

---

### Post by FunkyRider on 2007-06-25
67GTA:

I know it will be a little bit off topic, but please help me to repair my Motherboard with your BIOS dump!

It's very hard to find a user with the D945GCZ board, please do this to help me repair me motherboard! Coz this really gonna help me get my machine back alive! Thank you very much in advance! 

It only takes 1-2 minutes to do it, won't take you too long.

Search and download the tool "HWDirect", or from this URL: [http://www.soft32.com/download_27150.html](http://www.soft32.com/download_27150.html)

Run it. Select "Memory Dump" in left column, Enter "Physical Address (Hex)" = fff80000, "Size (Bytes in Hex)" = 80000. Click "Dump" This will read the memory shadow copy of BIOS image.

Then right click the hex code area, select "Select All", right click again, select "Copy" Either paste it to Notepad, pack it and upload it as an attachment, or paste it in a post.

Please help me to do this, thank you again!

---

### Post by 67GTA on 2007-06-25
?

---

### Post by FunkyRider on 2007-06-26
Holy smoke man, you saved my computer! You are my own personal Jesus Christ.......

Flashed your BIOS into the SPI chip taken off from the dead motherboard and soldered it back, power on and Vola! Instant back to life!

Thank you sooooo much man!

---

