---
title: "screen resolution problem"
date: 2005-09-29
forum: Hardware &amp; Laptops
---

### Post by tats on 2005-09-29
got it running as I wanted now!
turns out although my monitor specification is max 69 Horiz Sync, Its only happy running 1280x1024 @ 66Hz 
:cool: 
happy now and sticking around ubuntu for foreseable future
now if i can just get my sound working too....  ;)
original post:
> 
Hi 
I have compaq v70 monitor + nvidia GeForce FX 5200. Latest nvidia drivers are installed OK.
Problem is getting my preferred resolution 1280 x 1024 at any higher than 60hz
Ive tried various things suggested on other posts and still no luck. Any ideas?
Heres some stuff from my xorg.conf:
[HTML]
Section "Monitor"
Identifier   "Monitor0"
VendorName   "Monitor Vendor"
ModelName    "Compaq V70 Color Monitor"
DisplaySize  310	230
HorizSync    30.0 - 69.0
VertRefresh  47.5 - 130.0
Option	    "dpms"
EndSection
Section "Screen"
Identifier "Default Screen"
Device 	   "NVIDIA Corporation NV34 [GeForce FX 5200]"
Monitor    "Monitor0"
DefaultDepth     24
SubSection "Display"
Depth     16
Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth     24
Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection
[/HTML]
Was running fine under redhat9/kde but no luck so far in ubuntu/gnome. 
Any suggestions? fire away :)


---

### Post by grinchy on 2005-09-29
Try comparing the above to your redhat9/kde xorg.conf

Sorry prob not much help

---

### Post by jeffreyvergara.NET on 2005-09-29
have you tried: sudo dpkg-reconfigure xserver-xorg in Terminal?

i have a 17inch monitor and it's maxed resolution is 1280*1024 at 60hz

---

### Post by tats on 2005-09-29
[QUOTE=grinchy]Try comparing the above to your redhat9/kde xorg.conf

Sorry prob not much help[/QUOTE]

hehe yeah i did, its very similiar now to the rh/kde X setup

---

### Post by tats on 2005-09-29
[QUOTE=jeffreyvergara.NET]have you tried: sudo dpkg-reconfigure xserver-xorg in Terminal?

i have a 17inch monitor and it's maxed resolution is 1280*1024 at 60hz[/QUOTE]

actually ive not tried this yet

TBH i figured it would probably just give the same setup as was detected on the original install - worth a go though, i shall try it

---

### Post by tats on 2005-09-30
[QUOTE=jeffreyvergara.NET]have you tried: sudo dpkg-reconfigure xserver-xorg in Terminal?
[/QUOTE]

no luck :(

---

### Post by tats on 2005-09-30
Hmm...

some progress - i managed to get 1280x1024 @ 85Hz on the login screen by adding:

Option "NoDDC" 

into my "Device" section in xorg.conf

but after login it reverts back to the lower resolution @ 85Hz

---

### Post by Sheytan on 2005-09-30
Ignore

---

### Post by tats on 2005-09-30
[QUOTE=Sheytan]Look up the HorizSync and VertRefresh settings for your monitor in the manual or google for it and change the HorizSync and VertRefres settings in xorg.conf to match your monitors
It's   H Freq/ V Freq:  30-69 / 47.5-130
Fount the info on this page [http://www.monitorworld.com/Monitors/compaq/v70.html]("http://www.monitorworld.com/Monitors/compaq/v70.html")
EDIT: LOL didn't see it your xorg config have the right settings, my guess that the monitor can't handle 1280x1024 at 85hz[/QUOTE]
hehe yeah I found that page and doublechecked them yesterday
actually ddcprobe does seem to indicate the monitor your correct:
> 
tats@ubuntu:~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: NV34 Board - p241n-0 Chip Rev
memory: 131072kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 1 1
id: 170a
eisa: CPQ170a
serial: 54333836
manufacture: 52 1996
input: sync on green, analog signal.
screensize: 31 23
gamma: 2.250000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@60 Hz (VGA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
ctiming: 800x600@85
ctiming: 1024x768@85
ctiming: 1280x1024@60
dtiming: 640x350@70
monitorrange: 30-69, 50-150
monitorserial: 652CB07KT386
monitorname:  V70

although that doesnt explain why it works OK on redhat9/kde and now the Ubuntu login screen as well :confused:


EDIT:  dunno if this helps, from Xorg.0.log
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)

---

### Post by bob_c_b on 2005-09-30
[QUOTE=jeffreyvergara.NET]have you tried: sudo dpkg-reconfigure xserver-xorg in Terminal?[/QUOTE]

Definitely try this, Ubunutu did not detect my flat panel during set up, just set it as generic 1280x1024, but running the reconfig detected all the panel's info so I didn't have to hand edit my xorg.conf, worked like a champ. Everything by default was running smoothly but I replaced my FX5200 with a 6200 and while the nVidia driver found it, Xorg did not update. I was goint to edit it by hand but thought it might be worth the effort to run the tool and see what extra info it found, was worth the little effort it took.

---

### Post by tats on 2005-09-30
[QUOTE=bob_c_b]Definitely try this, Ubunutu did not detect my flat panel during set up, just set it as generic 1280x1024, but running the reconfig detected all the panel's info so I didn't have to hand edit my xorg.conf, worked like a champ. Everything by default was running smoothly but I replaced my FX5200 with a 6200 and while the nVidia driver found it, Xorg did not update. I was goint to edit it by hand but thought it might be worth the effort to run the tool and see what extra info it found, was worth the little effort it took.[/QUOTE]

yes, i re-tried (again) no luck still

have to do some work now so maybe i come back to this but for now im out of time and ideas :(

---

### Post by tats on 2005-10-03
Solved, see 1st post for solution

---

