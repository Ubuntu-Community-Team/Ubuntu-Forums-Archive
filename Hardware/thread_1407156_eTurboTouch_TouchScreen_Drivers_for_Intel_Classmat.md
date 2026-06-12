---
title: "eTurboTouch TouchScreen Drivers for Intel Classmate Convertible"
date: 2010-02-14
forum: Hardware
---

### Post by nam31355 on 2010-02-14
Hi all!

First of all, I am sorry for doubleposting.. I wrote more or less the same right here:
[http://ubuntuforums.org/showthread.php?t=1376765](http://ubuntuforums.org/showthread.php?t=1376765)
but I found out that the thread was [SOLVED], so I started a new one, in order to receive more feedback..

So.. It's my third day using Ubuntu Netbook Remix (Karmic Koala 9.10) on an Intel powered Classmate Convertible PC.. I am pretty excited about it, but also pretty confused trying to get everything to work, reading lots of new stuff and gathering millions of pieces of information about this new (for me) OS, which I find really interesting!

The Classmate Convertible features a Touch Screen, from eTurboTouch. After the installation of Ubuntu, the touchscreen works more or less like a touchpad. I found this post over here:
[http://ubuntuforums.org/showthread.php?t=1376765](http://ubuntuforums.org/showthread.php?t=1376765)
as well as this one:
[http://ubuntuforums.org/showthread.php?t=1182225](http://ubuntuforums.org/showthread.php?t=1182225)
and this one:
[http://www.admindu.de/wordpress/?p=453](http://www.admindu.de/wordpress/?p=453)

What I tried to do was the following:

1. I visited [www.eturbotouch.com]("http://www.eturbotouch.com/") and downloaded drivers for CB-R400 and CB-R500, for Ubuntu 9.04 (there is nothing for Ubuntu 9.10). I am not sure that these drivers are the correct ones to use, but they are the same ones used in the third one of the above links.

2. As explained in the Readme File, I extracted the zipped files and copied xfhiddrv_drv.so to /usr/lib/xorg/modules/input 

3. Next, I was supposed to make some modifications to /etc/X11/xorg.conf:
More specifically, add:
InputDevice    "HID TOUCH" "SendCoreEvents"
under:
Section "ServerLayout"
and also add the section:
Section "InputDevice" 
    Identifier  "HID TOUCH" 
    Driver      "xfhiddrv" 
    Option      "Device" "/dev/usb/hiddev0" 
    Option      "ScreenNo" "0" 
    Option      "Rotation" "0" 
    Option      "SwapY" "0" 
    Option      "UpSound" "0" 
    Option      "DownSound" "0" 
EndSection

After many hours of research in the internet (I am a total newbie with ubuntu and linux in general), I found out that there is not a xorg.conf file in Ubuntu 9.10, but there still is xorg.conf support. Meaning, that, if a xorg.conf file exists, then its settings will be used by the X server. I hope I understood it right, haven't I?

So, what I did was to open a new terminal (Ctrl-Alt-F2), then stop the Xorg server (sudo service gdm stop) and create a xorg.conf file (sudo Xorg -configure). A xorg.conf.new was created in my home folder. I edited this file as described above and moved it to /etc/X11 (sudo mv xorg.conf.new /etc/X11/xorg.conf). However, starting again the gdm service didn't help at all..

I also tried using the xorg.conf files provided in the above links, but I couldn't make the Touch Screen work as it was supposed to (even after hitting Ctrl-Alt-Bckspc, which I activated in the System-Preferences-Keyboard menu).

Do you have any suggestions on how to make the Touch Screen work?

P.S. Please take into account that, even if I am a good learner, I am still a newbie, so please try to explain as much as you can..

Thank you all in advance!

---

### Post by beatbm on 2010-02-18
where are you going you karamitro :Pp

 i am searching for you now :PP:P

---

### Post by Danb5854 on 2010-02-19
Hi,

I followed the instructions exactly as they said in the included readme for the Unubtu 9.04 version on my Ubuntu 9.10 system and all is working well except for the calibration screen.

If anyone has any suggestions on how to get the calibration system working that would be great... thanks :-k

DannyB

---

### Post by nam31355 on 2010-02-19
The calibrating system works just fine for me, simply following the instructions in the Readme file.. Note that in the last command (b. Run linearity utility) you should type:
#sudo LinearAp  /dev/usb/hiddev0 4
or:
#sudo LinearAp  /dev/usb/hiddev0 9
(for 4-point and 9-point calibration).

Could you please give me some more analytical information on how you made the touchscreen work?
You can click on the screen, except from simply moving the cursor, can't you?

---

### Post by Danb5854 on 2010-02-25
im using the serial port on my system and i just followed the instructions in the readme

---

### Post by Mauricio Jimenez on 2010-05-07
Hi!
I have a similar problem. Just update to Lucid 10.04 and the touch screen only send the pointer to de upperleft corner and not move to any place. When I have Karmic the touchscreen works nice with a tweeks in xorg.conf, Lucidn change de xorg.conf, and even i go back that changes the screentouch still not working.
Any idea?

---

### Post by hcmeyer on 2010-05-16
When I follow these instructions, xorg.log reports:

(II) LoadModule: "xfhiddrv"
(II) Loading /usr/lib/xorg/modules/input/xfhiddrv_drv.so
(II) Module xfhiddrv: vendor="CSWU, Risintech"
        compiled for 1.6.0, module version = 1.2.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(EE) module ABI major version (4) doesn't match the server's version (7)
(II) UnloadModule: "xfhiddrv"
(II) Unloading /usr/lib/xorg/modules/input/xfhiddrv_drv.so
(EE) Failed to load module "xfhiddrv" (module requirement mismatch, 0)

later in the log, I see:

(II) config/udev: Adding input device eTurboTouch eTurboTouch (/dev/input/event8
)
(**) eTurboTouch eTurboTouch: Applying InputClass "evdev tablet catchall"
(**) eTurboTouch eTurboTouch: always reports core events
(**) eTurboTouch eTurboTouch: Device: "/dev/input/event8"
(II) eTurboTouch eTurboTouch: Found 3 mouse buttons
(II) eTurboTouch eTurboTouch: Found absolute axes
(II) eTurboTouch eTurboTouch: Found x and y absolute axes
(II) eTurboTouch eTurboTouch: Found absolute tablet.
(II) eTurboTouch eTurboTouch: Configuring as tablet
(**) eTurboTouch eTurboTouch: YAxisMapping: buttons 4 and 5
(**) eTurboTouch eTurboTouch: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "eTurboTouch eTurboTouch" (type: TABLET)
(II) eTurboTouch eTurboTouch: initialized for absolute axes.
(II) config/udev: Adding input device eTurboTouch eTurboTouch (/dev/input/mouse2)

so something is loading for the touch screen, but it does not work. When I touch the screen, the mouse cursor flies to the top left corner, and pops out the menu.

I am using Lucid Lynx, and have a newer NL2 classmate convertible. Vendor, CTL, refuses to support linux on this new hardware, they have in the past.

Any suggestions ?

---

### Post by hcmeyer on 2010-05-25
After a couple weeks of research and hacking, I have a working xorg.conf for my classmate NL2. The important parts are:

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0"    "CorePointer"
    InputDevice    "HID TOUCH" "SendCoreEvents"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
    Identifier  "HID TOUCH"
    Driver      "evtouch"
    Option      "Device" "/dev/input/event7
    Option      "ScreenNo" "0"
    Option      "Rotation" "0"
    Option      "SwapY" "0"
    Option      "UpSound" "0"
    Option      "DownSound" "0"
    Option      "DeviceName" "touchscreen"
    Option         "MinX"                "0"
    Option        "MinY"                "0"
    Option         "MaxX"                "4100"
    Option        "MaxY"                "4100"
    Option        "TapTimer"            "50"
    Option        "longtouchTimer"    "30"
    Option        "MoveLimit"            "15"
    Option        "ReportingMode"      "Raw"
    Option        "emulate3buttons"    "true"
    Option        "emulate3timeout"    "50"
EndSection

I am not sure exactly what parts are important, but I will continue. I plan on moving this into a hal script.

---

### Post by mooware on 2010-06-01
Hi there,

I'm currently in the process of moving my Classmate Convertible from Karmic to Lucid, and already got touchscreen, autorotation and wireless working.
Setting display brightness does only work partially, meaning that the keyboard buttons to adjust brightness do not work and the gnome brightness applet does not recognize the display backlight device, but I managed to write a small python script that creates an application indicator for setting brightness.

Anyway, regarding the touchscreen in Lucid, you need a patched kernel, since kernel support for classmate hardware is only available from 2.6.34 on, while Lucid is using 2.6.32. I have already built a package with such a patched kernel, but since it's my first time doing this, it isn't perfect yet. Still, if someone is interested, I'll gladly provide the package and any help necessary.

---

### Post by hcmeyer on 2010-06-01
Hello  Mooware. Since my last post I have improved a little, putting the touchscreen snippet in /etc/xorg.conf.d/90-touchscreen.conf, rather than writing an xorg.conf.
I still have two problems, no rotation, and the .conf contains an option device /dev/input/event6 , and if anything else is plugged into usb at boot time, the touchscreen is at a different event number.
I will wait until the .34 kernel is released, and try again.

---

### Post by mooware on 2010-06-02
hcmeyer, for rotation you could try the scripts provided at [http://www.hannay.de/index.php?option=com_content&view=article&id=45&Itemid=45](http://www.hannay.de/index.php?option=com_content&view=article&id=45&Itemid=45), they work for me after adapting them a bit.[URL="http://www.hannay.de/index.php?option=com_content&view=article&id=45&Itemid=45"]
[/URL]

---

### Post by hcmeyer on 2010-06-13
The 2.6.35 kernel in meerkat seems to work, without any xorg.conf.  Attached is a chunk of Xorg log. X seems to config it as both a tablet and a mouse. 

Rotation does not work, and I have not tried to calibrate

---

### Post by mooware on 2010-06-13
It doesn't rotate by itself. See [this script]("http://www.hannay.de/index.php?option=com_phocadownload&view=category&id=8:intel-classmate&download=46:rotate-screen&Itemid=43") taken from [http://www.hannay.de/index.php?option=com_content&view=article&id=45&Itemid=45](http://www.hannay.de/index.php?option=com_content&view=article&id=45&Itemid=45) for manual rotation. The same site also has a script that does auto-rotation, but it only works well in tablet-mode.

---

### Post by C0rd on 2010-10-21
Sorry for reviving this topic, I am new to Ubuntu and still have a lot of questions

I installed Ubuntu 10.10 on my Classmate Convertible NL2 and everything works out of the box. The things that still need working are the touchscreen:

- (auto) rotation (rotating the screen together with the touchscreen)

- rightclick (when you keep the pressure on one point for a second in windows, it will register as a right mouse click)

I installed "gpointing-device-settings (1.5.1-2)" which shows the screen but only let's me activate a middle mouse button and a mousewheel (which are non-existing on a touch-pad i would guess).

Thank you for your help :)

---

### Post by mooware on 2010-10-27
Hi C0rd,

the rightclick thing is easy to do. In the Gnome mouse properties ("System configuration -> Mouse" or something) on the accessibility-tab you can activate the "simulated secondary click", which should do exactly what you want.

I'm not sure what you mean by autorotation. You wrote "rotating the screen together with the touchscreen", which sounds to me like aligning the touchscreen-input to the display orientation. But when I wrote "autorotation" in this thread, I meant automatically rotating the display so that e.g. "up" on your display is also "up" in the physical world.
Which one is it?

---

### Post by C0rd on 2010-10-29
Thank you, i found it as i was playing around with the 

edit: the device number was wrong, i had to change it to 10 in rotate.sh, then it worked flawless, now on to the accelerometer :)

---

### Post by mooware on 2010-11-02
I had autorotation running on Karmic, but it didn't really work flawlessly, so now I'm using a self-written application indicator to manually switch the display orientation.

I see two problems with autorotation:
- You need to tune your autorotation-script really well, so that it doesn't change the orientation when you don't want it to.
- You'd need to handle the lid switch to have decent autorotation. The lid switch is the device that can tell whether the classmate is in tablet mode. If it's not in tablet mode, like a normal netbook, you probably wouldn't want it to rotate by itself. It is a device in /dev/input/, you can find out which one by using evtest and opening and closing the lid.

---

