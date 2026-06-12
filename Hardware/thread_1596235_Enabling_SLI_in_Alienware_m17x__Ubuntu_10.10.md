---
title: "Enabling SLI in Alienware m17x / Ubuntu 10.10"
date: 2010-10-14
forum: Hardware
---

### Post by HellraiserAJ on 2010-10-14
[FONT=Palatino Linotype][SIZE=2]Hi,

I did a fresh install of Ubuntu 10.10 (32 bit Desktop Edition) on my Alienware m17x. I am a linux newbie and i referred to various forums and messages before i typed this. 

To note, I installed the NVIDIA drivers from System -> Adminstration ->Additional drivers. The laptop Seiko display works fine but there are some problems as outlined below. [/SIZE][/FONT][FONT=Palatino Linotype]
[/FONT][FONT=Palatino Linotype][SIZE=2][B]
Problems :[/B][/SIZE][/FONT][FONT=Palatino Linotype]

**1. My graphics cards are GeForce 260M in SLI mode (dual cards). However the graphics card that has been identified by NVIDIA is GeForce 9400 which is the onboard graphics. **Maybe if i correct this one, my other problems might go off but not sure. 
[I][B]
Attempted 

[/B][/I]Tried installing the newer NVIDIA driver from [http://www.nvidia.com/object/linux-display-ia32-260.19.12-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.12-driver.html). Installed from ROOT with TELINIT 3 and could not run command *nvidia-xconfig -a *to enable both GPUS. Got error as API MISMATCH: NVIDIA Kernel has version 260.19.06 whereas the NVIDIA Component has 260.19.12. 

When i rebooted my system, the resolution was worse than before. 

I then tried to remove the restricted drivers and do a fresh install of the downloaded driver by deactivating it and reinstalling the drivers. The screen went blank on reboot. 

So i had to resort to uninstalling the newer NVIDIA drivers and installing the restricted drivers to make the display look better. 

<EDIT> I checked the BIOS and saw that the HYBRID SLI had been disabled. I tried enabling the HYBRID SLI in BIOS and then do the* nvidia-xconfig -a *after reboot, but i got the following error. [/FONT][ATTACH]172265[/ATTACH]
[FONT=Palatino Linotype] 
So as of now, i am only running the graphics from the onboard GPU and not the SLI Cards present in my laptop. Pls help in this.

**2. Pressing CTRL + ALT + F1 thru F6 gives blank screen (no display no backlight even). I am able to switch back to X by pressing CTRL + ALT + F7. Also CTRL + ALT + BACKSPACE does not restart X as it is supposed to.**

I believe that this is due to the resolution conflict.

[B]3. Using an external monitor (Dell S2409W) with my laptop (thru VGA)

[/B]NVIDIA does recognize the monitor in NVIDIA-SETTINGS as shown in the image. 

[/FONT][ATTACH]172257[/ATTACH][FONT=Palatino Linotype]

I want separate display as TwinView is messing up with my laptop resolution and i cannot access the top / bottom panels etc. I want to use my monitor only for viewing and not the laptop display.[/FONT]
[FONT=Palatino Linotype]
[I][B]Attempted:
[/B][/I]
I did try to enable the monitor and click on [/FONT][FONT=Palatino Linotype]but the monitor does not seem to be receiving any signal from the laptop. I did a reboot as well but that did not work too.

[SIZE=2]I am also attaching the XORG.CONF file for reference. [/SIZE][/FONT][ATTACH]172258[/ATTACH]
[FONT=Palatino Linotype][SIZE=2]
I have tried to be as clear as possible in my wordings but pls dont hesitate to ask me any further details. Pls help me out.

Thanks
AJ[/SIZE] 
[/FONT]

---

### Post by HellraiserAJ on 2010-10-14
](*,)](*,)](*,)](*,)[FONT=Palatino Linotype]**SHAMELESS BUMP**[/FONT] ](*,)](*,)](*,)](*,)

[FONT=Palatino Linotype]Cos i have spent the last 3 days trying to solve this and still i couldn't. 

Pls guide me or direct me... 

AJ   [/FONT]

---

### Post by drbcladd on 2010-10-28
(1) the 9400 is the on-board graphics.

(2) To date, hybrid graphics is not supported in Linux. There are some projects that are working on it. As of a month ago none of them were stable.

(3) In the BIOS, to use the good stuff, you want hybrid graphics disabled and you want the integrated graphics disabled. 

(4) I am using 260.19.12. You can stop and start X, assuming you are using Gnome, with the commands

% sudo service gdm stop

The X server will halt. Alt-F2 should give you a separate screen where you can log in. Then you can execute the nvidia driver. 

To restart the server, the command

% sudo service gdm start

and you can see the driver start and GDM will let you log in.

(5) I am not, right now, using SLI. I actually found your post by searching for SLI instructions.

---

### Post by drbcladd on 2010-10-28
So, I ran

% sudo nvidia-xconfig --sli

rebooted, and the configuration reports using both cards. I am so happy right now (that it was that easy). 

Note that the m17x resets the graphics mode (in the BIOS) whenever it is started while unplugged. That is a major pain when I want to run in the most battery-draining mode all of the time (if I can only go off AC power for ten minutes, that is fine).

-bcl

---

### Post by HellraiserAJ on 2010-10-28
You SIR have no idea how you many hours of effort you have saved me from. THANK YOU SO MUCH. i disabled both the hybrid and on board graphics and rebooted and VOILA... the screen resolution looks perfect and everything works fine.... 

I even ran the command you gave me 
% sudo nvidia-xconfig --sli=On and it is working well. 

I have never been happier .... for this issue had me busy for the past 1 week and now it is resolved...

If you dont mind, i do have one more question.

I usually use only my external monitor and disable the laptop one. However currently if i close my laptop lid, the external monitor also blanks out. These are the only options in the Power management menu. 

But i worked around it by following the fix here - [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/390816](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/390816) Now my monitor is the only display i am using. 

however, pressing CTRL  + ALT + F1 brings up the terminal in the laptop display and not on the monitor. How do i fix this ?

You have already done a lot. Thanks a ton. 
AJ

---

### Post by drbcladd on 2010-10-28
Really good question. Never used the machine in that configuration so I cannot answer your question.

Glad the other stuff helped.

---

### Post by HellraiserAJ on 2010-10-28
its alright... as of now i can mark this issue closed and will ask the TTY question as a separte one...

Thanks again...

AJ

---

