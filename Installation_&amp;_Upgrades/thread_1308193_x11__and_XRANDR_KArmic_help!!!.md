---
title: "x11  and XRANDR KArmic help!!!"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by coacharnold on 2009-10-31
hi, 

 I've been using ubuntu for a long time and Ive been trying to get my boss on it so i convinced him to give me his old laptop to set up with 9.10...  no problem right? ... NO!!!!  The install went great but heres the issue ...
I can't get the screen resolution to show up right ... it's like i have an inch of black on all sides with a little 800x600 screen in the middle ... I  tried to get to xorg.conf but its not in karmic....  Ibmessed with xrandr but i have no clue how to get it right .....  here's my symptoms ...
1- it's an ols toshiba satellite laptop
2- here's the output of xrandr

Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  


3 and here's the video part of lspci

01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

when i go to the DISPLAY gui ... it tells me the display is unknown ...

lastly when i go to the bias there is a weird "Stretch" setting under display ....  with it enabled the  linux cosole is the correct size if it's disabled the linux console is the wrong resolution as well ....  

 ok ... somebody please help me with this ... I really think i can make my boss an ubuntu convert if i can get this old laptop running right ....

---

### Post by tekknokrat on 2010-01-26
I stumbled upon this topic when looking for some help regarding trident chipset.

I hope you have gotten the issue with screen resolution solved for your boss' laptop ( and earned some bonus points with this btw. :P )

I have a similiar laptop model toshiba satellite 4600 with this chipset:

> 01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)


It runs 1024x768 fine within gnome desktop using Arch Linux but when I tried Ubuntu it was also no problem. At all (X)Ubuntu was to slow for this laptop that's why the move to Arch.

I remember that I needed to create a xorg.conf via hwinfo. If you're still interested I can post it.

My only issue with this laptop (apart of slowiness)  is that it wont detect my beamer when connecting it in already booted system. It only detects it on reboot... :popcorn:

---

### Post by coacharnold on 2010-01-26
Well.... no I never did solve it .... in fact even worse the bios died on me  ....  it appeared to be the cmos battery ..... i found a brand new one on e-bay and installed it and I still get a "Please insert Maintenance Floppy" error when I boot ...  So I'm not even near the X-problem at the moment ...  If you have any thoughts or experience with this I'd love to hear it cause the machine is pretty much bricked at the moment ...

Thanks for the response though ..

T

---

### Post by tekknokrat on 2010-01-27
> **coacharnold said:**
> Well.... no I never did solve it .... in fact even worse the bios died on me  ....  it appeared to be the cmos battery ..... i found a brand new one on e-bay and installed it and I still get a "Please insert Maintenance Floppy" error when I boot ...  So I'm not even near the X-problem at the moment ...  If you have any thoughts or experience with this I'd love to hear it cause the machine is pretty much bricked at the moment ...

Thanks for the response though ..

T

Hi,

regarding the bios battery I dont have any clue. sorry. Funny is I just changed the bios battery of the Toshiba yesterday because the time was always reset to 2000 after powering down and linux refuses to boot with wrong fs timestamp. Now everything seems fine. Did you checked the power of battery? Perhaps it was shipped already uncharged... Perhaps you need to reset bios manually...

Regarding the Resolution problem I attach my xorg.conf. Just copy to /etc/X11/xorg.conf. If it does not work please post the log file.

```
tail -n 100 -f /var/log/Xorg.0.log
```

Cheers,
tekknokrat

---

### Post by stationx on 2010-01-29
> **tekknokrat said:**
> Hi,

regarding the bios battery I dont have any clue. sorry. Funny is I just changed the bios battery of the Toshiba yesterday because the time was always reset to 2000 after powering down and linux refuses to boot with wrong fs timestamp. Now everything seems fine. Did you checked the power of battery? Perhaps it was shipped already uncharged... Perhaps you need to reset bios manually...

Regarding the Resolution problem I attach my xorg.conf. Just copy to /etc/X11/xorg.conf. If it does not work please post the log file.

```
tail -n 100 -f /var/log/Xorg.0.log
```Cheers,
tekknokrat

THANK YOU for the file.
I installed Ubuntu last night and only problems I had is the video display.
Everything was unless until I found this thread. The file worked so well dude. Cheers!
It was so close to head back to Microsoft Windows.

Once again, you safed my bacon.

Cheers!:popcorn:

---

### Post by van_Zeller on 2010-02-19
Hello,

I am having a similar problem with ubuntu karmic, except with a GMA 950 onboard video card. I want to force 1080p on it and I cant. Can anybody help me create a xorg.conf??

Thanks in advance

---

