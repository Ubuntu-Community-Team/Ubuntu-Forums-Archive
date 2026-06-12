---
title: "[SOLVED] dialog boxes dont work with desktop effects"
date: 2008-11-16
forum: General Help
---

### Post by duanedesign on 2008-11-16
whenever I enable desktop effects save as dialog boxes dont work. I enable system>preferences>appearance>visual effects>normal. With the effects enabled I choose save as in any program and i am unable to select a folder or move around the hard drive folders. This seems to be the case with any dialog box that comes up. For example I tried to upload an Avatar. I hit the browse button to select a picture on my hard drive and the computer is stuck at the folder that was selected when the dialog box opened. I cant navigate the hard drive at all. However the Cancel button works so the box is not completelty dead.

some info on my setup
HP  G60-120us
2.6.27-7-generic
Ubuntu 8.10
Nvidia driver 177
compiz 1:0.7.8-0ubuntu4.1

---

### Post by duanedesign on 2008-11-16
I hope this helps find an awnswer. When using Firefox and Rythmnbox none of the dialog boxes like save as/import file work. While using Amarok, which is a KDE app, everything works fine.

---

### Post by duanedesign on 2008-11-21
bump

---

### Post by Marcus Derekus on 2008-11-21
OK, let's start with the basics. I have attached a script that i need you to download and run. it is called compiz-check and it checks if you have all the requirements to run compiz. 

I think all tests will run positive (cuz compiz is technically running), but if they don't it could help point us toward the problem.

download the file anywhere (remove the ".xcf" extension as i only added it so i could upload)

to run type this in terminal:

```
bash /PATH/TO/compiz-check
```

post any errors

Also just for convenience i have attached a file (compiz-switch) that allows simple turning on/off of compiz.(do NOT remove ".deb" extension)

After downloading just click on the file and install

After installation there will be an icon in the applications>accessories menu called compiz-switch.

If you want you can drag that icon to the panel for easy access.

---

### Post by duanedesign on 2008-11-21
Thank you for the reply.
[COLOR="Red"]
Kernel[/COLOR]

Linux duanedesign-laptop 2.6.27-8-generic 

[COLOR="Red"]computer info[/COLOR]

cpu family	: 17
model		: 3
model name	: AMD Turion Dual-Core Turion RM-70 2000 MHz  	
L2Cache - 2 x 512 KB
Graphics Card** GeForce 8200M G/PCI/SSE2/3DNOW!**
prop. driver **NVIDIA 177.80**

[COLOR="Red"]compiz check results:[/COLOR]

 Distribution:          Ubuntu 8.10 i386
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation Device 0845 (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

[COLOR="Red"]xorg.conf[/COLOR]

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "dri"
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

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
Option "XAANoOffscreenPixmaps"
Option "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection


Also I am including a list of installed packages.

---

### Post by Marcus Derekus on 2008-11-21
Wow, your on top of it, i was gonna ask you for xorg.conf but you got it posted ahead of time. thanks

---

### Post by Marcus Derekus on 2008-11-21
Perhaps it's your driver. Sometimes different drivers work better on different systems.

Perhaps you could try nvidia-glx-173. Or maybe nvidia-glx since it's in ubuntu the repository 

I have heard of some issues (including nvidia cards) being fixed by the changing of the driver.

Also get nvidia-sttings (to change graphics settings) this may help alot via:

```
sudo apt-get install nvidia-settings
```

to run it just type nvidia-settings i terminal if you dont have a menu icon

Plus if you are using compizconfig-settings-manager there may be a certain setting thats causing the problem.

---

### Post by Marius Derekus on 2008-11-21
If there is anyone else with the same card (and ubuntu 8.10) and has desktop effects working, then your help would be taken and aprecciated.

---

### Post by Marcus Derekus on 2008-11-21
BTW:I don't think it'll help, but perhaps you should add your cards BusID to **xorg.conf**.

DO NOT CHANGE ANY THING BESIDES ADDING THE CODE IN RED. BUT READ THIS POST ALL THE WAY THROUGH BEFORE PROCEEDING.

Ok open up xorg.conf in super-user mode

```
sudo /etc/X11/xorg.conf
```

Edit your file so it matches the one below.
we will only be changing the code in red.

```


Other parts in this file may not look like yours. This is because I got mine from a machine using an intel graphics card

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier "Configured Video Device"  
        Driver     "nvidia"
[COLOR="red"]        BusId      "PCI:01:05:0[/COLOR]
EndSection

Section "Monitor"
        Identifier "Configured Monitor"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
EndSection


```


On the **BusID "PCI:01:05:0"**, yours needs to be a little different. 

To find out your BusID open terminal and type:

```
lspci | grep VGA
```

You will get an output kinda like

```
[COLOR="red"]01:05.0[/COLOR] VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
```

Type your version of the number in red in the **BusID** SubSection (CAPS sensitive)

but a little changed so that if you got the number:

**01:05.0**

it would look like

**"PCI:01:05:0"**(and of course the quotes)


note the adding of **PCI:** and that the **.** after 05 is replaced with **:**


BTW: sorry if this posts format sounded a little wierd. I just copied it off of another post of mine (different thread) and edited it a little to be more relevant.

---

### Post by duanedesign on 2008-11-21
I thought switching to 173 instead of 177 might work.  Under Administration>Hardware Drivers it gives me both options. However it says the 177 is recommended. Are there any cons to using 173 over 177. 

I am going to try your suggestions, I will give an update in a bit.

[update]

added busID [-]
openedcompizconfig turned off all settings [-]
opened nvidia settings manager resaved xorg.conf [-]

installed nvidia glx-173 instead of 177. I cant get Compiz to start at all now. here is what I get in Terminal.

duanedesign@duanedesign-laptop:~$[COLOR="Red"] compiz --replace[/COLOR]
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity

when I run: glxinfo

duanedesign@duanedesign-laptop:~$ [COLOR="Red"]glxinfo | grep -i direct[/COLOR]
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

[COLOR="Red"][update][/COLOR]
too many issues with 173  went back to 177 were I only have one issue to solve.

---

### Post by Marcus Derekus on 2008-11-21
Did you try enabling compiz with the compiz-switch application i attached.

Also, if you disable EVERY setting with compizconfig you might not see a difference anyway.

Try using compiz-switch and see what happens.

---

### Post by duanedesign on 2008-11-21
I have been using the Compiz Fusion Icon to switch between Compiz AND Metacity.
I installed the Compiz switch and it doesnt appear to be doing anyhting.

---

### Post by eternalnewbee on 2008-11-21
Hi there.
Sorry for the intrusion, but have you tried disabling visual effects, and then pressing **ALT-F2**, and entering ```
compiz --replace
```
Btw. I use Emerald, and find it very stable. If you want to give it a try, just install it from **Synaptic Package Manager**, and after installation is completed, press **ALT-F2** and enter ```
emerald --replace
```
Hope this helps. Good luck.

---

### Post by duanedesign on 2008-11-21
I went back to the nvidia glx 177. There were way to many issues with the 173. 

with the 177 installed I got everything back working except for the original issue of the unresponsive dialog boxes that dont allow me to navigate folders.

I have tried emerald and it didnt fix the problem.

goimg to try the above suggestion, will update. 

[update]
Running compiz --replace from Alt+ F2 didnt solve it. When I run Compiz --replace from the Terminal I get.

duanedesign@duanedesign-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1366x768) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


I am going to post a picture to better illustrate this hard to describe problem. 
[COLOR="Red"]
[update][/COLOR]

the places in red are th parts of the dialog box that dont work. I can close the window save but I can not edit the name or choose a folder.


[IMG]http://farm4.static.flickr.com/3040/3048705415_1f6d781c5c.jpg[/IMG]
[COLOR="Red"]
[Update][/COLOR]
It is weird inkscape, Gimp, and Amarok work fine.

Evolution, Firefox, Rhythmbox, dont work. Is there something these programs use that the others do not?

---

### Post by eternalnewbee on 2008-11-21
Could you post a larger screenshot?

---

### Post by eternalnewbee on 2008-11-21
> Evolution, Firefox, Rhythmbox, dont work. Is there something these programs use that the others do not?
It must be something with the graphic card configuration.

---

### Post by duanedesign on 2008-11-21
> **eternalnewbee said:**
> Could you post a larger screenshot?

the areas highlighted in red are the areas that are completely unresponsive. Since other things in the window work I am wondering if the window is just not redrawing.

[IMG]http://farm4.static.flickr.com/3040/3048705415_1f6d781c5c_b.jpg[/IMG]

---

### Post by eternalnewbee on 2008-11-21
There you are.
One last thing I can think of is disabling your graphic card, reboot, and enabling it again, although no guarantees that it'll work...

---

### Post by Marcus Derekus on 2008-11-21
HMMM....this is confusing, maybe it is an input problem woth the mouse or keyboard or somthing (although it's probably graphics, i will research some more).

BTW when you click on the compiz switch icon all it will look like it did is make your screen blink (no notification of it being on of off or anything). But it actually switches compiz on/off.

Try turning compiz off the usual way of disabling graphics effects to the system>preferences>appearence menu. Then enable with compiz-switch.

(I mainly gave it to you to make testing quicker so you could easily turn it on and off quickly).

I'll be back later. Gotta have a break on my computer.

---

### Post by duanedesign on 2008-11-22
> **Marcus Derekus said:**
> HMMM....this is confusing, maybe it is an input problem woth the mouse or keyboard or somthing (although it's probably graphics, i will research some more).

BTW when you click on the compiz switch icon all it will look like it did is make your screen blink (no notification of it being on of off or anything). But it actually switches compiz on/off.

Try turning compiz off the usual way of disabling graphics effects to the system>preferences>appearence menu. Then enable with compiz-switch.

(I mainly gave it to you to make testing quicker so you could easily turn it on and off quickly).

I'll be back later. Gotta have a break on my computer.


when I switched back to the 177 I was able to tell that the switch was working. When I hAd the 173 driver installed it was hard to tell what was going on.

Ha, ha yeah you gotta take a break every now and then:)

---

### Post by the_Ben on 2008-11-23
I'm having the exact same issue running 8.10 on an HP G60-125NR.  At first I thought the problem was only occuring with programs that connect to the internet, because I first noticed it trying to download/upload files to emails.  Seems it's true with OpenOffice and text editor files as well. :(

I'll continue to scour the web for solutions, and post here if I find anything.

---

### Post by the_Ben on 2008-11-24
So I discovered (at least for me) that if you maximize the save dialogue window, the problem is resolved.  I was also having the "frozen window" issue with Thunderbird, and maximizing the window also resolves that issue.  Just something to make 8.10 more usable until we figure out a real fix.

---

### Post by 2hot6ft2 on 2008-11-24
Seems to work on my G60-125NR running Compiz Fusion and Ubuntu Ultimate Edition 2.0 64 bit. Pic below.

---

### Post by duanedesign on 2008-11-26
> **the_Ben said:**
> So I discovered (at least for me) that if you maximize the save dialogue window, the problem is resolved.  I was also having the "frozen window" issue with Thunderbird, and maximizing the window also resolves that issue.  Just something to make 8.10 more usable until we figure out a real fix.


**It works!!!!! **I have been trying to figure this out for weeks. I have been on the compiz-fusion forum and this forum and have had no luck. Thank you so much for the workaround.

Something I noticed was that I typed a name in the dialog box while in Compiz. I then remembered the dialog boxes dont work in Compiz. I switched to Metacity and the name I had typed was there. This makes me think that maybe the dialog boxes arent "frozen" they are just not redrawing.

---

