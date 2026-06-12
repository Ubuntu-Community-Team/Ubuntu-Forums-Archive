---
title: "Can't use Proprietary Drivers for Radeon HD6670 and need help on my CPU."
date: 2014-11-10
forum: Hardware
---

### Post by Finrod_Inglorion on 2014-11-10
Hi,

pretty much new to any *nix-Distro. Installed it a few days ago and killed my Windows partition somewhere during that. Kinda stuck on Ubuntu for now until i get some flashdrive to create a bootable USB-Stick again. Not that it matters too much, loving Ubuntu.

Edit: Forgot to mention. I'm on 14.04.1 LTS. I guess that's important to know.

Now to my problems...

I've got a AMD A6-3670 APU with Radeon(tm) HD Graphics CPU and my discrete GPU is a xfx Radeon HD6670. 
My issue with it being is that i can't use either the Proprietary drivers from the System Setting and i already tried manually installing the AMD Catalyst 14.9 Drivers. On either of these i'm stuck at boot and when i boot up using "nomodeset" instead of "quiet splash" in Grub i end up getting stuck at "System V Runlevel Compatibility" which seems to be related to the Drivers. I kinda need help getting them set up since the Open Source drivers are kinda slow and i need my GPU. 

On a note to that:
Back then I bought the 6670 because it can be run in CrossfireX in combination with the APU on my A6-3670. That combination is a 6530D.

 Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6530D]
 Advanced Micro Devices, Inc. [AMD/ATI] Turks XT [Radeon HD 6670/7670]

Those are the GPUs running on this PC. I'm just lost at how to setup up any proprietary drivers for these. Had to fix it in tty several times already.

---

Second Problem:

I don't know if it's really a problem and simply standard but...

The clockspeeds of all 4 cores a dynamic and usually hovering around 800mHz. I also noticed that when i run WINE/POL my CPU Load wouldn't go up according to the Sysmonitor Screenlet i got running. They're all around 0% and right underneath it it would say that Firefox for example is using 27% of my CPU. I don't think the Screenlet is accurate but i also don't think my CPU is being used to it's fullest when running CPU heavy applications. (Btw, it'd show WINE running at 130% CPU sometimes and another WINE command running at 80%, which i find weird. May be just WINE being funky.)

So I'd like to know what i can do to either keep the clockspeed either static or get the CPUs to actually crank up when they're needed.

If there's any logs you need just mention it and i'll post them. No idea what i should post as of now.

Greets, 
Finrod

[h=3][/h]

---

### Post by grahammechanical on 2014-11-10
Could it be that what you call "CPU heavy applications" are in fact not actually that heavy, especially with 4 cores? 

As for the graphic set up. well, that is beyond my experience.

Regards.

---

### Post by pqwoerituytrueiwoq on 2014-11-10
i would suggest sticking with the open source driver
for better performance i suggest using the xorg edgers ppa and the latest 3.18 kernel
1. purge your catalyst driver
```
sudo apt-get purge fglrx* && sudo apt-get autoremove --purge && sudo rm /etc/X11/xorg.conf
```
2. add repo source and update local packages list and install new stuff
```
sudo apt-add-repository ppa:xorg-edgers/ppa -y && sudo apt-get update && sudo apt-get dist-upgrade -y
```
3. update kernel
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)
here is step 4's command for the latest kernel
```
KernelUpdateChecker -r \*
```

personally i have found APU performance to be a bit lacking in the GPU area under linux compared to intel

---

### Post by Finrod_Inglorion on 2014-11-10
> **grahammechanical said:**
> Could it be that what you call "CPU heavy applications" are in fact not actually that heavy, especially with 4 cores? 

As for the graphic set up. well, that is beyond my experience.

Regards.

Well... I would call CS:GO CPU heavy already. For it to get high FPS you'd need a stronger CPU moreso than a stronger GPU.

> **pqwoerituytrueiwoq said:**
> i would suggest sticking with the open source driver
for better performance i suggest using the xorg edgers ppa and the latest 3.18 kernel
1. purge your catalyst driver
```
sudo apt-get purge fglrx* && sudo apt-get autoremove --purge && sudo rm /etc/X11/xorg.conf
```
2. add repo source and update local packages list and install new stuff
```
sudo apt-add-repository ppa:xorg-edgers/ppa -y && sudo apt-get update && sudo apt-get dist-upgrade -y
```
3. update kernel
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)
here is step 4's command for the latest kernel
```
KernelUpdateChecker -r \*
```

personally i have found APU performance to be a bit lacking in the GPU area under linux compared to intel

So, i'm on Linux 3.18.0-031800rc4-generic now and i got the xorg edgers ppa.
I'm not that concerned about the APU. Been using the discrete GPU only and disabled CrossfireX there since it'd otherwise cause Microlags which are quite annoying. Just want to get either the CrossfireX working or the 6670 using Proprietary Drivers. If that's possible.

Oh and... How would i get rid of Vsync on the xorg edgers ppa? Noticed that CS:GO for example is forced to 60 FPS whilst Vsync is disabled in the video settings.

Regards, 
Finrod

---

### Post by pqwoerituytrueiwoq on 2014-11-10
i am not very familiar with amd's gpus, been using nvidia as there drivers are on par with the windows counterpart where as the amd drives are not close at all
[http://stackoverflow.com/questions/17196117/disable-vertical-sync-for-glxgears](http://stackoverflow.com/questions/17196117/disable-vertical-sync-for-glxgears)
you will need to generate a xorg.conf file and make said edit to the file 
xorg.conf goes ins /etc/X11/

it is also possible the updated catalyst driver in the xorg edgers ppa will work for corssfire, however in my exp with nvidia the driver will not build with very new kernels, for example on 14.04 i cant use the 3.17 kernel unless i use the open-source nouveau driver, i have the same limitation with virtualbox (can by bypassed by pulling software from newer releases like utopic and vivid)
so if you cant build your catalyst driver on the 3.18rc4 try it on 3.17 and 3.16
here are the commands to grab those kernels (grub will boot the newest installed kernel by default, but for some reason a rc kernel comes before a release kernel, eg 3.18rc4 reads as newer than 3.18 final)
```
KernelUpdateChecker -r \* -f -v 3.16
KernelUpdateChecker -r \* -f -v 3.17
```

---

### Post by Finrod_Inglorion on 2014-11-11
So... Using a different Kernel for the Proprietary drivers didn't work. I still get stuck at "System V runlevel compatability."

And i also can't generate a xorg.conf for some reason.  

```

finrod@Luzifer:/etc/X11$ sudo Xorg -configure
[sudo] password for finrod: 
(EE) 
Fatal server error:
(EE) Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.
(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help.
```

Is what i'm getting as a result and there's not xorg.conf to be found in /etc/ or /etc/X11.

---

### Post by pqwoerituytrueiwoq on 2014-11-11
i forgot you have to switch to a tty and turn lightdm off then do that
save this to a file 
```

#!/bin/sh
sudo service lightdm stop
Xorg -configure
sudo cp xorg.conf /etc/X11/
sudo service lightdm start

```
save all open docs and close up stuff, unsaved data will be lost
press Ctrl + Alt + F2
login and run
```
sh /path/to/saidFile
```

---

