---
title: "Problem with ATI Sapphire HD 4850 graphic card"
date: 2008-08-18
forum: Hardware
---

### Post by hujer on 2008-08-18
While installing Ubuntu (either 8.04 or 8.10 ALPHA 4) I am experiencing problems with detecting graphic HW. After installation gdm correctly starts, but after login white screen with movable mouse pointer only is displayed, no panels no menus ...nothing.. only white desktop surface. I tried to install ATI Catalyst driver (which was O.K. with previous Sapphire (X850) card) from console, but it did not help. Gdm does not even display welcome screen, several times tries to operate the card, then shows menu for setting driver and monitor, but changing those settings has no effect (I tried mostly all of them) because next the display disappears at all. Sometimes I am able to switch to consoole mode by Ctrl-Alt-Fx. Changing usual parameters in xorg.conf has minimal effect. Startx, I tried it from console, reports fatal X-Server error. Next what I tried was to compile xf86-driver-ati, but failed too, configure reports missing "org-server", "fontsproto" and some other packages. apt-get to thiss ackages says that they cannot be found. Please, has anybody some idea how to set up ATI 4850 to work? Unfortunatelly I am not too strong in console commands. Thanks in advance. P.S. in other OS the card works perfectly.

---

### Post by jualin on 2008-08-18
Have you tried the package Envyng-gtk from Synaptic Package Manager?. It can help with ATI and Nvidia Graphics drivers. Just get the package from Synaptic or via terminal > sudo apt-get install envyng-gtk and then open up Envy, located in System Tools, and follow the instructions.

---

### Post by hujer on 2008-08-18
No, I did not. I will do it and let You know about results. Thank You.

---

### Post by jualin on 2008-08-18
Let us know if you need further help on your issue.

---

### Post by hujer on 2008-08-19
Hi. Well. After a day of diligent workaround I have to say that I have not moved even step forward. Basically different OS behave different way. Hardy (8.04) is more affable than Intrepid (8.10). My effort concerns more to Intrepid because it should be able to operate other peripherals such as my Aver TV card. First, I suspect that the graphic card somehow remebers its former settings and not being properly set by OS it reacts to  the same conditions different way (doing the same "experiment" with the same setting several times results in different behavior). Second, envyng-gtk do not work in Intrepid, says it is not supported by OS. Third, both OS are able to detect somehow one connected monitor, when there are two monitors connected, Intrepid crashes. The card has two DVI outputs, I would like to use two analog monitors connected via DVI to annalog reductions. Hardy somehow works with Catalyst ver 8.7 for Linux downloaded from AMD website. In Intrepid Catalyst instals, aticonfig creates xorg.conf but Catalyst itstelf says that nothing is initialised. Intrepid is able to start display (800x600) with "radeonhd" driver included in package, but I failed to configure it via xorg.conf. It seems that the driver ignores all settings in here. Connecting the second monitor results in "Internal error" during gdm start. The resolution in the case of one monitor, cannot be changed from System/Settings/Resolution menu. It does not offer other resolution. So finally I can somehow return to former Hardy, but it is very important to me to be able to operate TV card. Its support is included only in 2.6.26 kernel and I am afraid that Hardy is not able run this kernel (it has actually 2.6.24 one). So what I need is to run ATI Sapphire 4850 with two heads with aat leeast 1440x900 resolution in Intrepid. Do You think that iot is posssible and how? Thank You in advance, Dag. P.S Sorry for my english, I am not a native speaking person.

---

### Post by julian_mintz on 2008-08-22
I just read a post in another forum on how to install 4850. I make it works, but I still have some questions. And first, I will show my steps. Then hope to get answers on my question.
1. Download driver files from ATI website, save it to user directory;
2. In terminal, input:
```
sudo sh ati-driver-installer-8-7-x86.x86_64.run
```
3. Follow pop-up window, just next...all in default option
4. Reboot the PC, select UBUNTU8.04(RECOVERY MODE), then choose "root" command interface, input:
```
aticonfig --initial
aticonfig --overlay-type=Xv
exit 
```
   then choose "resume"
5. Do not change restricted driver manager (Is it the name? I can not recall it), also do not enable it when prompts.
6. Use these code to see whether the driver is installed normally.
```
glxinfo |grep -e 'direct' -e 'OpenGL' 
fglrxinfo 
glxgears 
fgl_glxgears
```

Here is my message using above codes, Is it right?
ubuntu:~$ glxinfo |grep -e 'direct' -e 'OpenGL'
direct rendering: Yes
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.7769 Release
OpenGL extensions:

ubuntu:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.7769 Release

ubuntu:~$ glxgears
45717 frames in 5.0 seconds = 9143.338 FPS
40523 frames in 5.0 seconds = 8104.495 FPS
45036 frames in 5.0 seconds = 9007.148 FPS
42578 frames in 5.0 seconds = 8515.409 FPS

ubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
14248 frames in 5.0 seconds = 2849.600 FPS
15492 frames in 5.0 seconds = 3098.400 FPS
14843 frames in 5.0 seconds = 2968.600 FPS
14734 frames in 5.0 seconds = 2946.800 FPS

And my question is:
[COLOR="Red"]When I play AVI files, why I always see player flicker? [/COLOR]

---

### Post by julian_mintz on 2008-08-22
And also I find that when system version updated, should use recovery mode to reinstall drivers, or it would be blank screen when you log into. So keep the driver file leaved on your disk!
Did it solve your problem?

---

### Post by hujer on 2008-08-22
> **julian_mintz said:**
> And also I find that when system version updated, should use recovery mode to reinstall drivers, or it would be blank screen when you log into. So keep the driver file leaved on your disk!
Did it solve your problem?

Hi to all. After more than a week of workarounds I returned to Hardy 8.04.1, because I was not able to make 4850 working under Intrepid 8.10 ALPHA 4, which is currenly in repos. By the way, there are newer fglrx drivers for Intrepid (ver. 8.522) available at launchpad ([https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.522-0ubuntu2/+build/697453](https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.522-0ubuntu2/+build/697453)) but still incompatible with 4850. The way I made the card working under Hrady was:
> 
1. Installed hardy from alternate install CD (in text mode)
2. Hardy started with 16 colours and nearly unreadable texts (after the 20th instaall i remembered aall text)
3. I imediatelly as root started "ati-driver-installer-8-7-x86.x86_64.run" downloaded from AMD site (it applies for both i386 and AMD 64 Ubuntu versions) even skipped offered OS updates. From menu I selected "Full instalation"
4. If installed ubuntu initially does not display anything or displayes garbage, try to switch to console mode (Ctrl-Alt-Fx) or run safe mode from Grub menu /it is the worst case, because You may need network connection running to resolve dependencies/ and start 'installer' from console. It will run in text mode. I found, that it is not necessary to genereate deb files and dpkg them to innstall.
5. When installation finished /display remains bad/, run 'sudo aticonfig --initial -f' and then reboot
6. If everything went O.K. You can see login screen in some acceptable resolution, so login and run Catalyst Control Center from Applications menu to finalize display. Finally reboot.
7. If you after installation of Catalyst (ati-driver...run) and reboot will receive unacceptable resolution either too high which Your monitor is not able to display or that, which does not fit into the screen and Catalyst CC seems not too accept changes You make from menu, edit /etc/X11/xorg.conf as root. In section Screen, Subsection Display put the line'Modes   "AxB@C"', where A, B are desired horiz and vert resolutions and C is horizontal frequency, for ex. 'Modes   "1440x900@60" for Asus AL1916w"".

If properly set, You will get two head screen cloning and sspreading destop to two monitors (large screen) etc. Overlaying and 3D capabilities would be also working (mine are).

That is all. 

Please, if You discover how to set 4850 working under Intrepid 8.10, please, let me know. Regards, Dag.

---

### Post by hujer on 2008-08-22
Last: If everything is installed properly but overlay is not avaulable (screen does not scroll but "jumps" while scrolled, check 'fglrxinfo", it should produce ATI driver string, not MESA!
> 
dag@ND-57-Lin:~$ fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.7769 Release



You probably would have to reinstall kernel source pert of 'ati-driver...run'. Select "Custm" from menu and check appropriate button. You may even reinstall all Catalyst Center, it renews all part without any other damages.

Daag.

---

### Post by molochi on 2008-08-22
> **julian_mintz said:**
> 
And my question is:
[COLOR="Red"]When I play AVI files, why I always see player flicker? [/COLOR]

Turning off Compiz effects appears to be a common work around for those that get the proprietary driver working but experience flicker during video playback.

---

### Post by hujer on 2008-08-22
About "flickering". If You use 'compiz' for effect or beryl, try to stop them. At least disable all effects: rightclick desktop, select 'change desktop beckground' and then select 'Effects' and check button 'None'. Dag.

---

### Post by telemetry9 on 2008-08-24
I'm not sure this is relevant in ubuntu.  I use kubuntu 8.04 and there is a known problem with desktop stability and ATI drivers.  There is a workaround from Kubuntu 8.04 but I don't know if it is relevant to those who use ubuntu and the gnome desktop but there might be some clues to your problem in the solution so here it is:

Some kubuntu users may find a stability problem with the X server in 8.04 with ATI drivers.
Intermittent crashes and frozen screens on the Desktop are an indication of this problem.  A permanent and relatively simple fix is availabe at the link below.

[http://ati.cchtml.com/show_bug.cgi?id=992#c26](http://ati.cchtml.com/show_bug.cgi?id=992#c26)

all the best
Robert.

---

### Post by telemetry9 on 2008-08-24
I'm using Kubuntu 8.04 and have envyng-qt installed and it has installed catalyst 8.6 drivers for my HD4850  but doesn't seem to had detected the new 8.7 drivers as yet.

I wonder if someone could give me some advice on why 8.7 isn't detected by envy as yet on my system.

thanks
robert.

---

### Post by brons2 on 2008-08-24
> **jualin said:**
> Have you tried the package Envyng-gtk from Synaptic Package Manager?. It can help with ATI and Nvidia Graphics drivers. Just get the package from Synaptic or via terminal  and then open up Envy, located in System Tools, and follow the instructions.

Well I tried that but autodetection failed.

Just tried manual, we'll see what happens!

---

### Post by hujer on 2008-08-27
I recently found the latest ATI Catalyst driver ver. 8.8 at [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html). I installed it under Intrepid, but the results were the same as with 8.7. In short (assuming that that I ran "aticonfig --initial -f" after installation): the computer starts, loads OS (displaying normally) and after gdm starts the display flickers several times, then message "Your computer runs in low resolution mode/ Set up, Continue, Close" (or something like this (I translate it from Czech language)). To click on "Continue" to avoid to force installing "vesa" driver, which btw does not work with 4850 either, results in half minute of flickering and then display dies into black screen. It is possible now by "Ctrl-Alt-Fx" switch to character console, log in and work in command line mode. The only way how to make 4850 work under Intrepid is to use in xorg.conf "ati" driver embeded in Inrepid. It works, supports dual head mode, but does not support YUY2 overlaying, which is required by tvtime (I do it everything to be able to watch the TV using my new A16D AverTV Hybried card). Does anybody advice me at least how to enable overlay mode for embeded "ati" driver?

---

### Post by molochi on 2008-09-05
I just installed Ubuntu 8.10 Alpha4 amd64 on a Core2Duo/intelP43 system. VidCard is an ATi Radeon 4850. Symptoms were similar. But I got past that to a desktop.

1)Right before login the tan background goes white for a split second then the login comes up on a tan background again.
2)After Login a WindowsXP wallpaper (really guys?) flashes and then the screen turns blank white again. There is a mouse pointer on the screen. It moves normaly. It changes to the little round "working" symbol for half a minute then returns to a pointer. Mouse buttons do nothing. Keyboard allows Ctr-Alt-Bkspc to login.
3)Ctrl-Alt-Bkspc & Select terminal login 
4)Get terminal window open at bottom right corner of screen.
5)sudo gedit works so does sudo synaptic.
6)uninstall (wait for it....) compiz. All of it.
7)Reboot
8 )No flash before login (good sign) login rewards with windows wallpaper and working desktop.
9)Change freaking wallpaper.

Notes:

It doesn't look like the open ati driver is running, everything in xorg.conf is "configured xxx". Screen resolution is locked
at 1152X864. There are no options to change resolution.

Driver support for the 4850 starts with ATiv8.6 and I think 8.10A4 is using ATiv8.5. I don't know yet if the open drivers support the 4850 yet. 


8.10A5 is supposed to be out RSN.

---

### Post by orlfman on 2008-09-29
ATI current drivers do not support Xorg 7.4. Ubuntu 8.10 uses Xorg 7.4. To get the drivers to work you have to downgrade to Xorg 7.3. Thats what I did and Ubuntu 8.10 works perfectly fine with the newest ATI drivers.

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)
> 
ATI Catalyst™ 8.9 Proprietary Linux x86 Display Driver
Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3


---

