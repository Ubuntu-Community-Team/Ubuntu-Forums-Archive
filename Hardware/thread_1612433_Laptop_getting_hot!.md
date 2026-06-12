---
title: "Laptop getting hot!"
date: 2010-11-03
forum: Hardware
---

### Post by bilalsana on 2010-11-03
hi
i have a dell inspiron 1564 with intel core i3 330 processor. it keeps on getting hot and has turned off, while i ws using it, quite a lot of times now (due to getting hot). i am currently using lucid, but i have tried maverick as well but to no avail. Plus the sensors dont seem to work, typing sensors in terminal always shows 27 degrees and the panel applet also always shows 27 or 0 degrees. i tried i8kutils, forced i8kmon0ut it would halt the system altogether! it did show the core temperature at 59 degrees twice before freezing the system.
however in windows 7, the system never shutsdown! and a temperature monitor i downloaded recently correctly shows the temperature, which ranges between 50-80 degrees!
Please help me to monitor my core temperatures as well as get rid of this heating problem!!

---

### Post by ajgreeny on 2010-11-03
Have you installed lm-sensors and hddtemp, both of which may help?

Also make sure your fan vents are clear of dust and muck.

I can never get sensors working on my old hardware,other than mbmon,which gives a readout, but could be way of mark, for all I know.

---

### Post by TSJason on 2010-11-03
I had an inspiron laptop that did this (a 5150 I think) and it was actually a hardware issue that Dell fixed (for free) by replacing the heatsink, fan, and thermal paste - though that was a P4 /w nvidia. 

It still got really hot after the repair. You might check for any bios updates and verify that if there is any speedstep configuration in the bios, that it is turned on.

---

### Post by bilalsana on 2010-11-03
yup, i tried lm-sensors but to no avail! and mbmon gave this reply 

No Hardware Monitor found!!
InitMBInfo: Success

and the laptop is like a few months old so it isnt the dirt, plus it does well under windows 7!

only if i could get something to control the fan/check the temperature!

---

### Post by Renée Jade on 2010-11-03
> **bilalsana said:**
> 
and the laptop is like a few months old so it isnt the dirt, plus it does well under windows 7!


That is really weird and I find it kinda hard to believe. How much data do you have that supports your theory that it only overheats under Ubuntu? Has it only happened a few times? Do you use the different OSs for different kinds of work? I found that my Inspiron used to crash from overheat most often for two reasons. When I was either using it on a bed or some other soft surface. And when I was downloading or transferring large amounts of data from the Linux partition to the Windows partition. This second situation seemed to cause the HDD to get very hot, probably from having to jump all over the disk. Before you assume that it is the OS, look closely at your usage patterns.

---

### Post by TBABill on 2010-11-03
Couple thoughts. I have an Inspiron 1545 that got baking hot with Ubuntu when 10.04 released. It got to 86C so I shut it down. Your machine should never shut off at 59C. That's in the normal range. If you are shutting down at that sort of temp then you have another failure somewhere. The sensors on your motherboard, even if reporting incorrectly (you are looking at core 0 most likely...mine shows the real temps of my i3-330m on core 1 and core 2). There is an applet you can install in the repos but I'm not home to give you the name. It shows all your cores and you can remove them one by one on the top panel. I keep 3 going....the 2 readings that are correct (2 of the 4 show false readings like you described) and then the other is the hard drive temp. Search for applet in Synaptic and play with the one that offers sensors, including cores and hard drive in one.
 
Anyway, I think the freezing or shutting down is not heat related. If you hit 80+ then you could lean that way, but under 60C is just normal on Ubuntu, especially online with flash and java apps or videos going. The max on your machine before the sensors force a shutdown should be in the neighborhood of 100C (99C probably). 
 
Do you have the frequency scaling applet running on the top panel? That's just a matter of right clicking the panel, select "add to panel", then pick the freq scaling applet. Default is either ondemand or powersave I think so you should see your processor speed stay low until more processing power is required. At least that being on the panel allows you to see what's going on visually with the scaling and sensors info right in front of you.
 
I would look more deeply than temperatures, or get that applet tweaked to report properly, and then diagnose the shutdown issue. You may be able to eliminate heat as a contributing factor.

---

### Post by bilalsana on 2010-11-06
thank you everyone for your concern!

well actually when the laptop froze at 59 degrees it was because of5 i8kutils. i know this because whenever i tried to i8kmon or i8kfan, the laptop immediately froze! on the other hand when it freezes when heated, its always terribly hot. hhdtemp is working right and shows the hdd temperature which never goes above 43 degrees!
i tried copying a 3gb movie over wlan and the laptop just shut down at both instances. i had placed it over a glass table for better cooling. at one instance when it just went off, i rebooted into windows 7 and the temperatures were in the 80s and they slowly came down to around 50s. then i tried copying the same movie and it gave an error while copying, but the system didnt turn off.
and yes, i have used that applet already and it either shows 27 degrees or 0 degrees.

even if you say it is a hardware problem, why is ubuntu not showing the right temperature??

---

### Post by Jimtheplanner on 2010-11-06
Hey Guy's

I've mentioned my 10.10 experiences with my Dell 1545 elsewhere in these forums. I would dearly love to use Ubuntu as Mandriva is on the ropes...

However; on my back to back "fresh" installations Ubuntu was 10 Deg C hotter than Mandriva with my hard drive. I actually removed it and could almost burn my fingers on it at 52 Deg C+. I've repeated this experiment several times.

This is all on the same hardware.... I may try either be OpenSuSE (just for an experiment) I started with SuSE around ten years ago but the tie in with M$ still makes me choke. I may also try Sabayon unless Mageia arrives before xmas.

Unless some knows of a way to reduce the HD temps.

Jim

---

### Post by jutt69 on 2010-12-13
I too have issues with Harddrive heat with Ubuntu 10.10 and not with Vista (OS problem not hardware)

The only solution I have found is to change the APM settings. The default setting are 254 when plugged in and 128 when running on battery. When the APM is set to 254 my Harddrive slowly creeps up to +60°C. However, when set to 128 it runs at a more reasonable 40ish°C.

Using the "hdparm -B" command I lower the APM when running on AC to 128 when it gets too hot. I have read threads which suggest permanently setting the APM to 200 (which does work well but is not without issues)

The only problem with lowering your APM is the load cycle count rises at, what is in my opinion, an unacceptable rate.

---

### Post by Filkins on 2010-12-16
> **Jimtheplanner said:**
> Hey Guy's

I've mentioned my 10.10 experiences with my Dell 1545 elsewhere in these forums. I would dearly love to use Ubuntu as Mandriva is on the ropes...

However; on my back to back "fresh" installations Ubuntu was 10 Deg C hotter than Mandriva with my hard drive. I actually removed it and could almost burn my fingers on it at 52 Deg C+. I've repeated this experiment several times.

This is all on the same hardware.... I may try either be OpenSuSE (just for an experiment) I started with SuSE around ten years ago but the tie in with M$ still makes me choke. I may also try Sabayon unless Mageia arrives before xmas.

Unless some knows of a way to reduce the HD temps.

Jim
I'm also having an issue with hard drive temp in ubuntu 10.10. I'm using a Gateway ma7, and all is well and functioning nicely except for the hard drive getting over 50 degrees. I tried setting th APM to 200 as suggested above by entering hdparm -B 200, but after hitting enter, everything i typed just disappeared.

-newb

---

### Post by Filkins on 2010-12-16
> **jutt69 said:**
> I too have issues with Harddrive heat with Ubuntu 10.10 and not with Vista (OS problem not hardware)

The only solution I have found is to change the APM settings. The default setting are 254 when plugged in and 128 when running on battery. When the APM is set to 254 my Harddrive slowly creeps up to +60°C. However, when set to 128 it runs at a more reasonable 40ish°C.

Using the "hdparm -B" command I lower the APM when running on AC to 128 when it gets too hot. I have read threads which suggest permanently setting the APM to 200 (which does work well but is not without issues)

The only problem with lowering your APM is the load cycle count rises at, what is in my opinion, an unacceptable rate.
I've got a hot hard drive too and tried setting hdparm -B to 128 and 200, however, I'm not sure if the settings are actually changing. I'll enter the command and hdparm doesn't appear to do anything in the terminal window (text just disappears). Maybe this is normal (I'm new to linux and command lines in general), but I'd like to see how it's configured to begin with before making any changes.

---

### Post by ripsometime on 2011-01-24
I use ubuntu a lot on my desktop but unfortunately it has issues with my laptop. It was fine for the first few boots, but one day i decided to boot up ubuntu instead of windows 7 (as it loads faster and i needed to quickly check something).

There were some display errors and the window manager would not load (i was using compiz) i thought nothing of it and the fan was not spinning fast.  i rebooted the laptop to check again and the same issue. i thought my gpu had failed so i booted into windows to check..... the fan came on instantly on full throttle. i checked speedfan and all temps were the highest i had ever seen them... scared the **** out of me. after the fan stopped the laptop behaved as normal and the gpu works fine in windows 7. all temps returned to normal and i was relieved.


This was very weird... was ubuntu stopping the fan from speeding up and cooking my gpu? or was it something else?

---

### Post by bilalsana on 2011-01-26
okay, this post has been here for quite sometime now..will someone plz come to our help?? i dont want to ditch ubuntu and i dont want to cook my laptop!

---

