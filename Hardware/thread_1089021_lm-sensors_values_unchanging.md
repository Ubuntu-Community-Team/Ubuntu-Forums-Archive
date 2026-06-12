---
title: "lm-sensors: values unchanging"
date: 2009-03-06
forum: Hardware
---

### Post by Fatman_UK on 2009-03-06
Hi all.

I'm running Ubuntu Netbook Remix (Intrepid, 32 bit) on an Advent G10 netbook and loving it. :D 

There's just one tiny fly in my large pot of ointment. I have lm-sensors and sensors-applet installed. Two sensors are detected: acpi/THRM and libsensors/temp1, both of which start at 50 deg C and never change.

From cold the G10 heats up fairly quickly, but I'm sure it's not at 50 deg C just after logging in. Or at any other time, thinking about it. Surely I should expect to see some fluctuations?

Other threads suggest that the sensors are present but not connected. I'm confident in my ability to disassemble, polish and reassemble laptops, but would it be possible for me to connect the temp sensors?

I'm puzzled as to why any manufacturer would go to the trouble of cramming temp sensors into a small device and then not connect them. Is there a good reason for this, or do I just have an assembly line dud?

Thanks in advance.

---

### Post by doas777 on 2009-03-06
keep in mind, a CPU can go from 22 to 50 in about 2 seconds. in fact my PC is hottest when loading the bios and windows. once I;m logged in it cools back down to 35 or so.

your system temp and HDD temps are much slower to change, but CPUs are quite mercurial, and can fluctuate widely in short periods of time. if you have a fast heat up, but a slow cool down, check your heatsink and fans.

good luck

---

### Post by Fatman_UK on 2009-03-06
Ah, I didn't realise they could heat up so quickly. Thanks.

I seem to recall reading that the Intel Atom (not sure which one, but ca. October 2008 ) runs hot.

I guess a lot of the heat is probably coming from the GPU as well, since I'm using the netbook-launcher interface.

---

