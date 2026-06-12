---
title: "Screen issues Ubuntu 16.04 + Hybrid NVIDIA GPU"
date: 2017-01-18
forum: Hardware
---

### Post by jappudesi on 2017-01-18
I am a Linux and Ubuntu **newbie**, and converted an old laptop to run Ubuntu (sole OS). The Machine is Sony Vaio SZ VGN-SZ75GN/B, with Intel Core 2 Duo, 3GB RAM,  and NVIDIA GEFORCE 8400M GS GPU in a hybrid graphic configuration. Ubuntu is 16.04 LTS 32bit, and chksum verified before installation. Haven't been able to update anything yet.


The problems are: 


1. Sometimes at start-up, the screen just shows a black and white pattern and nothing happens after that and i have to shut the machine down (once was a physical switch induced shut-down)


2. Sometimes it does start up, but as soon as I click the Ubuntu Icon, the screen goes garbled for a while, and resets when i click some other area


3. Starting any other app like Calc or Firefox takes a long time and the fan runs at high speed. Each time I've managed to start the comp, have had to shut it down after a while due to screen garbling.

4. I tried the following commands and their results are:


        sudo grep -i switcheroo /boot/config-*


**        /boot/config-4.4.0-31-generic:CONFIG_VGA_SWITCHEROO=y**
**        /boot/config-4.4.0-59-generic:CONFIG_VGA_SWITCHEROO=y**


        lspci -v |grep VGA


       ** 01:00.0 VGA compatible controller: NVIDIA Corporation G86M [GeForce 8400M GS] (rev a1) (prog-if 00 [VGA controller])**

**UPDATE:** This morning I managed to open the application updater through the icon and see that there are multiple graphics adapters (2 NVIDIA , one noveau, and 2 for the onboard one - apologies can't attach a screenshot as the screen went on the blink immediately after.. Additionally, tried **locating** Switcheroo, but got a message saying **file or folders not found** .... adding this info as it may be of some diagnostic value


Please advise what can I do further to fix these issues. I don't intend to run games or like, so would be ok to use one or the other card.


Much appreciated...

---

### Post by jappudesi on 2017-01-18
UPDATE 2:

I managed to get most of it working now except a couple of points 

Steps taken: 


[LIST=1]
[*]opened the driver page through the system settings-->Software and Updates-->Additional Drivers, and disabled the onboard intel GPU.
[*]selected NVIDIA 340 (proprietary, tested) as driver
[*]reduced swappability to 15
[/LIST]

Results: 
[LIST=1]
[*]Display is fixed
[*]Fan noise is gone down dramatically.
[/LIST]

I have the X.Org driver noveau still installed along with Nvidia **304 **(proprietary), which I want to remove. How do I do that pls help

thanks in advance.

---

### Post by QIII on 2017-01-18
Hello!

vgaswitcheroo is best used with AMD/Intel hybrids -- if it still works in recent releases.

The analogous software for Nvidia is Optimus.

---

