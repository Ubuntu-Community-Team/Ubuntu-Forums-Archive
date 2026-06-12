---
title: "Nvidia FX5200 unable to install driver"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by paul_2978 on 2009-06-07
Hello

Im having real difficulties with installing the driver for my FX5200 graphics card.

I have tried using ENVY which is installed and says:

NVIDIA
        173.14.16-oubuntu1 COMPATIBLE RECOMENDED this is ticked for both

I selected this and then restarted the computer however it just boots to a blank screen after loading the initail ubuntu loading screen. If I restart again it does load in but im on 640x480 :(.

If I goto 
System - > Prefernces -> Display

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"
           
If I click YES it opens the NVIDIA X SERVER SETTINGS.

Under X SERVER DISPLAY CONFIGURATION - the highest I can set my display is 640x480???????

when I do lshw in terminal

I get 

display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia

Iv been reading all over the place googling like mad but this is one I reall cant solve. I'v removed envy reinstalled enter safe mode and tried using the fix graphics problem.  

Tell me what you need and I'll provide all the information to help me fix this problem!

Thanks in Advance.

Im stumped on this one :(

---

### Post by hal8000 on 2009-06-07
You make it difficult to answer as you dont quote which version of Ubuntu you use.
Under Jaunty, 9.04, go to system, admin, hardware drivers.

This runs "jockey" and it will display a list of proprietary drivers for your Nvidia card. Recommended version is Nvidia 180, it will download the drivers, modify xorg.conf, next reboot, everything should be ok.

I suggest uninstall envy, and try the above. If youre not using Jaunty you need to state which version as things may work slightly different, hope that helps.

---

### Post by paul_2978 on 2009-06-07
Im using 9.04

When I go to System -> Administration -> hard Ware Drivers

There is a green circle = curently being used next to

NVIDIA accelerated graphics driver(version 173) [Recomended]

So Im unsure whats the issue should I remove ENvyNG again??

I have no idea about x.conf as this is not something I am used to dealing with :(

---

