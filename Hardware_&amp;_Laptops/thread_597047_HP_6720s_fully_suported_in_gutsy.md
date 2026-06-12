---
title: "HP 6720s fully suported in gutsy?"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by dixon on 2007-10-30
Hi,
I´m deciding to buy HP 6720s
Full specs:
HP compaq 6720s Intel® Core&#8482; 2 Duo T5470 (1.6GHz, 2MB L2 Cache, 800MHz FSB) - Intel GM965 - 1024 MB DDRII 667MHz - 120 GB 5.4krpm S-ATA - 15.4" TFT WXGA 1280 x 800 BrightView - Intel Graphics Media Accelerator X3100 384-MB shared - DVD+/-RW SuperMulti DL fixed - Modem56K/LAN10/100 - 802.11a/b/g WLAN - Bluetooth - ports: 3x USB 2.0, audio in/out, VGA, RJ-11, RJ-45 - 6-cell Li-Ion Battery- ExpressCard/54 slot -Secure Digital slot - HP travel battery connector - no dock - 2.49kg - 32,3x358x266 - FREE DOS - 1year wrty

General questions:
I´ve read some issues with X3100. Why is it blacklisted in gutsy´s compiz? I thought intel cards are fully supported in linux. I´m "lucky" ati user right now, so I want to buy laptop with good graphic support. Do the intel cards have something like ati´s textured video(one can using Xv vo run multiple videos)? Do the intel cards have some control center in linux? 


Questions to owners of this laptop:
What´s the battery life in gutsy?
Are suspend and hibernate working?
Are all the function keys(suspend, volume......) working?
What about the noise? How often the fan kicks in(while browsing, writing in OO....) and how loud is it, when it kicks in?

EDIT: Is bluetooth working?

---

### Post by marcin_b on 2007-11-02
> **dixon said:**
> Questions to owners of this laptop:
What´s the battery life in gutsy?


About three hours.

> 
Are suspend and hibernate working?


Errr... nope. I cannot make it working correctly. I noticed that the computer woke up from the hibernation/suspension, but the screen became dark immediately (I will test it next time using ssh to examine if the system is alive)

> 
Are all the function keys(suspend, volume......) working?


Volume is working very good.

> 
What about the noise? How often the fan kicks in(while browsing, writing in OO....) and how loud is it, when it kicks in?

Fan is not loud at all. You can hear a small noise after some time, e.g. half an hour of constant work (I use the laptop mostly to browse the web, draw some pictures, html and java development and of course music/videos)

> 
EDIT: Is bluetooth working?

Bluetooth gnome applet report that it is working, but I did not test it.

---

### Post by dixon on 2007-11-05
Thx for the info. I'm going to buy him next week(probably) :)

---

### Post by jelonertz on 2007-11-12
Hi!
I've bought the Compaq 6720s and installed gutsy on it. Everything goes fine during installation process but the ethernet interface port. I can configure an IP address, default gateway, DNSs and so on but no traffic is sent/received thru the interface. Any idea?

Thanks in advance.

Regards.

---

### Post by dixon on 2007-11-12
Try to boot with parameter "pci=noacpi"...

---

### Post by dixon on 2007-12-04
Don't you guys have any problem with videos(tearing), while using the xv output? Cause I get tearing in videos and it's quite annoying...

---

### Post by mubbashir on 2007-12-17
HI, 
I Wasn't able to enable Desktop-Effects on HP 6720s (with almost the specs)..
What do i need to do?

---

### Post by ChuPp0 on 2008-01-04
i finally have installed ubuntu and now i have the same problem with enabling desktop effects on the same comp
i'm totally beginer :)
so pls... :popcorn:

---

### Post by AlesUbu123 on 2008-01-05
Hello!

The graphics card driver that comes with 6720s is blacklisted in compiz. You can overcome this by overriding Compiz blacklist by paste-ing this command into the terminal:

```
mkdir -p ~/.config/compiz; echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```  

Don't try installing xserver-xgl or anything (like I did :-))
More info: [http://wiki.compiz-fusion.org/Hardware/Blacklist/](http://wiki.compiz-fusion.org/Hardware/Blacklist/) 

Got this bit of info from #compiz-fusion IRC channel.

PS.
Other issues with Ethernet card not working properly are not Ubuntu specific and are resolved by installing the latest BIOS upgrade from HP's site.

---

### Post by ChuPp0 on 2008-01-05
i have enabled desktop effects and its work fine...
now i tried to install compiz but it doesn't work
i've lookin to hundred posts but...

is there any tutorial or... something?
I'm new linux user... 
anyway thnx

i find this command to see something :)

compiz --replace ccp &

and i have this output
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

so if this can help...

---

### Post by AlesUbu123 on 2008-01-05
Can you tell me what actually happens after you run the compiz --replace command? Does nothing happen at all or you just don't see the borders of your windows? :-k

You could try installing emerald, libemeraldengine0 and libdecoration0 packages.  

Then try pressing Alt + F2 and enter "compiz --replace".

Ales

---

### Post by ChuPp0 on 2008-01-05
when i do that i have only backgroun pic for few sec and then all back to normal

---

### Post by AlesUbu123 on 2008-01-05
Have you tried configuring compiz effects? Most compiz effects are turned off by default
Try installing compizconfig-settings-manager. Then run "ccsm". You get the Compiz settings window. Try turning effects on (such as expo and wobbly windows and shift switcher...).

Then repeat the command "compiz --replace". 
Now try using some compiz effects, for example Expo by pressing Windows + E, or Shift switcher by pressing Windows + Tab.

(I get the same output in the terminal as you did and my background blinks for a few secs when I start compiz - like on your laptop, and compiz works perfectly for me!)

---

### Post by fflakey on 2008-01-18
> **ChuPp0 said:**
> i have enabled desktop effects and its work fine...
now i tried to install compiz but it doesn't work

If the desktop effects are working then compiz is installed.

You need to install compizconfig-settings-manager using Synaptic, then you will be able to enable the cube, scale, expo etc

---

