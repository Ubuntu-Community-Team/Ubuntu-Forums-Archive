---
title: "amd radeon graphics for gaming"
date: 2015-04-08
forum: Hardware
---

### Post by frank101 on 2015-04-08
Im fairly new to linux and completely lost....my amd graphics card works some as long as its only doing regular dispay work for desktop use, programs run fine even blender works good. As soon as i try to run any game at all i get a crash, sometimes i can recover with ctl alt f1 restart lightdm other times my keyboard wont even respond. I use the latest version of Kubuntu and i have installed proprietary amd drivers. I have tried all three drivers in my driver list which are amd drivers, amd drivers from amd update, and the recommended wrapper that came with kubuntu. Nothing seems to work. I have tried fidgeting with all the settings in amd catalyst to no avail. The games i have tried are all from steam and claim to be for linux, i have read some horror stories about amd graphics with linux do i just need to buy an nvidea card? I will be happy to perform any lookup or crash dump or whatever i need to do to further explain the problem i just dont know what or how. Any help will be greatly appreciated.  I work during the day so i can only respond before 7 am us central or after 6 pm, but if asked i will do anything needed to detail the problem.

---

### Post by QIII on 2015-04-08
Hello!

Tell Linus Torvalds you are thinking about an Nvidia card and you'll get a response with every known obscenity in English.  :)  

Nvidia is good and they work well with Linux.  So do AMD GPUs.  But the old view of ATI before they were bought by AMD persists.  I have AMD cards in my Linux machines.

Before we can start to help, we need to know what you mean by "latest" Ubuntu.  14.10?

We'll also need the exact model of the GPU.

Cheers!

---

### Post by mastablasta on 2015-04-08
I am experiencing some issues lately with opensource drivers as well. crashes. I mean I had crashes before, but only in some games. now minecraft is doing them as well. and just like your describe. but mine is a very old ATI card from 2003. However I had also what you had on a bit newer card as well.

however the proprietary drivers should work. 

I would start checking the logs if there is anything in them. system.log, kernel.log, xorg.log and similar.  since it crashes like that it is hard to find what the issue is.

oh and speaking from recent experience - there are "horror storries" with NVidia as well. spent many days, contacted NVidia etc. no one knew why the card did not initialise. card works well on windows, the slot and motherboard works, drivers installed well with no issues,  yet card just didn't get initialised with NVidia drivers. only reverse engineered ones worked to a degree (very bad performance). 

I will try to troubleshoot mine probably during weekend.

also try setting desktop effects to turn off when running full screen applications (it's in system settings), try to use software rendering for desktop and try one of the opensource games - for example supertux cart or wofenstein enemy territory. 

you can also run benchmark programs like glmark2 (but this one is only checking the old stuff mostly), phoronix suite (just some of the game demos there not necessary to run the whole thing as it is huge to download) or unity engine demo. see if they crash as well.

---

### Post by frank101 on 2015-04-08
Sorry for the late response...busy day at work. Thanks for the quick response.  My os is Kubuntu/Ubuntu 14.10 uptated daily the gpu in question is an AMD/ATI Turks XT [Radeon HD 6670/7670] as listed in PCI Devices-System Information. I will try the things mastablasta suggested this evening and let you know before bed tonite.

---

### Post by frank101 on 2015-04-09
Still no luck...tux kart will run but only at 1024x768 windowed no full screen and i use a 1080 hd projector.tried the no desktop effects for fullscreen still fail to run anything other than tuxkart. Looked at my system log which was no help to me, i have no idea what im lookin at. I downloaded phoronix test suite and ran the quake wars demo test which failed. The error reads as follows:  E: ./etqw.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory. I dont know what this means, i assume a file is missing but i dont know enough about it to feel comfortable doing anything. I will run some more of the tests after work today and see if i get anything else. I signed up with steam thinking i could buy some games to run on my linux machine, figured my hardware could handle it even thouh its a slightly older machine. Amd Athalon 3 core 3.3 gig processors 8 gig ram and the previously mentioned gpu. Am i just too far out of date to be effective running games or do i have an actual problem here. I dont even know how to figure out whats wrong.


Update: Tried the phoronix test #46 gpu test0.7.0 which failed also. E: 2015:04:09@06:22:55(00000000028) <*> - SimpleVertexColor GPU program error:

Again no idea what this means but it seems as though i have a problem still even though Tux SuperKart runs.

---

### Post by frank101 on 2015-04-10
I still have not managed to run any game from steam and the graphics tests from phoronix continually fail. Since this is really about gaming should i close this thread and start a new one in the gaming section? I am completely lost, I know i have a problem i just dont know how to tell whats actually wrong. Could it be the gpu actually failing or does it sound like a software/driver issue. The machine is several years old and i would be willing to buy a new gpu if i knew that was the problem, I'm just not able to tell whats going on.

---

