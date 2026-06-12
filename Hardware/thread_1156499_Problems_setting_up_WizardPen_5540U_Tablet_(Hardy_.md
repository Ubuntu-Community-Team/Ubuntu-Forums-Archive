---
title: "Problems setting up WizardPen 5540U Tablet (Hardy Heron)"
date: 2009-05-11
forum: Hardware
---

### Post by guedesav on 2009-05-11
Hi. I've followed the steps on [this tutorial]("https://help.ubuntu.com/community/TabletSetupWizardpen") to set up my new WizardPen table, and it worked fine... except neither xinput nor GIMP detect the Tablet as input. Also, I can't move the pen, just the mouse.

Here's the output of xinput:

```

"Virtual core keyboard" id=0    [XKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Virtual core pointer"  id=1    [XPointer]
        Num_buttons is 32
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is 0
                Max_value is -1
                Resolution is 0
        Axis 1 :
                Min_value is 0
                Max_value is -1
                Resolution is 0
"<default pointer>"     id=2    [XExtensionPointer]
        Num_buttons is 9
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
"Generic Keyboard"      id=3    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255

```

The "<default pointer>" is where the "Configured Mouse" was before I took it out, trying to force X into recognizing the tablet. Here's an excerpt of my xorg.conf file:

```

Section "InputDevice"
		Identifier		"WizardPen Tablet"
		Option			"SendCoreEvents"	"true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "2524"
        Option          "TopY"          "3930"
        Option          "BottomX"       "30215"
        Option          "BottomY"       "29253"
        Option          "MaxX"          "30215"
        Option          "MaxY"          "29253"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"WizardPen Tablet"	"SendCoreEvents"
	#Inputdevice	"stylus"	"SendCoreEvents"
	#Inputdevice	"cursor"	"SendCoreEvents"
	#Inputdevice	"eraser"	"SendCoreEvents"
EndSection

```

Anyone has any idea of what's going?

---

### Post by Favux on 2009-05-11
Hi guedesav,

You might want to check /etc/udev/rules.d/010_local.rules to make sure your symlink is there.

---

### Post by guedesav on 2009-05-11
No, the symlink is there, I had a problem with that, too, but that's not the case anymore. The symlink is there, and works quite right.

```
lrwxrwxrwx 1 root root 12 2009-05-11 20:51 /dev/tablet-event -> input/event9
```

---

### Post by Favux on 2009-05-11
Hi guedesav,

Good.  Xinput isn't seeing it so I guess the next step would be to find the name of the module (is it a kernel module?) and where it is suppose to install.

You might want to try:
```
dmesg | grep whateverthenameis
```
or
```
lsmod
```

---

### Post by guedesav on 2009-05-11
The name is "wizardpen", yet I now found out it's not being installed...

The file  /usr/lib/xorg/modules/input/wizardpen_drv.so is there, but this is what  "cat /var/log/Xorg.0.log | grep wizardpen" gives me:

```

(II) LoadModule: "wizardpen"
(WW) Warning, couldn't open module wizardpen
(II) UnloadModule: "wizardpen"
(EE) Failed to load module "wizardpen" (module does not exist, 0)
(EE) No Input driver matching `wizardpen'

```

Here is for "insmod /usr/lib/xorg/modules/input/wizardpen_drv.so":

```

insmod: error inserting '/usr/lib/xorg/modules/input/wizardpen_drv.so': -1 Invalid module format

```

The module was compiled in this same machine so... what?

---

### Post by Favux on 2009-05-11
Hi guedesav,

Good job.  You found the problem.  You'll probably have to uninstall the compile and then recompile.  Pay attention and see if there is an error when you compile again.  Maybe you missed a dependency.  I know there have been some updates to the driver so check to see if you're getting the one the wiki says.

---

### Post by guedesav on 2009-05-11
The wiki said me to get version 0.6.0.2, and so I did. I removed the installes drivers and reinstalled, and I get the exact same thing. I even tried with the pre-compiled version for Gutsy Gibbon in that same wiki, but it also gives me the "Invalid module format".

Well, I guess that means more Google time for me. Thanks a lot, anyway.

---

### Post by guedesav on 2009-05-11
Okay, I've removed and recompiled the driver, then restarted the X server. Here's the output of the Xorg.log.0:

```

(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules//wizardpen_drv.so
dlopen: /usr/lib/xorg/modules//wizardpen_drv.so: undefined symbol: xf86IsCorePointer
(EE) Failed to load /usr/lib/xorg/modules//wizardpen_drv.so
(II) UnloadModule: "wizardpen"
(EE) Failed to load module "wizardpen" (loader failed, 7)
(EE) No Input driver matching `wizardpen'

```

---

### Post by Favux on 2009-05-11
Hi guedesav,

Although Hardy is the long term release is it possible there is and updated kernel or xorg-xserver that's causing the incompatibility?  That may be what is giving you the "undefined symbol: xf86IsCorePointer" error.  Maybe you could try the link to the Intrepid HOW TO on Blue Wave and see if the Intrepid driver version now installs on Hardy.  If research doesn't show how others are installing on Hardy currently.

---

### Post by guedesav on 2009-05-12
No good. Tried the debian package, and all the HOW TO has to say to me is to look the logs and try Google. xf86IsCorePointer is still my sworn enemy... :mad:

---

### Post by Favux on 2009-05-12
Hi guedesav,

Bummer.

Well Felix Leong here  [http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html)  says the deb is untested.  Did you try the wizardpen-0.6.0.2.tar.gz or the wizardpen-0.7.0-alpha2.tar.gz?  I don't know about the alpha 1 here:  [http://digitalbluewave.blogspot.com/2008/11/updated-wizardpen-driver-070-alpha1-p.html](http://digitalbluewave.blogspot.com/2008/11/updated-wizardpen-driver-070-alpha1-p.html)  But obviously keep using xorg.conf not HAL.

Here's some more info (and people to contact?):
[http://code.google.com/p/linuxgenius/issues/detail?id=1](http://code.google.com/p/linuxgenius/issues/detail?id=1)
[http://aur.archlinux.org/packages.php?ID=18158](http://aur.archlinux.org/packages.php?ID=18158)

---

### Post by guedesav on 2009-05-12
I've tried 0.7.0-alpha2. And amidst this whole tablet + XFree86 blowing my system mess up, here's what the Xorg log gives me now:

```

(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
(II) UnloadModule: "wizardpen"
(II) Unloading /usr/lib/xorg/modules/input//wizardpen_drv.so
(EE) Failed to load module "wizardpen" (module requirement mismatch, 0)
(EE) No Input driver matching `wizardpen'

```

Now I really didn't get it. Beside that, they used to have a FAQ on how to use their products on Linux... until the page simply disappeared...

---

### Post by guedesav on 2009-05-12
Good news: It's working! Bad news: I don't know how...

After this last output, I've finally suceeded to get my X to work back with Xorg, and recompiled the wizardpen-0.6.0.2 driver. Then X finally suceeded in loading the module. The next step was setting udev to create the symlink and... ta-da!

So... thanks for the help, and hve a nice day!

---

### Post by Favux on 2009-05-12
Hi guedesav,

Congratualations!  Weird.  But think of all the "fun" you've had learning more about the driver!  :)

---

### Post by guedesav on 2009-06-30
Okay, one more quick question now...

The tablet works fine, except everytime I want to use it, I have to plug it, and then start X. Problem is I don't want to have to restart X everytime I need to use the pen, since sometimes I have a some applications loaded with all the files I need and such, and reopening everything again would be quite time consuming.

One paliative solution I've found is to start another X server in another display. That still is not what I want, since if I want to check something in an application already open, I have to switch displays, and that takes some time. Also, I still have to wait after the tablet is plugged to start the other session, so it's not much of a solution anyway.

What I really want to know is if there's a sequence of commands that perform the module loading X does when it starts. With that I could just reload the wizardpen driver whenever the tablet was plugged and (I hope) it would work just fine.

Any guesses?

---

### Post by Favux on 2009-06-30
Hi guedesav,

I don't know which version of Ubuntu you're currently using.  The simplest thing would be to try the old hotplug commands.

ctrl-alt-F1 and then ctrl-alt-F7

---

### Post by guedesav on 2009-06-30
All contrl-alt-F1 then F7 does is get me to the text terminal and then back to X, but the tablet keeps not responding to movement. When I press the pen, it performs a "middle button" action, but that's all. The pointer keeps stationed in the same place.

Truly, what I need is to restart the X without actually restarting it. Got it?

---

