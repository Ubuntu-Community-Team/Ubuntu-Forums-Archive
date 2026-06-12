---
title: "Need help with fpit (Ubuntu 11.4)"
date: 2011-05-06
forum: Hardware
---

### Post by linuxlover42 on 2011-05-06
Hello good people of earth. I've been playing around with a Compaq TC1000 tablet that I recently got for free. I have almost everything working except one. The pen.
Whenever I touch the pen to the screen X just crashes spectacularly.

I installed fpit and followed the instructions here [http://ubuntuforums.org/showthread.php?t=1325644](http://ubuntuforums.org/showthread.php?t=1325644) to make an xorg.conf which looks like this
```
Section "InputDevice" 
        Identifier "pen" 
        Driver "fpit" 
        Option "AlwaysCore" "on"
        Option "Device" "/dev/ttyS0" 
        Option "BaudRate" "19200" 
        Option "MaximumXPosition" "8600" # "6250"  
        Option "MaximumYPosition" "6485" # "4950"   
        Option "MinimumXPosition" "154"  
        Option "MinimumYPosition" "110" 
        Option "InvertY" 
        Option "TrackRandR"  
        Option "SendCoreEvents" 
        Option "ReportingMode" "Scaled" 
EndSection  

Section "Screen" 
    Identifier    "Default Screen" 
    DefaultDepth    24 
    Option    "AddARGBGLXVisuals"   "True"
EndSection 

Section "Module"  
    Load    "glx"
EndSection 

Section "Device" 
    Identifier    "Default Device" 
    Driver  "nv" 
    Option    "NoLogo"    "True" 
    Option  "ConnectedMonitor"    "DFP" 
EndSection  

Section "InputDevice"  
   Identifier     "Generic Keyboard"  
   Driver         "kbd"  
   Option         "CoreKeyboard" 
   Option         "XkbRules" "xorg"  
   Option         "XkbModel" "pc105" 
   Option         "XkbLayout" "gb"  
   Option         "XkbOptions" "lv3:ralt_switch" 
EndSection  

Section "InputDevice"
     Identifier     "Configured Mouse"
     Driver         "mouse"
     Option         "CorePointer"
     Option         "Device" "/dev/input/mice"
     Option         "Protocol" "ImPS/2"
     Option         "ZAxisMapping" "4 5"
     Option         "Emulate3Buttons" "true" 
EndSection  

Section "ServerLayout"
     Identifier     "Default Layout"
     Screen         "Default Screen"
     InputDevice    "Generic Keyboard"
     InputDevice    "Configured Mouse"
     InputDevice    "pen" 
EndSection  

Section "Extensions"
     Option         "Composite" "Enable" 
EndSection
```I can't find any error messages and I have no idea how to debug this thing. Can anyone help me out?

---

### Post by Favux on 2011-05-06
Hi linuxlover42,

Let's do a quick check and see if the system sees the tablet.  Enter in a terminal:
```
xinput list
```
and see if the tablet is present in the output.

If so your Xorg.0.log in /var/log should show the tablet being placed on the fpit driver.  We may need to look at it.  Also since X is crashing the Xorg.0.log and/or Xorg.0.old may show the crash and the error causing at it.  That should be at or near the bottom of the log.

Also the xorg.conf should be updated a little.  As always when messing with an X configuration file make a backup of your current working configuration file, in this case the xorg.conf.  And be prepared to restore the backup from the command line of a Recovery boot if the changes break X.

You should not need the keyboard and mouse entries so let's remove them.  Also the line:
```
        Option "SendCoreEvents" 
```
should read:
```
        Option "SendCoreEvents" "on"
```
But that doesn't matter since it has been deprecated since X server 1.7 and is no longer needed anyway.  The same is probably true of:
```
        Option "AlwaysCore" "on"
```
but let's leave that one in for now.  Neither probably hurts anything anyway.  So let's try:
```
Section "InputDevice" 
        Identifier "pen" 
        Driver "fpit" 
        Option "AlwaysCore" "on"
        Option "Device" "/dev/ttyS0" 
        Option "BaudRate" "19200" 
        Option "MaximumXPosition" "8600" # "6250"  
        Option "MaximumYPosition" "6485" # "4950"   
        Option "MinimumXPosition" "154"  
        Option "MinimumYPosition" "110" 
        Option "InvertY" 
        Option "TrackRandR"  
        Option "ReportingMode" "Scaled" 
EndSection  

Section "Screen" 
    Identifier    "Default Screen" 
    DefaultDepth    24 
    Option    "AddARGBGLXVisuals"   "True"
EndSection 

Section "Module"  
    Load    "glx"
EndSection 

Section "Device" 
    Identifier    "Default Device" 
    Driver  "nv" 
    Option    "NoLogo"    "True" 
    Option  "ConnectedMonitor"    "DFP" 
EndSection  

Section "ServerLayout"
     Identifier     "Default Layout"
     Screen         "Default Screen"
     InputDevice    "pen" 
EndSection  

Section "Extensions"
     Option         "Composite" "Enable" 
EndSection
```
and restart.

---

### Post by linuxlover42 on 2011-05-07
Ok,  xinput list is giving me:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Jing-Mold USB K/B+Mouse                     id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Jing-Mold USB K/B+Mouse                     id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
&#8764; TOUCHSCREEN                                 id=6    [floating slave]
```

I found no error messages in Xorg.0.log. I did however find:

```

[   206.800] (II) Using input driver 'fpit' for 'pen'
[   206.801] (II) Loading /usr/lib/xorg/modules/input/fpit_drv.so
[   206.803] (**) Option "AlwaysCore" "on"
[   206.803] (**) pen: always reports core events
[   206.805] (**) FPIT device name: TOUCHSCREEN
[   206.805] (**) Fpit associated screen: 0
[   206.805] (**) Option "MaximumXPosition" "8600"
[   206.805] (**) FPIT maximum x position: 8600
[   206.806] (**) Option "MinimumXPosition" "154"
[   206.806] (**) FPIT minimum x position: 154
[   206.806] (**) Option "MaximumYPosition" "6485"
[   206.806] (**) FPIT maximum y position: 6485
[   206.806] (**) Option "MinimumYPosition" "110"
[   206.806] (**) FPIT minimum y position: 110
[   206.806] (**) Option "InvertY"
[   206.806] (**) Option "TrackRandR"
[   206.807] (**) FPIT invert X axis: No
[   206.807] (**) FPIT invert Y axis: Yes
[   206.807] (**) FPIT swap X and Y axis: No
[   206.807] (**) FPIT Passive button mode: No
[   206.807] (**) FPIT RandR tracking: Yes
[   206.808] (II) XINPUT: Adding extended input device "TOUCHSCREEN" (type: Fujitsu Stylistic)
[   206.810] (**) TOUCHSCREEN: (accel) keeping acceleration scheme 1
[   206.810] (**) TOUCHSCREEN: (accel) acceleration profile 0
[   206.811] (**) TOUCHSCREEN: (accel) acceleration factor: 2.000
[   206.811] (**) TOUCHSCREEN: (accel) acceleration threshold: 4
[   206.811] (**) Option "Device" "/dev/ttyS0"
[   206.817] (**) Option "BaudRate" "19200"
[   206.817] (**) Option "StopBits" "0"
[   206.817] (**) Option "DataBits" "8"
[   206.817] (**) Option "Parity" "None"
[   206.818] (**) Option "Vmin" "10"
[   206.818] (**) Option "Vtime" "1"
[   206.821] (**) Option "FlowControl" "None"
[   206.930] (II) config/udev: Adding input device Power Button (/dev/input/event1)
```

Does this help identify the problem? I'm relatively new to Ubuntu and while I'm pretty good with code I have no idea what looks normal or not. Thank you very much for your generous assistance.

---

### Post by Favux on 2011-05-07
Hi linuxlover42,

The tablet isn't showing up in *xinput list* so presumably something is wrong.  You found the relevant section in Xorg.0.log and it says the fpit driver is working and the tablet was added:
```
[   206.808] (II) XINPUT: Adding extended input device "TOUCHSCREEN" (type: Fujitsu Stylistic)
```
Somewhere below that the "TOUCHSCREEN" may have been rejected.  Also it seems to recognize the Identifier "pen":
```
[   206.800] (II) Using input driver 'fpit' for 'pen'
```
So it is looking like we have the fpit stuff in xorg.conf close to correct.  I am hoping this means someone fixed the fpit driver in the repositories, because I think it has been broken since Lucid or so.

If you right click on the Xorg.0.log and choose Create Archive it will compress it and you can attach it with Manage Attachments below.

Also how new is the battery in the stylus?  We'll want to be sure that's working so we can pick it up when we get the driver working.


Meanwhile we can work on further refining the xorg.conf.  I noticed you are using the nouveau driver.  Was there an xorg.conf present or did you create one?  If there was one do you have the video sections that were there?

---

### Post by linuxlover42 on 2011-05-07
When I started this thread I was not in fact using the nouveau drivers but the old nv drivers. I have now installed the nouveau drivers and changed the driver for the device to "nouveau" from "nv" in accordance to the instructions of another veteran of ubuntu. 

There was no Xorg.conf file before and I had to make this one myself.

The battery in the pen is a few weeks old and the pen works perfectly in the BIOS (the driver for the pen seems to be built into the BIOS).

I have attached the Xorg.0.log file.

As an interesting note that might help, I wrote/adapted a script for screen rotation a while ago which uses the xrandr -o command. Now whenever I try to use it (even just typing xrandr -o into the terminal) I get a black screen. I theorize that this may be due to the fact that the pen is set to track screen rotation and it is not working properly.

Thanks

---

### Post by linuxlover42 on 2011-05-11
could the nvidia card be the source of the problem? Nvidia has always had problems with linux.

---

### Post by Favux on 2011-05-12
Well you are correct and the Xorg.0.log looks OK:
```
[    66.664] (II) LoadModule: "fpit"
[    66.689] (II) Loading /usr/lib/xorg/modules/input/fpit_drv.so
[    66.706] (II) Module fpit: vendor="X.Org Foundation"
[    66.707] 	compiled for 1.9.99.902, module version = 1.3.99
[    66.707] 	Module class: X.Org XInput Driver
[    66.707] 	ABI class: X.Org XInput driver, version 12.3
......
[    67.986] (II) Using input driver 'fpit' for 'pen'
[    67.997] (II) Loading /usr/lib/xorg/modules/input/fpit_drv.so
[    67.999] (**) Option "AlwaysCore" "on"
[    67.999] (**) pen: always reports core events
[    68.000] (**) FPIT device name: TOUCHSCREEN
[    68.001] (**) Fpit associated screen: 0
[    68.001] (**) Option "MaximumXPosition" "8600"
[    68.001] (**) FPIT maximum x position: 8600
[    68.001] (**) Option "MinimumXPosition" "154"
[    68.002] (**) FPIT minimum x position: 154
[    68.002] (**) Option "MaximumYPosition" "6485"
[    68.002] (**) FPIT maximum y position: 6485
[    68.002] (**) Option "MinimumYPosition" "110"
[    68.002] (**) FPIT minimum y position: 110
[    68.002] (**) Option "InvertY"
[    68.002] (**) Option "TrackRandR"
[    68.003] (**) FPIT invert X axis: No
[    68.003] (**) FPIT invert Y axis: Yes
[    68.003] (**) FPIT swap X and Y axis: No
[    68.003] (**) FPIT Passive button mode: No
[    68.003] (**) FPIT RandR tracking: Yes
[    68.005] (II) XINPUT: Adding extended input device "TOUCHSCREEN" (type: Fujitsu Stylistic)
[    68.008] (**) TOUCHSCREEN: (accel) keeping acceleration scheme 1
[    68.009] (**) TOUCHSCREEN: (accel) acceleration profile 0
[    68.010] (**) TOUCHSCREEN: (accel) acceleration factor: 2.000
[    68.010] (**) TOUCHSCREEN: (accel) acceleration threshold: 4
[    68.010] (**) Option "Device" "/dev/ttyS0"
[    68.012] (**) Option "BaudRate" "19200"
[    68.013] (**) Option "StopBits" "0"
[    68.013] (**) Option "DataBits" "8"
[    68.013] (**) Option "Parity" "None"
[    68.014] (**) Option "Vmin" "10"
[    68.014] (**) Option "Vtime" "1"
[    68.016] (**) Option "FlowControl" "None"
```
I don't see the pen getting unloaded.  So is TOUCHSCREEN, pen, or fpit showing up in *xinput list*?

> could the nvidia card be the source of the problem? Nvidia has always had problems with linux.
I don't think so, but I'm not totally sure.  I had problems with Nvidia in Natty too.  To use nouveau I had to add the 'nomodeset' option to the kernel line.  So I switched to the proprietary Nvidia driver.
> Now whenever I try to use it (even just typing xrandr -o into the terminal) I get a black screen. I theorize that this may be due to the fact that the pen is set to track screen rotation and it is not working properly.
That probably means the driver doesn't support rotation or needs to be configured for it.  Was that with nv or nouveau?

With nouveau I'd think Xorg would automatically configure it for you and you might be able to remove all of the video sections from the xorg.conf.  Again trying to figure out how to simplify the xorg.conf and remove extraneous variables.  In Synaptics Package Manager nouveau was installed by default and I didn't have an xorg.conf until I went to the proprietary driver.

---

### Post by linuxlover42 on 2011-05-12
TOUCHSCREEN is showing up in xinput list as a floating slave.

> That probably means the driver doesn't support rotation or needs to be configured for it.  Was that with nv or nouveau?With the nv driver the script simply did not work as nv is incompatible with xrandr. Noveau worked fine before I made an xorg.conf file.

> With nouveau I'd think Xorg would automatically configure it for you and  you might be able to remove all of the video sections from the  xorg.conf.  Again trying to figure out how to simplify the xorg.conf and  remove extraneous variablesSo should I try and remove all the video sections in the xorg.conf and see where that gets me?

Edit: I tried it and it works fine, the pen still makes it crash though

---

### Post by Favux on 2011-05-12
Please post the output of *xinput list* when TOUCHSCREEN shows.  We need that.

Good work on the xorg.conf.  Can you post your current working one?

---

### Post by linuxlover42 on 2011-05-12
Certainly, the xorg.conf is as follows
```
Section "InputDevice" 
        Identifier "pen" 
        Driver "fpit" 
        #Option "AlwaysCore" "on"
        Option "Device" "/dev/ttyS0" 
        Option "BaudRate" "19200" 
        Option "MaximumXPosition" "8600" # "6250"  
        Option "MaximumYPosition" "6485" # "4950"   
        Option "MinimumXPosition" "154"  
        Option "MinimumYPosition" "110" 
        Option "InvertY" 
        Option "TrackRandR"  
        Option "ReportingMode" "Scaled" 
EndSection  

Section "Module"  
    Load    "glx"
EndSection 

Section "ServerLayout"
     Identifier     "Default Layout"
     InputDevice    "pen" 
EndSection  

Section "Extensions"
     Option         "Composite" "Enable" 
EndSection
```

And the TOUCHSCREEN section of xinput list is

```
&#8764; TOUCHSCREEN                                 id=6    [floating slave]
```

---

### Post by Favux on 2011-05-12
Thanks.  Do you mind posting the entire xinput list?  I'm thinking it shouldn't be reported as a floating slave so I want to see everything.

We could also try a few more modifications of the xorg.conf.  You are backing up your current working xorg.conf in case we break X, right?

---

### Post by linuxlover42 on 2011-05-13
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Jing-Mold USB K/B+Mouse                     id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Jing-Mold USB K/B+Mouse                     id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
&#8764; TOUCHSCREEN                                 id=6    [floating slave]

```

> You are backing up your current working xorg.conf in case we break X, right?
My last backup was when I removed the video sections

---

### Post by Favux on 2011-05-13
Ok, let me take a peak.  Could you post your current xorg.conf too?

---

### Post by linuxlover42 on 2011-05-13
I haven't changed it since the last time I posted it.

---

### Post by linuxlover42 on 2011-06-14
looks like TOUCHSCREEN is not being recognized as a pointer (xinput list is showing it as a floating slave) I tried using xinput reattach to attach it to the master pointer but it didn't seem to work...

edit: here's my xorg.conf, it hasn't changed much

```
Section "InputDevice"
 Identifier "pen"
 Driver "fpit"
 Option "Device" "/dev/ttyS0" 
 Option "BaudRate" "19200"
 Option "MaximumXPosition" "8600"
 Option "MaximumYPosition" "6485"
 Option "MinimumXPosition" "154"           
 Option "MinimumYPosition" "110" 
 Option "InvertY"
 Option "TrackRandR" 
 Option "ReportingMode" "Scaled"
EndSection    

Section "Module"
 Load    "glx" 
EndSection   

Section "ServerLayout"
 Identifier     "Default Layout"
 InputDevice    "pen" 
 EndSection 

Section "Extensions"
 Option         "Composite"
"Enable"  
EndSection
```
another interesting point is that xrandr is still not working, is it compatible with noveau?

---

### Post by linuxlover42 on 2011-07-20
I'm going to bump this thread just because I'm still interested in it.

---

### Post by Favux on 2011-07-20
Well maybe a couple of ways to go.  We could try changing it from a floating slave to a slave pointer with whatever *man xinput* tells us to use.  Maybe it's detached for some reason (made a float) and we need to reattach it.  I can't tell if TOUCHSCREEN is the "device name" or not.  But if it is what does:
```
xinput list-props "TOUCHSCREEN"
```
show?

It looks like I was trying to compile fpit and see if that is the problem before I got distracted.  I assume you did *sudo apt-get install xserver-xorg-input-fpit*?  From my notes I managed to compile in Lucid and Maverick using the fpit git repository.  I'll have to check the notes to see if there were any problems, but I don't see any errors.  Also I'll have to boot into Natty and try it there and see what happens.

> another interesting point is that xrandr is still not working, is it compatible with noveau? 
I thought it was.  Remind me the proprietary Nvidia driver doesn't work?  And where did you get those video sections from in your xorg.conf?
```
Section "Module"
 Load    "glx" 
EndSection   

Section "Extensions"
 Option         "Composite"
"Enable"  
EndSection
```
And by the way the last section is wrong if it is really that way.  It should be:
```
Section "Extensions"
 Option         "Composite"    "Enable"  
EndSection
```


Edit:  If TOUCHSCREEN is the "device name" try:
```
xinput reattach "TOUCHSCREEN" "Virtual core pointer"
```
To detach it you should have had to run:
```
xinput float "TOUCHSCREEN"
```

**Edit 2**:  Never mind.  Just spent some hopefully fruitful time and we may be able to get the stupid thing to work.  I need a break and then I'll write it up.

---

### Post by Favux on 2011-07-20
Alright, it looks like Natty is using an fpit version 1.3+ with the last commit on 12-6-10:  [http://packages.ubuntu.com/natty/xserver-xorg-input-fpit](http://packages.ubuntu.com/natty/xserver-xorg-input-fpit)  It turns out there has been a fair amount of activity, mainly by Peter Hutterer, and v. 1.4 was released about 3 weeks ago and also there have been a couple of useful looking commits since:  [http://cgit.freedesktop.org/xorg/driver/xf86-input-fpit/](http://cgit.freedesktop.org/xorg/driver/xf86-input-fpit/)  The commit log:  [http://cgit.freedesktop.org/xorg/driver/xf86-input-fpit/log/](http://cgit.freedesktop.org/xorg/driver/xf86-input-fpit/log/)

So lets try v. 1.4+ and see if the new version of the driver works in Natty.  It has a new .conf file so hopefully you'll no longer need to configure the tablet PC through your xorg.conf.  First we have to update xorg macros from Natty's default 1.11 to 1.12.  We'll work on the Desktop.  Copy and paste each line/command in a terminal and enter the command.  One line extends past the right edge of the box, be sure to get it all.
```
cd ./Desktop

wget http://xorg.freedesktop.org/releases/individual/util/util-macros-1.12.0.tar.bz2

sudo cp /usr/share/aclocal/xorg-macros.m4 /usr/share/aclocal/xorg-macros.m4.bak

tar xjvf util-macros-1.12.0.tar.bz2

cd util-macros-1.12.0

./configure --prefix=/usr

make

sudo make install

cd ..
```
Then clone the fpit git repository and compile the driver:
```
git clone git://anongit.freedesktop.org/xorg/driver/xf86-input-fpit

sudo apt-get update

sudo apt-get install build-essential libxrandr-dev x11proto-input-dev xserver-xorg-dev autoconf libtool pkg-config

sudo apt-get upgrade

cd xf86-input-fpit

./autogen.sh --prefix=/usr

make

sudo make install

(Now reboot.)
```
Good luck!  And remember to comment out (#) the fpit stuff in your xorg.conf including the "pen" line in "ServerLayout" before rebooting.

---

### Post by linuxlover42 on 2011-07-22
when I try to make either of the packages it tells me 
```
make: Nothing to be done for `all'.
```

---

### Post by Favux on 2011-07-22
That doesn't matter as long as you see a line like:
> libtool: install: /usr/bin/install -c .libs/fpit_drv.so /usr/lib/xorg/modules/input/fpit_drv.so
You can check and see if there is a new fpit_drv.so located in /usr/lib/xorg/modules/input with the same date and time as when you compiled.

---

### Post by linuxlover42 on 2011-07-22
there is only an fpit_drv.la

---

### Post by Favux on 2011-07-22
Hmmm.  What's the date on it?

---

### Post by linuxlover42 on 2011-07-22
oop never mind there it is. I don't think the macros installed though...

---

### Post by Favux on 2011-07-22
Well a show stopper would be an E or error in the output of make or maybe sudo make install.  So if you need to just post the outputs of compiling macros and fpit and we can check if you have a library missing that you need.

---

### Post by linuxlover42 on 2011-07-22
I tried using sudo checkinstall, which is much nicer than make install because it puts the package into the package manager, to compile the macros and the driver. the macros worked perfectly but the driver failed. the error log was 

```
dpkg-deb: error: parsing file '/var/tmp/tmp.PXAMbuKy8A/package/DEBIAN/control' near line 7 package 'xf86-input':
 error in Version string 'fpit-1': version number does not start with digit
```

---

### Post by Favux on 2011-07-22
It looks like checkinstall is balking because the version format disagrees with it.  I don't know enough about it to figure that out and don't want to learn.  I started with checkinstall about 2 years ago but when I discovered there was a known bug that broke it and had been present for over a year I abandoned it.  Seemed like if they really wanted us to use it, as the Ubuntu wiki seemed to indicate, they would have fixed it.  After all the fix had been out for some time, just hadn't bothered to apply it.  Plus I thought instructing people to compile in a directory that required you to change the permissions on it before you could use it was ridiculous.  If they wanted you to compile there install the directory with the correct permissions.

Try it without checkinstall.

---

### Post by linuxlover42 on 2011-07-22
I already managed to install it with checkinstall by directly downloading the source tarball and compiling that. both packages are (theoretically) installed but the pen still does not work and xinput list has no TOUCHSCREEN entry. The pen does have batteries. Any ideas?

---

### Post by Favux on 2011-07-22
Good!  Nice job.  I thought you'd have to alter at least the configure.ac version to get it to work with checkinstall:
```
AC_INIT([xf86-input-fpit],
        1.4.0,
        [https://bugs.freedesktop.org/enter_bug.cgi?product=xorg],
        xf86-input-fpit)
```
You rebooted correct?  Check and see if the new 50-fpit.conf is installed in /usr/share/X11/xorg.conf.d.  If it is there post the contents.  It could be the identifier for your tablet isn't there so run this command:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```
and post the output.  We're pretty sure it is on ttyS0 correct?

---

### Post by linuxlover42 on 2011-07-22
the output is 


```
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pnp0/00:06/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:06':
    KERNELS=="00:06"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="FPI2002"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""
```

one other thing, I switched to lubuntu on this tablet a while ago since it's much lighter. Will that be a problem?

---

### Post by Favux on 2011-07-22
Did you check for the 50-fpit.conf?  The default should look like:
```
Section "InputClass"
        Identifier "fpit class"
        MatchProduct "FUJ02B2|FUJ02B3|FUJ02B4|FUJ02B6|FUJ02B7|FUJ02B8|FUJ02B9|FUJ02BC"
        Driver "fpit"
        Option "TrackRandR" "on"
EndSection

Section "InputClass"
        Identifier "fpit FUJ02B2 and FUJ02B3 default configuration"
        MatchProduct "FUJ02B2|FUJ02B3"
        Option "BaudRate" "19200"
        Option "MaximumXPosition" "6250"
        Option "MaximumYPosition" "4950"
        Option "MinimumXPosition" "130"
        Option "MinimumYPosition" "0"
        Option "InvertY" "on"
EndSection

Section "InputClass"
        Identifier "fpit FUJ02B6, FUJ02B7, FUJ02B8, FUJ02B9, FUJ02BC default configuration"
        MatchProduct "FUJ02B6|FUJ02B7|FUJ02B8|FUJ02B9|FUJ02BC"
        Option "BaudRate" "9600"
        Option "MaximumXPosition" "4070"
        Option "MaximumYPosition" "4020"
        Option "MinimumXPosition" "0"
        Option "MinimumYPosition" "0"
        Option "Passive" "on"
EndSection
```
Please check.

As you can see the identifier:
```
ATTRS{id}=="FPI2002"

```
Isn't in there so we need to add it.  I'm almost finished writing it.

---

### Post by Favux on 2011-07-23
If the fpit.conf is there be sure to back it up in case our changes break X and you need to restore it from the Recovery Mode command line.

So add FPI2002 to the first snippet like so:
```
Section "InputClass"
        Identifier "fpit class"
        MatchProduct "FUJ02B2|FUJ02B3|FUJ02B4|FUJ02B6|FUJ02B7|FUJ02B8|FUJ02B9|FUJ02BC|FPI2002"
        Driver "fpit"
        Option "TrackRandR" "on"
EndSection
```
and add a new snippet to the end:
```
Section "InputClass" 
        Identifier "fpit FPI2002 default configuration" 
        MatchProduct "FPI2002"
        Option "BaudRate" "19200"
        Option "MaximumXPosition" "8600" # "6250"
        Option "MaximumYPosition" "6485" # "4950"
        Option "MinimumXPosition" "154"
        Option "MinimumYPosition" "110"
        Option "InvertY"
        Option "ReportingMode" "Scaled"
EndSection
```
So 50-fpit.conf looks like:
```
Section "InputClass"
        Identifier "fpit class"
        MatchProduct "FUJ02B2|FUJ02B3|FUJ02B4|FUJ02B6|FUJ02B7|FUJ02B8|FUJ02B9|FUJ02BC|FPI2002"
        Driver "fpit"
        Option "TrackRandR" "on"
EndSection

Section "InputClass"
        Identifier "fpit FUJ02B2 and FUJ02B3 default configuration"
        MatchProduct "FUJ02B2|FUJ02B3"
        Option "BaudRate" "19200"
        Option "MaximumXPosition" "6250"
        Option "MaximumYPosition" "4950"
        Option "MinimumXPosition" "130"
        Option "MinimumYPosition" "0"
        Option "InvertY" "on"
EndSection

Section "InputClass"
        Identifier "fpit FUJ02B6, FUJ02B7, FUJ02B8, FUJ02B9, FUJ02BC default configuration"
        MatchProduct "FUJ02B6|FUJ02B7|FUJ02B8|FUJ02B9|FUJ02BC"
        Option "BaudRate" "9600"
        Option "MaximumXPosition" "4070"
        Option "MaximumYPosition" "4020"
        Option "MinimumXPosition" "0"
        Option "MinimumYPosition" "0"
        Option "Passive" "on"
EndSection

Section "InputClass" 
        Identifier "fpit FPI2002 default configuration" 
        MatchProduct "FPI2002"
        Option "BaudRate" "19200"
        Option "MaximumXPosition" "8600" # "6250"
        Option "MaximumYPosition" "6485" # "4950"
        Option "MinimumXPosition" "154"
        Option "MinimumYPosition" "110"
        Option "InvertY"
        Option "ReportingMode" "Scaled"
EndSection
```
Using:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-fpit.conf
```

---

### Post by linuxlover42 on 2011-07-23
still nothing, I did however notice that when I install fpit, I get the message



```
debconf: unable to initialize frontent: Gnome
debconf: (unable to load GTK -- is libgtk2-pearl installed?)
debconf: falling back to frontend: Dialog

```

along with the usual installation messages. Again do I need to switch back to regular ubuntu from lubuntu to get this to work?

---

### Post by Favux on 2011-07-23
That could be.  Also remember you've added another layer of uneeded complexity by using checkinstall and packaging the compile as a deb.

I'd prefer you did the straight compiles and once you have things working you could try the checkinstall route.

*debconf* sounds like debian configuration, i.e. something to do with checkinstall packaging the deb.


Edit:  With the above fpit.conf could you show me your Xorg.0.log in /var/log?  Go ahead and compress it and attach it.  Also the output of *xinput list*.

---

### Post by linuxlover42 on 2011-07-23
xinput list:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Jing-Mold USB K/B+Mouse                 	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; Jing-Mold USB K/B+Mouse                 	id=10	[slave  keyboard (3)]
```

I'm gonna dual-boot this thing with ubuntu classic and try the install again just to remove all the extra complexity. then I'll go back and see if I can get it on lubuntu.

---

### Post by linuxlover42 on 2011-07-24
I did a fresh install of Ubuntu 11.4 classic and followed your instructions to install fpit. It all went smoothly but it's still not working. Attached is the xorg.0.log (which contains no mention of fpit.) Any ideas?

---

### Post by Favux on 2011-07-24
Sure, what does the 50-fpit.conf look like?  And what is the output of:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```

Maybe the wrong baud rate.  Also does your stylus have a battery in it?

---

### Post by linuxlover42 on 2011-07-25
the output of 
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
``` is :

 ```
 looking at device '/devices/pnp0/00:06/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:06':
    KERNELS=="00:06"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="FPI2002"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""
```
and 50-fpit.conf looks exactally like the one you showed me.

---

### Post by Favux on 2011-07-25
1) Alright, we know the plug and play identifier for the tablet is FPI2002.  So that has to be the correct keyword for a match.  By the way the Gateway tablet PCs are FPI2004.
2) Nothing is happening with either the default Natty fpit driver (which has no fpit.conf) or the updated v. 1.4 fpit driver with a fpit.conf.

So maybe this isn't a driver problem but something else.  The Gateway's were a pain to set up too.  Some would just work and others we had to sweat over.  The magic incantation was often contained in:  [https://help.ubuntu.com/community/FujitsuStylus](https://help.ubuntu.com/community/FujitsuStylus)  But no one ever figured out what the magic phrase was.  From a fpit readme my guess has been it was adding the fully specified setserial line to /etc/rc.local, e.g.:
```
setserial /dev/ttyS0 port 0x06A8 uart 16954 irq 4 baud_base 38400

```
If that's what you need we need to figure out yours.

Before we go down that rabbit hole we should try out a couple of other things.  For example I doubt you need the ReportingMode line.  The other is do we need the Passive line?  I'm pretty sure your stylus has a battery and so that should be Passive "off" and that should be default, i.e. you don't need the line.  But maybe we should try it:
```
Section "InputClass" 
        Identifier "fpit FPI2002 default configuration" 
        MatchProduct "FPI2002"
        Option "BaudRate" "19200"
        Option "MaximumXPosition" "8600"
        Option "MaximumYPosition" "6485"
        Option "MinimumXPosition" "154"
        Option "MinimumYPosition" "110"
        Option "InvertY" "on"
#        Option "ReportingMode" "Scaled"
        Option "Passive" "off"
EndSection
```
And definitely use "on" if your stylus doesn't have a battery.

Also I have seen a Gateway report TOUCHSREEN in its *xinput list* just like your TC1000 does.  Where is that coming from?  I do not know.  At a guess, is a udev rule somewhere picking it up?  And then messing things up?  Could be.  Should we try to override it with our own udev rule?  Maybe.

What would that look like?  Why not try something like?:
```
ACTION!="add|change", SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="FPI2002", ENV{ID_MODEL}="Compaq TC1000 on Finepoint $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Compaq TC1000 on Finepoint $attr{id}"
```
That's all one line.  And we'll add it to the directory the user supplied rules are suppose to go in using:
```
gksudo gedit /etc/udev/rules.d/70-fpit.rules
```

If that fails we could go back to the xorg.conf.

---

### Post by linuxlover42 on 2011-07-28
hmm, still nothing. Should I try setting up the xorg.conf again. Also does the 70-fpit.rules need something special done to it? Xorg.0.log is still not showing anything to do with TOUCHSCREEN or fpit.

---

### Post by Favux on 2011-07-29
Darn.  :(

Before we abandon the fpit.conf for now and go back to the xorg.conf let's try specifying that fpit is the preferred driver in the fpit.rules.  So add to the end this:
```
ENV{x11_driver}="fpit"
```
So the whole thing reads:
```
ACTION!="add|change", SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="FPI2002", ENV{ID_MODEL}="Compaq TC1000 on Finepoint $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Compaq TC1000 on Finepoint $attr{id}", ENV{x11_driver}="fpit"
```
Remember still all one line.

Nope, if you put the above in a file called 70-fpit.rules in /etc/udev/rules.d it should be good.

---

### Post by linuxlover42 on 2011-07-29
still no, is there any way to check if 50-fpit.conf is being picked up? Also, gedit seems to be wrapping the text in 70-fpit.rules into multiple lines, is that a problem?

---

### Post by Favux on 2011-07-29
Well the list-props changed from evdev to not reporting a driver so I assume that indicates that the match to fpit was made and that the fpit driver hasn't been updated to report itself.  I'm fairly sure I've seen that before.

No the wrap shouldn't matter as long as you've entered it as on line, i.e. no line breaks or returns/enters.

Oh well, time to go back to the xorg.conf.  If we get that working we can always come back to the fpit.conf.  It would sure be nice to have that working if/when we submit a patch for the TC1000 to the fpit driver.

---

### Post by linuxlover42 on 2011-07-29
I set up the xorg.conf and the result is much the same as it was before, x crashes and then restarts.

```
xinput list gives me
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Jing-Mold USB K/B+Mouse                     id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Jing-Mold USB K/B+Mouse                     id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
&#8764; pen                                         id=6    [floating slave]
```Note that it is now saying pen instead of TOUCHSCREEN.
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```gives me:

```
  looking at device '/devices/pnp0/00:06/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:06':
    KERNELS=="00:06"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="FPI2002"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""
```I am attaching xorg.0.log

---

### Post by Favux on 2011-07-30
> Note that it is now saying pen instead of TOUCHSCREEN.
That's interesting.  Do you still have the 70-fpit.rules in place?

What does your current xorg.conf look like?
> I set up the xorg.conf and the result is much the same as it was before, x crashes and then restarts.

So X comes back up and you get your Desktop back?  What causes X to crash?  Using the pen/stylus?  Let's see what the Xorg.0.log shows.

---

### Post by Favux on 2011-07-30
Your first and fourth Xorg.0.log look very similar, other than the "switch over" to pen.  Can you check in your Xorg.0.log and Xorg.0.log.old to see if you have an error associated with the X restart.  That would be very helpful.

---

### Post by linuxlover42 on 2011-07-30
Here's something interesting. Near the ends of both xorg.0.log and xorg.0.log.old is this.
```
[  2730.869] Segmentation fault at address 0x4
[  2730.869] 
Caught signal 11 (Segmentation fault). Server aborting
[  2730.869] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[  2730.869] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  2730.870] 
[  2730.878] (II) UnloadModule: "fpit"
[  2730.879] (II) Unloading fpit
```
and then it continues to unload the rest of the modules.

---

### Post by Favux on 2011-07-30
So it doesn't have anything to do with your use of the stylus?

Looks like it may be a video driver or possibly font related crash.  What's your video chipset?
```
lspci | grep VGA
```
Also need to see your current xorg.conf.

---

### Post by linuxlover42 on 2011-07-31
Actually, the segmentation fault was probably caused by my attempt to use xrandr -o which resulted in a blank screen. Sorry. The TC1000 uses a GeForce 2 go chipset and I think nouveau has a problem with that.

There is now no mention of that error in the log (I did crash it with the pen and check). There is nothing in the log that suggests an error or a crash which leads me to believe that the crash was a catastrophic one.

---

### Post by Favux on 2011-08-04
How sure are we that the baudrate is 19200.  Have you tried 38400?

Let's see if the system will tell us something.  What's the output of?:
```
sudo dmesg | grep ttyS
```
or
```
setserial -g /dev/ttyS0
```

---

### Post by linuxlover42 on 2011-08-05
Neither command shows any mention of baud rate. I might end up just installing lucid and setting it up on that.

---

### Post by Favux on 2011-08-05
Hi linuxlover42,

Could you post the output you are getting from the two commands?  That could/would be helpful for either release.

---

### Post by linuxlover42 on 2011-08-06
Here are the outputs
```
$ setserial -g /dev/ttyS0
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
$ sudo dmesg | grep ttyS
[    1.189964] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

Actually, I've discovered that natty is really the wrong distro alltogether for this. Fpit does not work (or is a pain to get working) and the graphics drivers (nvidia and nouveau) have problems with the version of x included with natty (a problem which stops Xrandr from working). I set it up on Lucid and everything (pen, rotation, etc.) works perfectly with the exception of the pen's right click button which seems to not be doing anything. 

I thank you for your generous help

---

### Post by Favux on 2011-08-06
Hi linuxlover42,

Thanks for posting the outputs.

Absolutely outstanding!!!

For others could you expand a little on what you did to get it working in Lucid?

Did you use the fpit driver in the repository or did you compile it?  Are you using a xorg.conf and what does it look like?  And so on.

---

### Post by Favux on 2011-08-06
Also, now that you have it working in Lucid I would like to test the fpit.conf in xorg.conf.d.  See if you can use it instead of the xorg.conf.  I guess we should follow the wacom.conf which was 10 in Lucid before changing to 50 for Maverick and Natty, since it is 50-fpit.conf in the download.  The location in Lucid is different too so you'd use:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-fpit.conf
```
with the contents:
```
Section "InputClass"
        Identifier "fpit class"
        MatchProduct "FUJ02B2|FUJ02B3|FUJ02B4|FUJ02B6|FUJ02B7|FUJ02B8|FUJ02B9|FUJ02BC|FPI2002|FPI2004"
        Driver "fpit"
        Option "TrackRandR" "on"
EndSection

Section "InputClass" 
        Identifier "fpit FPI2002 default configuration" 
        MatchProduct "FPI2002"
        Option "BaudRate" "19200"
        Option "MaximumXPosition" "8600"
        Option "MaximumYPosition" "6485"
        Option "MinimumXPosition" "154"
        Option "MinimumYPosition" "110"
        Option "InvertY" "on"
EndSection
```

---

### Post by linuxlover42 on 2011-08-07
I will be posting everything soon. I need to clean up my xorg.conf a bit first though. Also, I am using fpit 1.3 from the repositories so fpit.conf does not work. I do want to try to build 1.4 and see if it works. I assume I still need to install the macros.

---

### Post by Favux on 2011-08-07
Good.  For sure clean up the xorg.conf if you think it needs it.

So you tried the one in the above post with 1.3?  Hmmm.  I'm not sure we need 1.4 for a fpit.conf to work.  But definitely to compile 1.4 you'll need to update the macros.

I wonder if this would work with 1.3:
```
Section "InputClass"
        Identifier "fpit class"
        MatchProduct "FUJ02B2|FUJ02B3|FUJ02B4|FUJ02B6|FUJ02B7|FUJ02B8|FUJ02B9|FUJ02BC|FPI2002|FPI2004"
        Driver "fpit"
        Option "TrackRandR" "on"
EndSection

Section "InputClass" 
        Identifier "fpit FPI2002 default configuration" 
        MatchProduct "FPI2002"
	Option "Device" "/dev/ttyS0"
        Option "BaudRate" "19200"
        Option "MaximumXPosition" "8600"
        Option "MaximumYPosition" "6485"
        Option "MinimumXPosition" "154"
        Option "MinimumYPosition" "110"
        Option "InvertY" "on"
EndSection
```

---

### Post by linuxlover42 on 2011-08-08
I tried it with 1.3 and it does not work.

---

### Post by Favux on 2011-08-08
Thanks for trying.  I'll wait until you post your working xorg.conf before I make any more guesses on needed Options for a xorg.conf.d .conf file.

---

### Post by linuxlover42 on 2011-08-08
alright here it is.
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen         "Screen" 
    InputDevice    "pen"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dbe"
    Load  "dri"
    Load  "dri2"
    Load  "extmod"
    Load  "glx"
    Load  "record"
EndSection

Section "InputDevice" 
        Identifier "pen" 
        Driver "fpit" 
        Option "AlwaysCore" "on"
        Option "Device" "/dev/ttyS0" 
        Option "BaudRate" "19200" 
        Option "MaximumXPosition" "8600" # "6250"  
        Option "MaximumYPosition" "6485" # "4950"   
        Option "MinimumXPosition" "154"  
        Option "MinimumYPosition" "110" 
        Option "InvertY" 
    Option "Button2" "2" #"3"
        Option "TrackRandR"  
        Option "SendCoreEvents" 
        Option "ReportingMode" "Scaled" 
EndSection  

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "nouveau"
    VendorName  "nVidia Corporation"
    BoardName   "NV11 [GeForce2 Go]"
    BusID       "PCI:0:5:0"
EndSection

Section "Screen"
    Identifier "Screen"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


Section "Extensions"
     Option         "Composite" "Enable" 
EndSection
```

---

### Post by Favux on 2011-08-08
Great!

What I would like you to try is commenting out a few fpit lines and see which ones break the tablet function after a reboot.  If you've already done these experiments let me know.  Start with:
```
#        Option "ReportingMode" "Scaled" 

```
My guess has been that one isn't needed.

I also think this one:
```
#        Option "SendCoreEvents"
```
isn't needed because SendCoreEvents should be assumed by default since Xserver 1.7 (Lucid) and higher.  Plus to work it should be:
```
        Option "SendCoreEvents" "on"
```
I would think.

So what I am wondering is if this is the one we need in the fpit.conf:
```
#        Option "AlwaysCore" "on"

```
I thought this should also be default for Xserver 1.7 and up but maybe I'm wrong.  It's the only thing I can think of that might be missing.

By the way how does the stylus behave?  Is it smooth and do you have pressure?

---

### Post by linuxlover42 on 2011-08-17
nope, it works fine with all three commented out... As for the pen, it's behaving quite smoothly although it needs a wee bit of calibration.

---

### Post by linuxlover42 on 2011-09-19
As a final recap, The TC1000 does not work with Natty for many reasons. Getting everything to work in Lucid is a simple matter downloading fpit from the repositories and adding 

```

Section "InputDevice" 
         Identifier "pen"
         Driver "fpit"
         Option "AlwaysCore" "on"
         Option "Device" "/dev/ttyS0"
         Option "BaudRate" "19200"
         Option "MaximumXPosition" "8600" # "6250"
         Option "MaximumYPosition" "6485" # "4950"
         Option "MinimumXPosition" "154"
         Option "MinimumYPosition" "110"
         Option "InvertY"
         Option "TrackRandR"
         Option "SendCoreEvents"
         Option "ReportingMode" "Scaled"
EndSection 
```to the body of xorg.conf and 

 ```
InputDevice    "pen" 
```to the server layout

---

### Post by verymadpip on 2012-01-15
First, I apologise for the necromancy, but I've only recently been given a TC1000 & docking station & I thought I'd try to revive it.

I've read through this thread:

[http://ubuntuforums.org/showthread.php?t=1325644](http://ubuntuforums.org/showthread.php?t=1325644)

What I'm wondering is does anybody know if the rotation & stylus stuff works with 11.10?

I've got the TC1000 working as a laptop (IceWM on a minimal install) & that's about it really.  I found that the 10.04 mini iso hung during the install process & I didn't like 11.04 very much so I didn't try.  (Looks like that was a blessing in disguise really).  The tablet is useable, I just think it would be waaaay cooler if I can get its features to work too.

Again, I apologise for reviving this & also if it's in the wrong place.

---

### Post by linuxlover42 on 2012-01-15
as far as I know,  neither the stylus nor the graphics card works on any OS above 10.04. I would suggest using the LXDE version of linux mint 9, I've found that that is the best option for the TC1000.

Link to linux mint 9:[ http://linuxmint.com/rel_isadora_whatsnew.php]("http://linuxmint.com/rel_isadora_whatsnew.php")

---

### Post by verymadpip on 2012-01-15
Thanks for the speedy reply linuxlover42.

I tried Mint LXDE 11, & it was a little heavy I thought.  For example flash video was very choppy.  But 11 is not 9 :)

To be honest the pen & rotation would be a bonus & a bit of a fun project, it's not a deal breaker.

---

