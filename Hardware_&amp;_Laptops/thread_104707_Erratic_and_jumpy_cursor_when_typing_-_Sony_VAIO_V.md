---
title: "Erratic and jumpy cursor when typing - Sony VAIO VGN-A190 running Ubuntu Breezy."
date: 2005-12-16
forum: Hardware &amp; Laptops
---

### Post by oneTime on 2005-12-16
[SIZE=4][COLOR=Blue][FONT=Times New Roman]Greetings from my side of the world!

I posted this thread two weeks ago:

[http://ubuntuforums.org/showthread.php?t=95695&highlight=onetime]("http://ubuntuforums.org/showthread.php?t=95695&highlight=onetime")

and haven't got a single reply. 

I've been debugging my **AlpsPS/2 ALPS GlidePoint**:

Ubuntu breezy installed the Synaptics TouchPad driver for X.Org server 
version 0.14.3+revertedto+0.13.6-0ubuntu3 out of the box and it works. 
Well, horizontal & vertical scrolling along the bottom and right edges of the 
touchpad don't work though.

** 1.) **Some disturbing lines from my **/var/log/Xorg.0.log** file:
[COLOR=Black][I]...
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
[/I][/COLOR][/FONT][/COLOR][/SIZE][INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman][COLOR=Black]*     compiled for 4.2.0, module version = 1.0.0*[/COLOR][/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman][COLOR=Black]*     Module class: XFree86 XInput Driver*[/COLOR][/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman][COLOR=Black]*     ABI class: XFree86 XInput driver, version 0.3*[/COLOR][/FONT][/COLOR][/SIZE]
[/INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman][COLOR=Black]* ...*[/COLOR]

I'm dead certain that XFree86 isn't installed at all! 
XFree86 has always been blind to my 1920x1200 display - at least the last time I tried. 
Why is it an XFree86 class then? I expected the above section to be something like:

[COLOR=Black][I]...
(II) LoadModule: "synaptics"
    (II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
    (II) Module synaptics: vendor="X.Org Foundation"
[/I][/COLOR][/FONT][/COLOR][/SIZE][INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman][COLOR=Black]*             compiled for 4.3.99.902, module version = 1.0.0*[/COLOR][/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman][COLOR=Black]*             Module class: X.Org XInput Driver*[/COLOR][/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman][COLOR=Black]*             ABI class: X.Org XInput driver, version 0.4*[/COLOR][/FONT][/COLOR][/SIZE]
[/INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman][COLOR=Black]* ....*[/COLOR]

Could this mean the synaptics driver isn't properly loaded by the X server? 
If it is not properly loaded, then why does it function? I didn't find any bug filed on this one.

** 2.) **A look at my **/proc/bus/input/devices **
file indicates my touchpad is an "**AlpsPS/2 ALPS GlidePoint**".

Here are some relevant sections of my /**etc/X11/xorg.conf **file with comments inserted directly 
in the lines I believed needed some changes or lines that I did modified or added:

[I][COLOR=Black]Section "Module"
    ...
    **[COLOR=Black]Load    "synaptics"[/COLOR] **[/COLOR][/I][COLOR=Black][COLOR=Blue]#This line was missing in my original
                           #  xorg.conf file but the touchpad 
                           # does work without it!! [/COLOR][/COLOR][I][COLOR=Black]
EndSection

Section "InputDevice"
[/COLOR][/I][/FONT][/COLOR][/SIZE][INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Identifier    "Generic Keyboard"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Driver        "kbd"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "CoreKeyboard"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "XkbRules"    "xorg"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "XkbModel"    "pc104"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "XkbLayout"    "us"[/COLOR]*[/FONT][/COLOR][/SIZE]
[/INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman][I][COLOR=Black] EndSection

Section "InputDevice"
[/COLOR][/I][/FONT][/COLOR][/SIZE][INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Identifier    "Configured Mouse"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Driver        "mouse"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "CorePointer"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "Device"        "/dev/input/mice"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "Protocol"        "ImPS/2"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "Emulate3Buttons"    "true"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "ZAxisMapping"        "4 5"[/COLOR]*[/FONT][/COLOR][/SIZE]
[/INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman][I][COLOR=Black] EndSection

Section "InputDevice"
[/COLOR][/I][/FONT][/COLOR][/SIZE][INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Identifier    "**ALPS**" [COLOR=Blue]# My original **xorg.conf **file [/COLOR][/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black][COLOR=Blue]                            # had **"Synaptics Touchpad" **instead [/COLOR][/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black][COLOR=Blue]                            # of **"ALPS" **in this line.[/COLOR][/COLOR]*[/FONT][/COLOR][/SIZE]
[/INDENT][INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Driver        "synaptics" [/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "SendCoreEvents"    "true"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "Device"        "/dev/psaux"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "Protocol"        "auto-dev"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "HorizScrollDelta"    "0"[/COLOR]*[/FONT][/COLOR][/SIZE]
[/INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman][I][COLOR=Black] [COLOR=Blue]# An attempt to add more options like MaxTapTime, 
# MaxTapMove, AccelFactor rendered
     # my entire touchpad almost useless. Movements became 
# extremely slow. Playing with values of the variables I added didn't help. 
#Besides the cursor stayed jumpy and erratic like before.[/COLOR]

EndSection

Section "Device"[/COLOR][/I][/FONT][/COLOR][/SIZE][SIZE=4][COLOR=Blue][FONT=Times New Roman][I][COLOR=Black]
[/COLOR][/I][/FONT][/COLOR][/SIZE][INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]Identifier    "ATI Technologies, Inc. Radeon   Mobility 9600/9700 M10/M11 (RV350 NP)"[/COLOR]*[/FONT][/COLOR][/SIZE]
[/INDENT][INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Driver        "ati"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     BusID        "PCI:1:0:0"[/COLOR]*[/FONT][/COLOR][/SIZE]
[/INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman][I][COLOR=Black] EndSection

Section "Monitor"
[/COLOR][/I][/FONT][/COLOR][/SIZE][INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Identifier    "Generic Monitor"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Option        "DPMS"[/COLOR]*[/FONT][/COLOR][/SIZE]
[/INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman][I][COLOR=Black] EndSection

Section "Screen"
[/COLOR][/I][/FONT][/COLOR][/SIZE][INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Identifier    "Default Screen"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Device        "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Monitor        "Generic Monitor"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     DefaultDepth    24[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     SubSection "Display"[/COLOR]*[/FONT][/COLOR][/SIZE][INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]         Depth        1[/COLOR]*[/FONT][/COLOR][/SIZE]
    [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]         Modes        "1920x1200"[/COLOR]*[/FONT][/COLOR][/SIZE]
    [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     EndSubSection[/COLOR]*[/FONT][/COLOR][/SIZE]
    [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     SubSection "Display"[/COLOR]*[/FONT][/COLOR][/SIZE]
    [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]         Depth        4[/COLOR]*[/FONT][/COLOR][/SIZE]
    [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]         Modes        "1920x1200"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [/INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     EndSubSection[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]...[/COLOR]*[/FONT][/COLOR][/SIZE]
[/INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black] EndSection[/COLOR]*[/FONT][/COLOR][/SIZE]
[SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black] Section "ServerLayout"[/COLOR]*[/FONT][/COLOR][/SIZE][INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Identifier    "Default Layout"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Screen        "Default Screen"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     InputDevice    "Generic Keyboard"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     InputDevice    "Configured Mouse"[/COLOR]*[/FONT][/COLOR][/SIZE]
  [SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     I[COLOR=Black]nputDevice[/COLOR]**[COLOR=Black]    "ALPS"[/COLOR] **[COLOR=Blue]# My original xorg.conf file had **"Synaptics Touchpad" **instead of **"ALPS" **in this line[/COLOR][/COLOR]*[/FONT][/COLOR][/SIZE]
[/INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black] EndSection[/COLOR]*[/FONT][/COLOR][/SIZE]
[SIZE=4][COLOR=Blue][FONT=Times New Roman][I][COLOR=Black] 
Section "DRI"
[/COLOR][/I][/FONT][/COLOR][/SIZE][INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black]     Mode    0666[/COLOR]*[/FONT][/COLOR][/SIZE]
[/INDENT][SIZE=4][COLOR=Blue][FONT=Times New Roman]*[COLOR=Black] EndSection[/COLOR]*

Yes, I've checked and all handlers and events are in place. 
My Logitech USB-PS/2 Optical Mouse doesn't get in the way either.

All I want is to key-in text in my Ubuntu breezy without have to go searching 
for my currently jumpy and erratic cursor. I tried converting my sister to Linux. 
My erratic and jumpy cursor put her off completely. I saw the look in her eyes: 
"But your Linux can't even keep the cursor where I want it to be when typing!"

It could as well be possible that the erratic and jumpy cursor problem has 
nothing to do with the touchpad.

Somebody help me! 

OneTime
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
I learned the next one will be called Windows VISTA. 
Well, the name says it all:[B][SIZE=5]
V[/SIZE][/B]iral [SIZE=5]**I**[/SIZE]nfections, [SIZE=5]**S**[/SIZE]pyware, [SIZE=5]**T**[/SIZE]rojans and [SIZE=5]**A**[/SIZE]dware! Cheers![/FONT][/COLOR][/SIZE]

---

### Post by logan001101 on 2006-01-24
dude, check if you are touching the mouse pad when typing, same problem here. at first i thought the cursor is jumping but then realize i did touch the mouse pad, its very sensitive.

PS: ur using a big font. it's anoying me

---

### Post by Griffin3 on 2006-01-25
Actually, you may not be touching the touchpad at all.  Seems the the very eMachine I have here has a Synaptics touchpad, and under windows, every now and then hitting a letter key hard enough will cause enough vibration to trigger the "hit" of a left-mouse-button click.  When I switched to Ubuntu, the default sensitivity was high enough that I never had to touch it, so I don't know exactly where to configure it.  But I bet you dollars to donuts if you bump down the sensitivity two notches, your problem will go away.

See also: [http://ubuntuforums.org/showthread.php?t=77099&highlight=synaptics+sensitivity](http://ubuntuforums.org/showthread.php?t=77099&highlight=synaptics+sensitivity)

---

### Post by oneTime on 2006-02-25
[FONT=Verdana][COLOR=Black]Thanks to Griffin3 and Logan001101 for their suggestions. 

I did always made sure I didn't touch my touchpad while typing. Logan001101, those big fonts appear relatively tiny on my 17" screen. I'll always remember to scale them down when posting.

It might be worth noting that my jumpy cursor problem pushed me into compiling my own kernel from the pristine sources. The cursor wasn't erratic anymore after leaving out lots of features I knew I didn't need.  I started with my old Ubuntu Breezy configuration file. I'll encourage anyone having serious issues to recompile their kernel. I did also noticed during reconfiguration that I had been running a 386 kernel on my 686 machine! The 386 one was installed by default from the Ubuntu Breezy CD. At least I do not remember having been offered another option during installation.

I have been away for a long time. Now back with (the still to be released) Ubuntu Dapper because of the radically improved hardware recognition. Marvelous! Linux can now reboot my machine without me giving it a hand and some of those special Sony keys do work out of the box! Now with a fully functional touchpad (after tweaking) but with the same jumpy cursor problem like with Breezy. Griffin3, I did two sensitivity down-scaling as you suggested but nothing changed. It might work if I try some more values. I honestly dislike trial by error and will first go on with a kernel-recompile like I did with Breezy. If it doesn't solve my erratic cursor problem I'll then try some more sensitivity values and eventually disable the touchpad completely, just to make sure it is truely the culprit.

I downloaded kernel version 2.6.15 directly from Ubuntu but will not go on with the compilation because I haven't figured out how to check its authenticity i.e. gpg --verify or sha1 without the necessary public key or checksum. Kernel.org has a public key deposited on their site and on a key exchange server. I found neither a public key nor the sha1 checksum for Ubuntu-patched kernels on the Ubuntu site. I'll start a separate thread on this one.

Thanks again for the replies!
OneTime
[/COLOR][/FONT]

---

