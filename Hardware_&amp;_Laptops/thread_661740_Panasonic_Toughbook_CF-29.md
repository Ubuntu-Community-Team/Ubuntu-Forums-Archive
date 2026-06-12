---
title: "Panasonic Toughbook CF-29"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by kr4m17 on 2008-01-08
Hello all, I am new to Ubuntu but have used Linux on and off for both server and desktop purposes for years. I am impressed with many of the features of Ubuntu. I just installed on a Panasonic Toughbook CF-29. I know many people are having problems with the touchscreen. I am not worried about this yet (although I did find instructions on how to calibrate the touchscreen and I will keep everyone posted if it does work). I am worried more about the fact that my synaptic touchpad 'works'. It works in theory. The mouse moves where I move my finger but it is TERRIBLY slow. I have checked numerous forums (including this one) and googled many potential solutions. I can not get the touchpad is so slow it almost makes me sick. The bazaar part is that the touchpad seems to work much better (not great, but better) from left to right. When I move the mouse Up & down it is HORRIBLY slow. I was wondering if anyone else is having a problem like this or if anyone knows a solution. Thanks for all of your help in advance!

Jeffrey M. Simon
[email]jeffreymsimon@gmail.com[/email]

---

### Post by kerry_s on 2008-01-08
try using xset to set the speed.

in a terminal:
xset m 3 10  <-fast
or
xset m 7 10  <-faster

type-> man xset  <- to read the manual

don't forget to put the 1 that works into your start up.

---

### Post by kr4m17 on 2008-01-08
Thanks I will give it a go. Also, I was trying to get the program gsynaptics installed to configure it. I was having very little luck! It keeps saying the value has to be changed to true. I used true & on and I am still getting the exact same error. Can anyone help? I followed instructions on this forum... no help.

[http://ubuntuforums.org/showthread.php?t=345192](http://ubuntuforums.org/showthread.php?t=345192)

Jeffrey M. Simon
[email]jeffreymsimon@gmail.com[/email]

---

### Post by Daelyn on 2008-01-09
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.whatever 
```
```
 sudo gedit /etc/X11/xorg.conf 
```

Look up something looking like this
```
 
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

```
Do not copy this one, because it might not be properly configured.

Just before "EndSection" create a new line with
```
 Option  "SHMConfig"  "true" 
``` 

Your synaptics xorg section should now look like this.
```
 
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option  "SHMConfig"  "true" 
EndSection

```
Yet again, do not copy the entire section because it might not work on your machine.

I'm not myself using gsynaptics or qsynaptics, but, I tried once and this made the tools work fine. Unfrotunately, I feel they are lacking in their capabilities so I do it manually instead.

If this does not work, post back and we'll try investigate some further.

EDIT: Do not forget to reboot or restart X to make use of this new option.
If this does not work, try ```
 sudo modprobe synaptics
``` after reboot/restart. Saw something about missing module in some forum post that could relate to this.. 

If it does work with modprobing, add the module in "/etc/modules".

---

### Post by kr4m17 on 2008-01-09
So the xset feature worked great. It took some time to figure out how everything worked but I eventually figured it out. Thanks!

However, I have a new problem I have just discovered that if I put my computer into sleep or suspend mode, there is no way to 'wake' the computer back up. I have moved the mouse, hit all they keys on the keyboard & hit the power button... Any suggestions?

Jeffrey M. Simon
[email]jeffreymsimon@gmail.com[/email]

---

### Post by kerry_s on 2008-01-10
> **kr4m17 said:**
> So the xset feature worked great. It took some time to figure out how everything worked but I eventually figured it out. Thanks!

However, I have a new problem I have just discovered that if I put my computer into sleep or suspend mode, there is no way to 'wake' the computer back up. I have moved the mouse, hit all they keys on the keyboard & hit the power button... Any suggestions?

Jeffrey M. Simon
[email]jeffreymsimon@gmail.com[/email]

a quick google tells me it's a common problem with toughbook, i didn't come across any answers for ya. sorry.

---

### Post by Daelyn on 2008-01-10
> **kr4m17 said:**
> So the xset feature worked great. It took some time to figure out how everything worked but I eventually figured it out. Thanks!

However, I have a new problem I have just discovered that if I put my computer into sleep or suspend mode, there is no way to 'wake' the computer back up. I have moved the mouse, hit all they keys on the keyboard & hit the power button... Any suggestions?

Jeffrey M. Simon
[email]jeffreymsimon@gmail.com[/email]

It could very well be the common issue many people are reporting about here in the forum.
I, unfortunately, or fortunately depending how you look at it do not have this issue, hence I don't know anything about it.

Here are some stuff that might help you on your way. 

[http://ubuntuforums.org/showthread.php?t=505890](http://ubuntuforums.org/showthread.php?t=505890)
HOW-TO Debug SUSPEND, RESUME, HIBERNATE issues topic.

Other gathered ones.
[http://ubuntuforums.org/showthread.php?t=583539](http://ubuntuforums.org/showthread.php?t=583539)
[http://ubuntuforums.org/showthread.php?t=590017](http://ubuntuforums.org/showthread.php?t=590017)
[http://ubuntuforums.org/showthread.php?t=350265](http://ubuntuforums.org/showthread.php?t=350265)
[http://ubuntuforums.org/showthread.php?t=621250](http://ubuntuforums.org/showthread.php?t=621250)

---

### Post by kr4m17 on 2008-01-18
OK, so I have read about a million different threads on a TON of different message boards. I have yet to see anyone getting the touch screen working with the 2.6 kernel. The touchscreen actually works, however it is not calibrated. Anywhere I touch the screen it clicks in the bottom right hand corner (on the default trash bin in Ubuntu). Is anyone else having the same problem? I located supported drivers at [www.xig.com](www.xig.com) and I was ready to pay the $130.00 to get it working and someone from the company called and told me they will not sell to individuals. Only 'LARGE' businesses. Very agitating. Anyway. If anyone has ANY information please post it in this thread so I can start compiling information in one place. Hopefully this will turn into the thread of getting your toughbook touch screen working...

---

### Post by aziscohos on 2008-04-10
They can be made to work, honest!
Get the evtouch driver from [here]("http://www.conan.de/"), and follow the instructions. My calibration should give you a starting point. Relevant bits from /etc/X11/xorg.conf:

```
Section "InputDevice"
     Identifier "touchscreen"
     Driver "evtouch"
     Option "Device" "/dev/input/event4"
     Option "DeviceName" "touchscreen"
     Option "MinX" "250"
     Option "MinY" "280"
     Option "MaxX" "4000"
     Option "MaxY" "3850"
     Option "ReportingMode" "Raw"
     Option "Emulate3Buttons"
     Option "Emulate3Timeout" "50"
     Option "SendCoreEvents" "On"
#     Option "Calibrate" "1"
 EndSection

#Section "InputDevice"
#     Identifier "dummy"
#     Driver "void"
#     Option "Device" "/dev/input/mice"
# EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

.....

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "touchscreen" "CorePointer"
#       InputDevice     "dummy"
        InputDevice     "Synaptics Touchpad"

```
The "dummy" input device was specified in the **evtouch** instructions. When I enabled it, my touch*pad* completely stopped working. Also, I couldn't get the calibration script to run properly, so I fell back on my old numbers, which still worked perfectly.
Use:
```
sudo od /dev/input/ <mouse*, event*> 
```to find out the device mappings. 
**Caveats:** I just installed Kubuntu yesterday, so I may not have everything right yet.
I don't know if the Synaptics Touchpad setup is what is actually running the touchpad, for example.
This setup works for the CF-29. YMMV. It seems that every different Toughbook model uses a completely different touchscreen. [Here's a great long thread]("http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/panasonic-toughbook-cf-29-touch-screen-485053/") about Toughbook touchscreens. Be sure to ignore the obsolete information pertaining to 2.4 kernels.

---

