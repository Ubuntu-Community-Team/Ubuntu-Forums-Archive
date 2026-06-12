---
title: "Test Report Jetway 7F3E - Mini-ITX"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by TuxCrafter on 2007-03-27
This is a test report I made for the jetway 7F3E motherboard:

Review version type 0.1 beta

version 1.1

12-03-2007, The Netherlands

This is a test report of the Jetway 7F3E Mini-ITX motherboard and the Morex Cubid 3688 case. I am creating a way to do benchmarking under Linux. I still need help with this. For example with the creation of universal test methods and automated benchmark scripts. Please contact me if you can help or have any questions, also if you are a vendor and want to test Linux support on hardware.

Pictures: (full resolution pictures on request)
640x480-P3030022.JPG:
Here you can see that the fan hits the case and makes it impossible to close the case.
640x480-P3030025.JPG to 640x480-P3030027.JPG:
These are pictures of an old type Morex Cubid 3688 mini-ITX case with a better power supply unit on it. You can see the beauty of the big, good designed heat sink of the VIA EN12000E motherboard and how well it fits in the case.

Chipsets:
The7F3E motherboard uses an AMD GEODE 1750 CPU with a SIS741CX North Bridge Chipset and a SiS964 South Bridge Chipset.

Problems with audio:
The SiS SI7012 with ALC655 sound chip has a lot of unwanted signal noise on the speakers, which is much higher compared to the VIA VT1618 sound chip. 

The Dolby Surround 5.1 modus doesn't work fully. The Center and LFE speakers are not working well. There is also no function to control the volume of different running applications. The VIA V1618 sound chip has this functionality. This is a real minus. Maybe it is possible to configure the ALSA .asoundrc file to get things working correctly. Normally I test Dolby with this command: speaker-test -Dplug:surround51 -c6 but it doesn't work out of the box. It needs a custom buffer and period size. If someone creates a good .asoundrc for this chipset please contact me. This is the link to the related ALSA website: [http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?module=intel8x0](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?module=intel8x0)

With the default settings it was impossible to use more than one application with sound capabilities. This can also be solved with a good .asoundrc file.

Problems with video:
The company SiS does not develop or support Linux video drivers! But there is someone who develops SiS drivers in his spare time. This is really a great job of him and I respect him for that. His website is [http://www.winischhofer.com/](http://www.winischhofer.com/) but there are only 2D drivers that work with the SiS741CX chipset. Normally drivers should come from the freedesktop.org website: [http://dri.freedesktop.org/wiki/SiS?action=highlight&value=CategoryHardware](http://dri.freedesktop.org/wiki/SiS?action=highlight&value=CategoryHardware) You can compile a SiS DRI driver but it will not work with the SiS741CX chipset. I mailed some people about it but they did not respond.

In my opinion there is no 3D driver support for Linux with the SiS741CX chipset!c If someone finds a way to get 3D working please contact me! The short come of no 3D drivers for the chipset is a real pain in the ***. I advise not to buy this system if you want 3D driver support under Linux with the SiS741CX chipset!

There is also a problem with the 2D driver. When you hit control + alt + backspace the system will freeze and you have to manually reboot. Does someone know why this happens and how to fix it?

Problem SATA (Serial-ATA):
My sata hard drive works out of the box with, I did not tested raid support or hot swap capabilities.

Problem USB:
There are only 2 USB sockets on the back of the motherboard. In my opinion this is too little. There are however still 3 USB connectors for expansions cabels on the motherboard.

Problem noise:
There is an AMD Geode 1750 (1399MHz) CPU in the system. This is a CPU based on the Athlon XP and has a 14W power consumption. There is a poorly designed heat sink and a very noisy 12V (Volt) fan with an RPM signal(fan rotation speed) on it. I bought a Zalman Fanmate II for controlling the fan between 5V and 11V. On 5V the fan's noise is acceptable and it is about the same as the noise from the 2.5" HHD I use. I guess this will be around 22dB of noise production.
CPU Fan: 2145 RPM (min = 0 RPM)                  
CPU Temp: +65°C (high = +255°C, hyst = +0°C) [thermistor]
The motherboard will automatically power down if the CPU temperature reaches a temperature of 85 degree Celsius, this is a last resort safety function. If I run the CPU fan on 5V I have to keep the case open, otherwise the CPU will turn to hot. This is because of the bad airflow which makes it difficult to get the heat? air out of the case.

I think the VIA EDEN CPU has a better thermal design than the AMD GEODE CPU. The GEODE is more powerful but uses more power and creates more noise because of its load cooling fan. But working with the Jetway 7F3 type motherboard, using my Linux xubuntu distribution with XFCE desktop environment, has been a pleasant experience. The start-up time of most programs is under one second and overall system response is fast enough. I wish there was a processor that could be configured with these variables: speed, power, heat, noise. To create a customizable set-up.

Problem with case:
The Morex 3688 is my favourite mini-ITX case but it is not perfect, however it will do. We have one of a BIG problem, the motherboard does not fit in the case! The heat sink and fan will make the motherboard stick out to far and makes it impossible to close the case. The design of the heat sinks and fan is poor,  hot air is blown on to the other chipsets heat sinks. And the heat can't get out of the case very well, compared with the VIA EN12000E that fits perfectly without any fan, this motherboard fits like hell.

Problem power cable:
The power cable is just long enough to reach the ATX power connector on the motherboard. I had to remove the plastic cable binders to release some tension of the cable. But there is still a lot of tension left on the power cable. This can never be good. The cable also lies above and around the fan of the CPU and is blocking the airflow, which is very bad.

Prices including taxes:
96,00EUR Morex Cubid 3688 (mini-ITX, 60W extern, Zilver)
175,00EUR Jetway J7F31750 AMD GEODE 1400MHz Mini-ITX
4,50EUR Zalman Fan Mate 2 Fan Controller 5~12V
24,00EUR Jetway Adapter 1xGiga Lan

Power consumption:
I measured a maximum of 45W power consumption on full load, this includes:
adapter
power supply
motherboard
hard drive
memory

Behaviour:
Despite the lack of good audio and 3D driver support, it is still a pleasant system, not ideal, but it will do. The AMD GEODE CPU is more powerful than the VIA C3, but compared with the EN12000E things are not shockingly faster. The CPU runs with a nice speed, a few more years of research and development and we can have a passive cooled CPU, which will achieve the same speed or even higher. The GLAN Ethernet is CPU powered and with an NFS server and client it will pump data across with 11 MB/s. This is acceptable for a low price affordable RTL r1000 driver based chipset.

I wanted to have GLAN Ethernet so I bought an AD1RTLANG add-on module. These add-on modules are a very nice  feature of the Jetway motherboards.

Conclusion:
If you want mini-ITX performance for a low price you can buy a Jetway 7F3E system.
Compared with the VIA EN15000 this system is faster but is lacking a 3D video driver and has noisy audio and a noisy CPU fan. If you want a silent system you can buy the VIA EN12000E which is designed better. If you want full Linux support don't buy either of these systems but buy something Intel based for around 2 a 3 times the money. I still have to find a fully Linux supported mini-ITX system with passive CPU under &#8364; 300,-. Also the sound chip is bad, but does work if you can tune up a custom .asoundrc file.

---

### Post by TuxCrafter on 2007-03-27
Test Report Jetway 7F3E - Mini-ITX Motherboard

The attachment contains the report inclusive benchmarking exclusive pictures

---

### Post by jfdill_2 on 2007-05-12
Cool, I am just now considering to get a Jetway based system, so this article is very useful food for thought.  I am going to use this primarily as a "headless" box or just basic web browsing and such, looking for something that consumes less power than my AMD Linux box, but is faster than my Debian-based NSLU2.

---

