---
title: "Black Screen @ Feisty Live"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by Black Sliver on 2007-08-26
Hi there!

First here's my hardware:
Board: Asus P5N32-E SLI
CPU: Core 2 Duo E6600 (64bit)
HDD: 2x 320GB, Raid0 onboard controller (no comments on this plz)
Graphic: 2x nVidia gForce 8800 GTS 320MB SLI, Display connection via DVI
LAN: 2x GBit-Lan (worked in Dapper)

What i did so far:
I've set up the Raid0, installed WinXP to test my new hardware / SLI, made the following BIOS Settings to boot into Dapper Live (x86-Disc):
Power -> APM Configuration -> HPET Supoort -> Disabled
Tuning Section -> everything standard

Tried to start Dapper-Live in "normal" Mode -> Error Message by X
Tried to start Dapper-Live in "safe graphics mode" -> worked

I got the Feisty Live 64bit-Image, burned it on disc and when i boot it i get to the Live-Menu.
Selecting "Start or Install Ubuntu" leads to 2 Loading-Lines at the top, "kernel alive" at the bottom and then just a black screen. Selectiong "Safe graphics mode" makes the same.
I made no changes to VGA (the F4-Menu).

Im not sure what the problem is but i think even with the black screen, the linux is still running "behind" (cd activity), so i think its about my graphic card :( 


[size=3][EDIT][/size]
What i'm going to try is [http://www.realriot.de/index.php/2007/04/25/fakeraid-howto-ubuntu/](http://www.realriot.de/index.php/2007/04/25/fakeraid-howto-ubuntu/)
To use this guide, i absolutely need the live-disc, no change with alternate...


[i]so long..
Andy[/i]


PS: I made memtest x86 last night.. about 7 hours, no errors. CD-drives seems to be okay as the other hardware (2days old)

---

### Post by Hoenheim on 2007-08-26
I had the same problem when I tried to use the 64bit cd, but the x86 cd works perfectly so I suggest you use x86.

---

### Post by Black Sliver on 2007-08-26
well.. thanks for that tip :) 

I'm going to try it out today. Anyone has background informations about this? Shouldn't be the standard-video-driver the same on x86 and x64?? 


[i]so long..
Andy[/i]

---

### Post by Black Sliver on 2007-08-26
I've tried the x86 disc. I see the loading-bar with the ubuntu-logo in both graphic modes now.

BUT

Using normal start (not safe graphics): (after loading is finished an x is going to run)
```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-15-generic #2 SMP Sun
Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 26 17:54:35 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation G80 [GeForce 8800GTS]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"

(WW) NV: No matching Device section for instnce (BusID PCI:1:0:0)
found
(EE) NV(0): No display device found
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```
Before Loading some nv-Module its an unknown nVidia chipset, after loading that module it's (as listed above) nVidia GeForce 8800GTS 


Safe graphics mode: (after loading is finished)
There is a blinking underscore displayed some seconds, CD-rom is working. After a while the underscore disappears, the screen is just black. CD-rom drive is still working half a minute or something like.


Please HEEELP :cry:


[i]so long..
Andy[/i]

---

### Post by merlinus on 2007-08-26
You can try Safe Video Mode.  If you can get to a CLI via Crtl-Alt-F1, try this:

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
or reboot.

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

Or you can use the text-based Alternale cd, which will avoid video problems.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by Black Sliver on 2007-08-26
Thanks for answer!

> You can try Safe Video Mode. If you can get to a CLI via Crtl-Alt-F1, try this: WHEN?

> Or you can use the text-based Alternale cd, which will avoid video problems.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Got it a while ago because i was about to install ubuntu with it. 
But the problem is that i need a running linux to install ubuntu on raid0 (see first post, @ edit)

---

### Post by merlinus on 2007-08-26
Often Safe Video Mode (from the menu screen) will get you to a command line, if nothing else.

If it comes up with some sort of error message, however, Ctrl-Alt-F1 (or Ctrl-Alt-F2) may get you there.  If so, then try what I suggested.

Other than that, I am at a loss about RAID configurations.  You might do a forum search.

-merlin

---

### Post by Black Sliver on 2007-08-26
Well ill try it soon :)
I think its nothing about raid coz the live disc should not stop if the raid is not accessible.


[i]so long..
Andy[/i]

---

### Post by Black Sliver on 2007-08-26
Starting ubuntu without safe graphics leads to an x-server-error-report (as described above). When I hit ctrl+alt+F1 it takes me to the "command line".

The problem is that i have absolute no idea what to set up within "sudo dpkg-reconfigure xserver-xorg". Video card is detecded correctly (nv gForce 8800 GTS) but i have no plan what to enter for PCI (got 2 graphic cards) and the other switches / modules.
"versa" (if this is vbe) is on by default ?!

Starting ubuntu w/o safe graphics takes me to the thing described in some post above. If i hit ctrl+alt+F1 while the screen is black i get to the command line too. If i try startx here the following message appears: ```
xauth:  creating new authority file /home/ubuntu/.serverauth.9235


Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

stop
```


Maybe you can analyze the error message i got in some post above?
Tanks so far :)


[i]so long..
Andy[/i]


PS: Is it normal that theres nothing but the loading-bar displayed while ubuntu feisty is loading?
PPS: Is it possible that i'm the first one trying to run ubuntu with such a master piece of hardware? Oo

---

### Post by merlinus on 2007-08-26
As my original post suggested, select vesa.  Even though your nvidia may be detected, the drivers will not work.  That is the problem.

Otherwise try the Alternate text-mode install cd.

-merlin

---

### Post by Black Sliver on 2007-08-26
> As my original post suggested, select vesa. Even though your nvidia may be detected, the drivers will not work. That is the problem. Well.. i think were talking about 2 different things :( 
Where and how to select it exactly? 

> Otherwise try the Alternate text-mode install cd. here's the problem: 
1st: even after installing it: i'll have the same problem with my graphics!?
2nd: i have to set up my raid in linux (using dmraid) BEFORE installation.Thus i have no acces to that before setting up my hdd for installation, i cannot use the alternate disc.
So i think the above way is to go :) 

> PS: Is it normal that theres nothing but the loading-bar displayed while ubuntu feisty is loading?
Whats about this?


[i]so long..
Andy[/i]

---

### Post by merlinus on 2007-08-26
You can edit the boot line and remove "quiet."  Then you will see exactly what is happening.

-merlin

---

### Post by Black Sliver on 2007-08-26
> **Black Sliver said:**
> Well.. i think were talking about 2 different things :( 
Where and how to select it exactly? 
lol.. its at the first screen of the config-tool


(In normal graphic mode) After changing this, leaving the rest to default values (my graphic card name and all the modules) and starting the x-server again, i get nothing :( 
No error, but black screen. Same behavior as described above for safe graphics mode.

Any idea? Maybe some other changes for the x-config?


[i]so long..
Andy[/i]

---

### Post by merlinus on 2007-08-26
If you selected vesa and still nothing worked, then all I can suggest is playing with some of the other options that come up with

sudo dpkg-reconfigure xserver-xorg

And if you cannot use the Alternate text-based install cd because of RAID issues, I do not know what else to suggest.

Sorry....

-merlin

---

### Post by Black Sliver on 2007-08-27
What if .. i deactivate raid and make use of the alternate disc.
After Setup im going to boot into ubuntu and it will be just the same sh*t as now ?! Or what is different to the live-mode?


[i]so long..
Andy[/i]

---

### Post by Black Sliver on 2007-08-27
OMFG...

I've just changed the Bus-Id from Bus:10:0:0 to Bus:1:0:0 and everythnig worked :)
Nothing about vesa drivers or flags ;) 

Thanks for support!
[i]so long..
Andy[/i]

---

### Post by Ferrixman on 2007-12-21
Can you explain me STEP by STEP how you managed to install ubuntu 64-bit, please?

Mainboard: p5k premium
cpu: core 2 duo 6750
video: nvidia 8800 gts 320mb
hd: 2x500gb raid0

Tnx in advance

---

