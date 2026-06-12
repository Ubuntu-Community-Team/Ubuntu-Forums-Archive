---
title: "Processor temp problems"
date: 2014-12-23
forum: Hardware
---

### Post by jammydodger2 on 2014-12-23
Hi All 
I have a compaq cq61 with upgraded processor from sempron to turion II ultra dual core 2.4ghz m600 (it has been installed for quite a while using on windows until I switched to ubuntu)
when I play the game oolite my laptop gets quite hot and after an 1.5-2hrs or so it crashes to black screen without any warning except fan blowing hot maybe IMO
 I have dual boot of windows 7 and ubuntu on laptop(altough rarely use WIN7 now)
I have run sensors command from terminal and get idle of 53-56
and 63-66 when playing game Oolite   	 	 	 	
**should this chip show two cores temps or just the one?**spec below fron terminal
Cant find anything to change in BIOS regards fan except enable and disable (always  enabled)
AMD driver say up to date for running WIN7 unsure if BIOS is correct for 
Have 
turion II ultra dual core 2.4ghz m600 
6gb Ram
150 HD
ATI Radeon HD4200 336MB GPU RS880M (I believe this is not great spec)
Any help appreciated 
JD




   Notebook-PC:~$ sensors
 acpitz-virtual-0
 Adapter: Virtual device
 temp1:        +56.0°C   
 

 k10temp-pci-00c3
 Adapter: PCI adapter
 temp1:        +56.0°C  (high = +70.0°C)
                        (crit = +115.5°C, hyst = +110.5°C)

---

### Post by Mike_Walsh on 2014-12-23
Hi, and welcome to the forums.

You may find these two links give some insight into the behaviour of the AMD thermal sensors:-

[http://help.argusmonitor.com/index.html?TemperaturemeasurementforAMDCPUs.html](http://help.argusmonitor.com/index.html?TemperaturemeasurementforAMDCPUs.html)

[http://forums.guru3d.com/showthread.php?t=376926](http://forums.guru3d.com/showthread.php?t=376926)

Quote:-
> [COLOR=#000000]turion II ultra dual core 2.4ghz m600 [/COLOR]
[COLOR=#000000]6gb Ram[/COLOR]
[COLOR=#000000]150 HD[/COLOR]
[COLOR=#000000]ATI Radeon HD4200 336MB GPU RS880M (I believe this is not great spec)[/COLOR]

Makes little or no difference..! In the open-source community, you will find that there are more people running 'old' hardware, than there are running cutting-edge. One of the attractions of using open-source OSs is the ability to keep hardware running, that many people would consider to be only fit for the scrapheap. So, to be blunt, running the top-of-the-range CPU, motherboard, graphics card, etc., doesn't really count for very much.....and may, in fact, present MORE problems than older hardware, since Linux developers don't get PAID for making sure new stuff 'works' almost the instant it's released...

My 'newest' machine is 9 years old, and my oldest is 12.....and they all, without exception, run variants of Linux.

Hope the links help.


Regards,

Mike.

---

### Post by Yellow Pasque on 2014-12-24
I've got a triple core Phenom and k10temp only shows one core.

If you're going to use your laptop for long gaming sessions, then consider a laptop cooling pad.

---

### Post by jammydodger2 on 2014-12-27
Thanks for replies and link on amd 
Regards
JD

---

