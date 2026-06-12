---
title: "Toshiba laptop overheats in latest Kubuntu?"
date: 2013-06-18
forum: Hardware
---

### Post by RollingSmoke on 2013-06-18
Hello all, 

Recently looked up some overheating problems for people with Toshiba laptop especially. I read installing lm-sensors would fix the problem. 
I followed the guide [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto), and auto detect said my sensors was already loaded into my modules and no configuration is necessary. 

Though using the software PSensors, it shows my temps around 170 degrees average running idle no programs running. Random restarts usually follow after using the computer as normal. This does not happen when I boot into windows, so I know its probably a sensor problem(sounds like im talking about my car), or something not controlling the fans properly. 

All help is much appreciated
-Jeremy

---

### Post by QIII on 2013-06-18
Hello!

Sensors do not help keep your machine cool any more than your speedometer controls your speed on the highway.  Installing a speedometer will not slow you down  :)

What are the hardware specs for your machine?

---

### Post by RollingSmoke on 2013-06-18
Its a Toshiba Satellite L355D-S7815 laptop. 

Sorry for late reply, fairly old laptop.

---

### Post by Yellow Pasque on 2013-06-18
[www.cnet.com/laptops/toshiba-satellite-l355d-s7815/4505-3121_7-33155829.html](www.cnet.com/laptops/toshiba-satellite-l355d-s7815/4505-3121_7-33155829.html)
It's got a Radeon 3100 GPU, so perhaps setting it a lower power level would help:
[http://askubuntu.com/questions/162073/what-prevents-setting-ati-radeon-power-profile-from-boot-and-retaining-it-afte](http://askubuntu.com/questions/162073/what-prevents-setting-ati-radeon-power-profile-from-boot-and-retaining-it-afte)

---

### Post by azitizz on 2013-06-19
My L350 D is also experiencing higher heat in Ubuntu 13.04. It was fine in the other distibutions. I alos installed a new herd drive, the specs on my laptop are :

AMD Athlon 64 X2 QL-65 / 2.1 GHz ( Dual-Core )

750.0 GB SATA - 7200.0 rpm hard drive

ATI Radeon 3100 Shared video memory (UMA)

I have Psensor installed and monitoring, however Im not sure how to distinguish which temperature is reading what. It only has temp1, and temp1 (I was expecting CPU, Harddrive...) Doing nothing more than emails and reading the news one temperature (the second "temp1" seems to climb frequently to 80C and has even gone up to 90C. The other one also goes to 80 but tends to stay a little cooler but hovers around that ballpark. Fan is going constantly. Sometimes when the fan is working but not excessively hard it has kicked in an emergency shutdown. Anything I missed installing on the new version of Ubuntu?

I ended up installing a 32 bit version as the 64 version of 13.04 wouldt work once installed, even though it worked with off a USB flash drive  in trial mode. Once installed the 64 bit version would have the resolution way off and the mouse wouldnt work, either by USB or on the laptop. So I couldnt do anything....
Any ideas?

---

