---
title: "How to configure Plasma after removing video card"
date: 2020-02-03
forum: Hardware
---

### Post by cedric9 on 2020-02-03
My knowledge of Linux / Ubuntu is somewhat limited, so I will apologize in advance for getting some of the below terminology wrong.  


To begin with, I recently began experiencing a problem in which my PC would reboot two or three time during POST, and after some expermintation, I was able to determine that my PCI Express video card was at fault.


I removed my video card and plugged my monitor cable into the onboard VGA port built onto my mother board, changed settings in BIOS, and the rebooting problem during POST went away.  However, as Ubuntu is booting, Plasma no longer loads, and I’m simply left with a black screen which I cannot do anything with.


I’m assuming that my installation of Ubuntu is still looking for my old PCI Express card which I removed, and that it doesn’t know to utilize the built in on board video until changes are made in its settings?  


However, if I reboot my computer I’m able to get to the menu which contains an option for Generic Recovery Mode, and from there I can get to the Root prompt, but I don’t know what to do here.


I remember playing around with Red Hat Linux about twenty years ago, and back then I remember that there was a command called “./Xconfigurator” which would allow a user to make changes to their system in case X Windows did not load.


I guess my question is, Is there any utility I can launch at the Root command prompt which will allow me to make changes to my settings so that the system will use my onboard video instead of the now missing PCI Express card?  


As I said, I’m pretty sure that my video card was the cause of my initial rebooting problems, because since I’ve removed it the rebooting problems have gone away.  Also, I appreciate everyone’s paitence given the fact that I’m probably not using the correct Linux terminology when trying to describe my problems.   - Any info greatly appreciated.  (Also, if I boot my system using an Ubuntu DVD, the graphical user interface seems to load fine.)




System Info:


KDE Plasma Version:  5.12.9
KDE Frameworks Version:  5.44.0
Qt Version:  5.9.5
Kernel Version:  4.15.0-76-generic
OS Type:  32-bit




Processors: 4 x Intel Core 2 quad CPU Q6600 @ 2.40 Ghz
Memory: 1.9 GiB of RAM

---

### Post by SeijiSensei on 2020-02-03
When you get to the root prompt, first mark the file system as writable with the command:
```
mount -o remount,rw /
```

Next, see if you have an /etc/X11/Xorg.conf file. If so, rename it like this

```
mv /etc/X11/Xorg.conf /etc/X11/Xorg.conf.old
```

then type "exit" and reboot.  Any better?

You may not have this file. If not, I'm afraid someone else will have to help.

---

### Post by cedric9 on 2020-02-03
> **SeijiSensei said:**
>  You may not have this file. If not, I'm afraid someone else will have to help.

Hmm...Unfortunately I don't seem to have a file named [COLOR=#000000][FONT=&quot]Xorg.conf 

[/FONT][/COLOR]I included the below list of the files in my /etc/X11 folder just in case I'm missing something.  


```
cedric@farm-400:/etc/X11$ ls


app-defaults  
default-display-manager  
rgb.txt  
xkb
Xreset.d
Xsession
Xsession.options  
XvMCConfig
cursors      
fonts
xinit
Xreset
Xresources
Xsession.d
xsm
Xwrapper.config
```

---

### Post by CatKiller on 2020-02-03
> **cedric9 said:**
> As I said, I&#8217;m pretty sure that my video card was the cause of my initial rebooting problems, because since I&#8217;ve removed it the rebooting problems have gone away.

Not necessarily; failing power circuitry might also cause your computer to struggle to start because it can't drive the load of the graphics card as well as everything else, even if the graphics card is fine, as an example. But, whatever the cause, not having the graphics card in means that it can start properly, which is good.

You've not given us enough information to go on, though. In particular, you've given us no information on the graphics that you were using before or the graphics that you're using now. AFAIK, the Q6600 doesn't have integrated graphics of its own, which means whatever you're using now must come from your unidentified motherboard. We also don't know what you were using before, so we don't know if you were using the proprietary Nvidia driver which won't work with non-Nvidia hardware.

I *suspect* that you were using the proprietary Nvidia driver before, and now you're using some kind of (probably Intel) chip on the motherboard. If that's the case, you should only need to remove the Nvidia driver to have everything work again.

Since you're using a VGA connection you may also need to do some work to get the correct resolution when things aren't hampered by the wrong kernel modules; a lot of the connections of the VGA era (either end) weren't great at doing EDID, and if you're using some kind of adaptor now that can also interfere. If your graphics system can't determine the appropriate resolution you might get a really low-res display, and if your display can't do the low-res you might not get anything.

---

### Post by cedric9 on 2020-02-05
> **CatKiller said:**
> 
I *suspect* that you were using the proprietary Nvidia driver before, and now you're using some kind of (probably Intel) chip on the motherboard. If that's the case, you should only need to remove the Nvidia driver to have everything work again.

Thanks, I'll give it a try this weekend.  BTW, I reinstalled my video card, yet the rebooting problem at POST does not seem to have returned as of yet.

---

### Post by slickymaster on 2020-02-05
*Thread moved to **Hardware**.*

---

### Post by mastablasta on 2020-02-06
> **cedric9 said:**
> Thanks, I'll give it a try this weekend.  BTW, I reinstalled my video card, yet the rebooting problem at POST does not seem to have returned as of yet.

what is the card? if nvidia, do as above. remove the driver and let the OS find the card and load the correct drivers for the new chip (on mother board).

check capacitors on card. see if any are bulging. it's a sign that they are failing and would cause the issue you mentioned. i had simialr issues on AMD card. was working fine then had issues, then fine again then issues again. i cleaned it, monitored the temp, added additional fan, replaced the PSU, tested RAM...  in the end i got fed up with it all and got a new case, motherboard, ram, CPU and GPU. basically a new PC. i used what i could from the old one though.

---

