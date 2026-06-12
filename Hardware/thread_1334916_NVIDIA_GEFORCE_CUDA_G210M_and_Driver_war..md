---
title: "NVIDIA GEFORCE CUDA G210M and Driver war."
date: 2009-11-22
forum: Hardware
---

### Post by jhonnytunes on 2009-11-22
Hi everyone. Im using LINUX(ubuntu 8.04 x86) since september. I installed it in a TOSHIBA SATELLITE and all was so fine. I fell in love with this OS. Starting this week I received my new LAPTOP. A SONY VAIO (vcp-cw190x) including WIN7 x64. I removed WIN7 and installed ubuntu  9.10 and the only problem was the VIDEO DRIVER. I hadnt know this till i tried to enable the DESKTOP EFFECTS and it return "Desktop Effect could no be enabled". I started to google, then I tried some solution.

 First I Activated the NVIDIA accelerated graphics driver (version 185) (the one that appeared in System>Administration>Hardware drivers). When it was installed I had to restart so I did. When My laptop was about to show the login the screen powered off. It made me reinstall UBUNTU again.  When I installed ubuntu for second time I did the same and the same happened. I plug an external screen to my laptop instead of reinstall OS. I plugged it on my moms Desktop Screen and there the OS was showing. I also could enable the effects. But  unluckly I could made the LAPTOP screen shows anything. Laptop just show on screen till the logon. Ok i disable the driver because I want to use my LAtop screen.

Second, I Download the driver directly from the page and I selected the model and my OS(NVIDIA_SOMETHINGHERE.run). I made all steps and when I restart the computer the Video just crashed. It was unable to show any data  in both,  laptop screen and Dektop DELL screen. So I reinstall Ubuntu Again.

I hope somebody can rescueme from this. Im getting used to Linux and dont want to go back to WIN. Have a nice day.

I attached some outputs and some pictures so you can helpme. 

[PC SPECS. From Store.]--------------
[     [IMG]http://www.sonystyle.com/wcsstore/SonyStyleStorefrontAssetStore/img/75x49/VPCCW190XCTOBLACK.jpg[/IMG]]("http://www.sonystyle.com/webapp/wcs/stores/servlet/SYTSSwitchUser?storeId=10151&catalogId=10551&langId=-1&mode=add&LBomId=8198552921665977150&URL=SYCTOProcess&callAction=StoreCatalogDisplay&customerId=196070572&refreshRepFrame=true") [Model Number:  **US-VPCCW190X-LBOM**]("http://www.sonystyle.com/webapp/wcs/stores/servlet/SYTSSwitchUser?storeId=10151&catalogId=10551&langId=-1&mode=add&LBomId=8198552921665977150&URL=SYCTOProcess&callAction=StoreCatalogDisplay&customerId=196070572&refreshRepFrame=true")
 [VPCCW190X Configure-to-Order]("http://www.sonystyle.com/webapp/wcs/stores/servlet/SYTSSwitchUser?storeId=10151&catalogId=10551&langId=-1&mode=add&LBomId=8198552921665977150&URL=SYCTOProcess&callAction=StoreCatalogDisplay&customerId=196070572&refreshRepFrame=true")
    **Customization Details**
 
[LIST]
[*] No additional Photo Editing Software
[*] No Fresh Start
[*] Microsoft® Works
[*] 4GB (2GBx2) DDR3-SDRAM-1066
[*] No additional Finance Software
[*] Standard Capacity Battery (VGP-BPS13)
[*] Norton Internet Security™ 2009 (30 Day Trial)
[*] Blu-ray Disc™ playback/burning
[*] No Engraving
[*] Intel® Pentium® Processor T4300 (2.10GHz)
[*] No additional Video Editing Software
[*] NVIDIA® GeForce® G210M GPU (256MB VRAM)
[*] Jet Black
[*] Genuine Microsoft® Windows® 7 Home Premium 64bit
[*] 500GB Hard Disk Drive (5400rpm)
[/LIST]


-------------------------------

~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
---------------------------------------

If you need any output from the terminal just make me know. Bye.

---

### Post by wentzr on 2009-11-26
hi, 
user "egghead" over on the nvnews forums has a work around for this for now supposedly it's worked for most everyone:
[http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2)

You need to extract the EDID (hardware identifier for your laptop's LCD screen) from windows, then reference the bin file from within your xorg.conf. 

What was the first thing i did when i got my vaio 61112L? install suse, fedora and ubuntu after completely wiping the harddrive of win7 and all restore partitions that were on there... and of course the only windows i ever bought and used (win xp sp2) gives a BSOD while installing. . . so yeah. this work around requires you have windows running on the same laptop so you can extract the EDID. 

If anybody happens to run into this and can help me out by shooting me the EDID file I'd appreciate it greatly. Otherwise I might just return this laptop ... I thought I was doing GOOD by picking out one with an NVIDIA chipset over ATI. It's a shame cause i love everything else about this portable. again it's a Sony Vaio.. the manual says it's a VPCCW1 series, the box says its the VPCCW13FX/B, and the underside of the laptop says its model PCG-61112L

---

### Post by wentzr on 2009-11-26
Well, I'm using one of s e v e r a l kernel partitions I've made on this laptop.. this one is Ubuntu Studio 9.10, with the latest and greatest updates and so far so good on the Sony Vaio VPCCW1 (3FX).. just plugged in my external monitor into the vga port on the left of the laptop, and went to displays under system settings. logged out after making my settings and whammo. i've got dual monitors including the laptop screen on the G210M, pretty much out of the box w/ a fresh install of the latest builds of ubuntu studio karmic. 

nice.

very nice. this gives me indication that maybe I wont need to swap this laptop back, although the timing probably couldn't be better seeing what tomorrow is... All selfish intentions aside,  compiz effects work, although a bit sluggish but it's there. 

So according to Synaptic I have the following installed:
nvidia-173-modaliases
nvidia-180-modaliases
nvidia-185-modaliases
nvidia-96-modaliases
nvidia-common
smartdimmer
xserver-xorg-video-nv 

as well as jockey-common and jockey-gtx

 hoping NVIDIA will make an update soon so i can really rock with maya (on the 14 inch screen :) it is really all about a lot of power in a small package for me. I need to be able to do this stuff on the go, but then plug into a larger display when not going anywhere for a few hours. it seems that egghead has got somethign that probably works better than this, but this for now is a work around for people like myself who just have no way of restoring windows at the moment. 

just an update on my end regarding this.

---

### Post by jhonnytunes on 2009-11-26
Hi man. Thank you. Im currently finishing the semester at university so Im a little busy right now. I have another problem with the RAM. I have 4GB RAM running Ubuntu 32 so my parter tolds me to install linux server kernell so I can use my 4 Gigas. I would like this kernel can fix my problem. If not i want to know something. Can somebody send me an EDID.bin so i dont have to install WIN7 to extract it or Do i need to make it in my own machine. The linux server kernel doesnt repair this? Thank you form your hel. Have a nice day.

---

### Post by wentzr on 2009-11-27
> **jhonnytunes said:**
> Hi man. Thank you. Im currently finishing the semester at university so Im a little busy right now. ...Can somebody send me an EDID.bin....

I understand. I'm looking for the same thing you are right now, so if I run across it or find any leads for you I'll let you know. It'd be great if you could return the favour but for the time being ubuntu studio will probably suffice. i do need to tweak xorg.conf so i can get the screen area to fit the two monitors properly.. it's a little jenky right now. . seems theres a no-man's land for about 500-1000 pixels below my laptops lcd and the vga connected LCD. probably not more than a few minutes work, I just moved on to getting my JACK latency optimized. . .

---

### Post by jhonnytunes on 2009-11-27
Hi man. Sorry for my really bad english, im latin and doing my best. Im working on an Final Proyect for My programming class in C language. AFAI I'll be owrking on this. H.A.N.D.

---

### Post by jhonnytunes on 2009-12-06
Hi. Im glad to tell you that semester ends. Listen, I cant install windows XP in this PC for do that. Luckily the university gave me free access to Microsoft Software, so as far as I Get an DVD-R I'll burn WIN7 and do the EDID Stuff.

Let me tell you about my stupid try: I have the WIN7 in a virtual machin running in ubuntu(I only have the ISO of 7) so I extract the EDID from my Virtual WIN7 and I saw the EDID so real, so .bin that I tought it could works. When I did all the steps the screen was doing the same thing. As Far As I install seven and make this steps Ill tell you. See ya.

---

### Post by lubosz on 2009-12-21
This is my working xorg.conf from my VPCCW1 with GeForce 230M

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Virtual     1366 768
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Device"
   Identifier          "Device0"
   Driver              "nvidia"
   VendorName         "NVIDIA Corporation"
   Option             "ConnectedMonitor"   "DFP-0"
   Option             "CustomEDID"          "DFP-0:/etc/X11/SNY05FA.bin"
EndSection
```

I attached the EDID extracted from Windows.

---

### Post by lubosz on 2009-12-21
Funny thing. When i switch to the non graphical shell with Ctrl + Alt + F{n}, i get funny animated gray stribes. This is the same bug as if i start the xserver with an invalid EDID.
The non graphical shell works with the vesa driver.

I attached a photo of the bug. Any idea how to solve it?

---

### Post by wentzr on 2009-12-30
> **lubosz said:**
> Funny thing. When i switch to the non graphical shell with Ctrl + Alt + F{n}, i get funny animated gray stribes. This is the same bug as if i start the xserver with an invalid EDID.
The non graphical shell works with the vesa driver.

I attached a photo of the bug. Any idea how to solve it?

well, my first guess was to stop gdm but unless I mistyped twice after logging in in the dark (I get a black screen on the laptop when hitting ctrl+alt+F1 etc) that didn't work. 

/etc/init.d/gdm stop

somehow you've got to unload the glx module. I know there's a way, but I'm heading to bed for now...

Thank you for the EDID and xorg.conf. i'm now typing this after a successful boot, using the latest and greatest NVIDIA driver to date (NVIDIA-Linux-x86-190.53), for the first time ever on this laptop. So this worked to get myVPCCW13FX recognizing the NVIDIA g210m with NVIDIA's latest driver.... BUT im sorry to say this still is not a workable solution.

I am noticing some quirkiness even with this method, but at least I can see my laptop screen in full color. have you tried plugging in to the vga port? my external monitor (dell LCD) is apparently not being recognized through the nvidia X server settings panel.. more to do tomorrow, but this was a big step... i just wish NVIDIA would do something about it. I had tried the ignore EDID option earlier on thinking that would work but no dice.

my ten cents: SEND NVIDIA A BUG REPORT with your system specs.

From Nvidia's web site:
To submit Linux bug reports please email (In English only) [email]linux-bugs@nvidia.com[/email] or [email]linux-nforce-bugs@nvidia.com[/email] please attach an nvidia-bug-report.log, which is generated by running "nvidia-bug-report.sh".

---

### Post by karukera7 on 2010-02-22
hi guys 
,

every body who is having such a problem with nvidia accelerated graphic driver try this forum, i had the same issue , after spending 3 days on this problem, by reading several forum on the web, this forums did provide me the best solutions and it worked :

[http://www.nvnews.net/vbulletin/show...=140482&page=2]("http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2")

---

