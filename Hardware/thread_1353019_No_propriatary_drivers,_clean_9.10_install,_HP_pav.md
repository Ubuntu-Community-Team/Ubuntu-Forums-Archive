---
title: "No propriatary drivers, clean 9.10 install, HP pavillion"
date: 2009-12-12
forum: Hardware
---

### Post by cough-e on 2009-12-12
[problem solved, see my third post]

Hi.
I've seen this problem, or similar, been posted on the forum earlier. I also know that is not a good line to start a new thread with.

Laptop: HP Pavillion tx1020, broadcom 4312, nVidia gf go 6150 graphics.
OS: Clean installed Ubuntu 9.10, downloaded yesterday.

Under "Hardware Drivers" nothing is listed. The physical wireless adapter led-indicator is red, should be blue. If I plug in a network cable no lights are lit on the port, wich it usually does.

When I run Ubuntu from the boot-CD ("Try Ubuntu without making hardware changes" or something) all the needed propriatary drivers are listed in "Hardware Drivers".

I have blacklisted all other wlan drivers.
I have tried ndiswrapper with windows driver files.
The laptop has recognized my broadcom, but claims missing firmware file.

BUT somehow I am not that interested in making the hardware drivers work individually. I believe the solution is to make Ubuntu recognize the needed proprietary drivers, because this method worked smoothly on the 9.04 install. Am I right?

As I hvae read many threads on this forum, it seems that some drivers, type: restricted, needs to be pre-installed before 9.10 install. Correct? So why is it that theese drivers show up under "Hardware Drivers", listed as proprietary drivers running live-cd?

I have spent all freaking night trying to figure this out, now I just had to post here for suggestions...

Thanks
Henrik

---

### Post by KommaH on 2009-12-12
Insert your disk into your computer. Go to System -> Administrator -> Software Sources and check the CD ROM, then click close.

You should be able to go to System -> Administrator -> Hardware Drivers now and install the drivers you need.

---

### Post by cough-e on 2009-12-13
Thank you for your reply, I will try this as soon as I get back home!

---

### Post by cough-e on 2009-12-16
I hereby present the solution that worked for me

I found out that even tho the lights around the network cable connection plug did not light up as it used to when I plug in a cable, ubuntu had actually recognized it and I was online. 
When I was online through the cable, I went to update manager, updated everything that was available, then updatet all packages in synaptic (do not know wich one made the difference) the Hardware Drivers list finally listed all my needed drivers.

Even tho I was not able to test KommaH's solution it could be this would also work. Thanks for your reply anyway.

---

