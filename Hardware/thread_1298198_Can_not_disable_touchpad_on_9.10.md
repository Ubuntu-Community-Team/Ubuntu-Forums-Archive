---
title: "Can not disable touchpad on 9.10"
date: 2009-10-22
forum: Hardware
---

### Post by Kognit on 2009-10-22
Hi

I have ASUS K50IJ T3000 and Ubuntu 9.10 and i just can not disable touchpad. I installed packages for "TOuchFreeze" and "Touchpad" and still there is no result. Please help it's really annoying!

---

### Post by Dark_Stang on 2009-10-22
System > Preferences > Mouse. "Touchpad" tab. Uncheck enable touchpad.

---

### Post by Kognit on 2009-10-23
> **Dark_Stang said:**
> System > Preferences > Mouse. "Touchpad" tab. Uncheck enable touchpad.

Thx for reply but here i don't have this option - already checked. Any other solution?

---

### Post by Neo40 on 2009-10-23
Same here. I have a HP Pavilion dv2000 laptop. I tried:

System > Preferences > Mouse. "Touchpad" tab. Uncheck enable touchpad.

Does not work for me. Was ok with 9.04.

---

### Post by Kognit on 2009-10-24
Didn't try it because i automatically upgraded to 9.10. I have installed gsynaptics, touch frezze, touchpad, and still doesn't work. Any other solution?

---

### Post by scebert on 2009-10-29
I have the same problem on 9.10. I had previously used synclient touchpadoff=1, but that now has no effect. When I run synclient -l it shows that the value of touchpadoff has changed, but that doesn't turn the touchpad off. There is also no option to turn it completely off in the mouse settings or gconf.

---

### Post by dnairb on 2009-10-29
> **Dark_Stang said:**
> System > Preferences > Mouse. "Touchpad" tab. Uncheck enable touchpad.

Oh, if only it were that easy. This option *was* available in 9.04, but *not* in 9.10.

So, do we now have to look for third-party software to achieve what was achievable out-of-the-box in earlier versions of Ubuntu?

---

### Post by djurny on 2009-10-29
have you tried
```
synclient $(synclient -l|awk '$1~/^.*Tap.*/{print $1 "=0"}')
```
that will set all 'tap' related configurables to zero..

---

### Post by dgilbert on 2009-10-29
> **djurny said:**
> have you tried
```
synclient $(synclient -l|awk '$1~/^.*Tap.*/{print $1 "=0"}')
```that will set all 'tap' related configurables to zero..

That didn't work. It changed the synclient entries but the touchpad ignored them on my Thinkpad T61. I want control over it or I want it disabled.

Kidnapping the offending driver works. In a shell as superuser I did this:

$ mv /usr/lib/xorg/modules/input/synaptics_drv.so ~

Then restart X.
That move can be reversed to put the synaptics driver back where X expects it.
Hopefully Ubuntu fixes this properly soon.

---

### Post by Kognit on 2009-10-30
Hi,
I found a solution in _[this webpage]("http://ubuntuforums.org/showthread.php?t=1204735&page=3")_. For deactivation type in terminal:
```
sudo modprobe -r psmouse
```

For activation type:
```
sudo modprobe psmouse
```

I created two lunchers for touchpad with this commands.

I hope it will work.

Bye

---

### Post by dnairb on 2009-10-30
I have now managed to disable the touchpad on my Dell laptop:

Install gpointing-device settings

Run this (I did this in terminal: gpointing-device-settings)

Click entry on the left that relates to the touchpad (mine reads "ALPS DualPoint touchpad)

On the General tab, there is an option to turn the touchpad off.

---

### Post by xiphosurus on 2009-10-30
i tried this, and it seemed to worked at first. but after a minute or so, the touchpad comes back on again!! the coming back on can be (not exclusiveluy) triggered by alt-f2.

---

### Post by dnairb on 2009-10-30
I spoke too soon - the touchpad re-enabled itself somehow, for no reason (no keys pressed)

So I tried gsynaptics - same result: disables the touchpad initially, but not for long.

---

### Post by xiphosurus on 2009-10-30
I think I've figured it out.

It gets re-enabled due to the new "disable touchpad while typing" feature, which turns it back on AFTER you stop typing. 

I unchecked that in System > Preferences > Mouse > Touchpad, and now the touchpad stays off after disabling in either gpointing-device-settings or gsynaptics.

---

### Post by dnairb on 2009-10-30
Magic!!

Many thanks xiphosurus. That worked.

---

### Post by hus126 on 2009-10-30
> **Kognit said:**
> Hi,
I found a solution in _[this webpage]("http://ubuntuforums.org/showthread.php?t=1204735&page=3")_. For deactivation type in terminal:
```
sudo modprobe -r psmouse
```

For activation type:
```
sudo modprobe psmouse
```

I created two lunchers for touchpad with this commands.

I hope it will work.

Bye
This method not only disables the touchpad but also the track point on my thinkpad t61 ...

I just want to kill the touchpad

---

### Post by ehj on 2009-11-01
_[Hi dnairb,]("http://ubuntuforums.org/member.php?u=516176")_ I also have a Dell laptop, a Latitude E4300. And the same "problem". Did you finally manage to disable the touchpad completely? It's particularly when you use the trackpoint and by mistake touch the touchpad that the cursor goes anywhere.

---

### Post by joanmunoz on 2009-11-01
> **dnairb said:**
> I have now managed to disable the touchpad on my Dell laptop:

Install gpointing-device settings

Run this (I did this in terminal: gpointing-device-settings)

Click entry on the left that relates to the touchpad (mine reads "ALPS DualPoint touchpad)

On the General tab, there is an option to turn the touchpad off.

Hi dnairb!

That works for me. I have a Compaq 6720s with Ubuntu 9.10.

Thx!

Joan

---

### Post by Vesukka on 2009-11-01
Hi,

It appears again after restart. :(
As a temporary workaround I have a shortcut to gpointing-device settings...

---

### Post by Kognit on 2009-11-01
> **dnairb said:**
> I have now managed to disable the touchpad on my Dell laptop:

Install gpointing-device settings

Run this (I did this in terminal: gpointing-device-settings)

Click entry on the left that relates to the touchpad (mine reads "ALPS DualPoint touchpad)

On the General tab, there is an option to turn the touchpad off.

That doesn't work for me. I only ger some configuration for wheel and the like but not to disable the touchpad. Only thing that works for me now is the terminal commands i wrote.

---

### Post by bluegene on 2009-11-02
It worked for me. I did install gsynaptics, disabled the touchpad as well as making sure that the *Disable the touchpad while typing* option in the System > Preferences > Mouse > touchpad tab is UNCHECKED. I got it working until now. I hope it woks in your situation :).

---

### Post by Vesukka on 2009-11-02
> **bluegene said:**
> It worked for me. I did install gsynaptics, disabled the touchpad as well as making sure that the *Disable the touchpad while typing* option in the System > Preferences > Mouse > touchpad tab is UNCHECKED. I got it working until now. I hope it woks in your situation :).

Exactly as you did... Doesn't work for me after restart.

---

### Post by m42h31 on 2009-11-02
i like disable touchpad when using mouse, in jaunty i can disable touchpad by uncheck "enable touchpad". in karmic I try using touchfreeze but not work.
i think better ubuntu doing automatic disable touchpad when using mouse.

any solution?

---

### Post by Kognit on 2009-11-03
I hope this will work for you - it works fine for me.

 For deactivation type in terminal:
```
sudo modprobe -r psmouse
```

For activation type:
```
sudo modprobe psmouse
```

I created two lunchers for touchpad with this commands.

---

### Post by shawnisalk on 2009-11-04
sudo modprobe -r psmouse worked great! Thanks!

---

### Post by sumi76 on 2009-11-04
Hi!

I possibly have a solution for this which is not effected by reboot.
I unticked the "disable touchpad while typing" box as xiphosurus advised,
and managed to disable the touchpad **without** gpointing-device-settings
by [COLOR=Red][COLOR=Black]typing [/COLOR]synclient TouchpadOff=1[/COLOR] in terminal.

I used the gpointing GUI for setting FastTaps and realized, that some of the setting made there (e.g. switching on/off touchpad) are getting wiped out after a few seconds. It seems,
that synclient has priority to handle touchpad issues.

Hope I was of help!

EDIT: sorry, I was wrong, the value for TouchpadOff is changed back to 0 after reboot..

---

### Post by tstduke on 2009-11-08
To make the disable touchpad launcher run the terminal command just right click anywhere and create a launcher, then in the command section paste the following:
gnome-terminal -e "sudo modprobe -r psmouse"

make a launcher to enable the touchpad by doing the same but in the command section paste:
gnome-terminal -e "sudo modprobe psmouse"

When the launcher runs for the first time, the terminal asks for your password as you are using a sudo command.

Its the easiest workaround till it gets fixed

---

### Post by thaitang on 2009-11-19
Why is this thread marked as solved? does a band-aid constitute a solution?

I run xubuntu which is more limited in its mouse options, but the sudo modprobe -r psmouse command works like a charm. I added it to run during start-up, and I also created a couple of alias' for a quick enable and disable in case I want to re-enable that PITA touchpad for some GD unknown reason. 

I had a different fix in 9.04 that worked fine, but of course it doesn't work in Karmic. I wonder why they keep breaking stuff every time there is a new release... yeah yeah yeah I know you can't make an omelette with breaking a few eggs, or something gay like that.

oh well that concludes my whine, so you can now return to your regular programming.
tt

---

### Post by Kognit on 2009-11-19
I marked this thread as solved because this workaround works fine at least for me and it is better to use this workaround than nothing.

---

### Post by JohnnyF on 2009-11-19
> **Kognit said:**
> I marked this thread as solved because this workaround works fine at least for me and it is better to use this workaround than nothing.

But it doesn't work for me and other Thinkpad-Users who just want to disable the Touchpad but not the Trackpoint. On Ubuntu 9.04, this worked with a simple Mouse Click.

Oh how much I hate it if upgrading the OS steals usability!

---

### Post by Kognit on 2009-11-19
Voila, i reversed it to unsolved :)

---

### Post by Kognit on 2009-11-19
> **thaitang said:**
> Why is this thread marked as solved? does a band-aid constitute a solution?

I run xubuntu which is more limited in its mouse options, but the sudo modprobe -r psmouse command works like a charm. I added it to run during start-up, and I also created a couple of alias' for a quick enable and disable in case I want to re-enable that PITA touchpad for some GD unknown reason. 

I had a different fix in 9.04 that worked fine, but of course it doesn't work in Karmic. I wonder why they keep breaking stuff every time there is a new release... yeah yeah yeah I know you can't make an omelette with breaking a few eggs, or something gay like that.

oh well that concludes my whine, so you can now return to your regular programming.
tt

How did you manage to add a command on start-up. I really don't know! Can you show the procedure?

---

### Post by jesseedavis on 2009-11-26
I'm having all sorts of problems with this issue. I'm using an old Gateway 600yg2 and the touchpad works fine, but if I'm using my external mouse (which I prefer to use) and accidentally bump the touchpad then weird things happen. Usually what happens is that the cursor jumps to the corner and just starts clicking on its own and some of the windows or tabs get closed and a bunch of trash windows open or something. It gets irritating sometimes. I have turned the touchpad off in gpointing-device-settings, but even though the touchpad doesn't move anything, it still disrupts my external mouse.

I can't use the 

sudo modprobe -r psmouse  
command because it shuts both the touchpad and the external mouse off. Could this be solved by using a different mouse, possibly?

---

### Post by Kognit on 2009-11-27
Huh, i am not actually expert for this issues but i doubt that different mouse would help though try it anyway.

What about functions keys for disabling the touchpad?

---

### Post by jesseedavis on 2009-11-28
Nope. They don't work either. It seems to me that it is registering both the mouse and the touchpad and so if I'm using the mouse and the touchpad at the same time (through tapping it or other accidental movement) it goes nuts. This makes sense to me.

At the same time it seems to see both as the same thing when it comes to the commands. This could be why the commands shut them both down and not just the intended touchpad.

If this is the case, switching mice wouldn't do anything. Besides, the mouse works perfectly fine. Would drivers have anything to do with it? Maybe the driver for the PS/2 port is either not there or needs updated?? I'll check them all out tomorrow after work, in the meantime, hopefully I can get some advice as to what could even remotely be in the equation. Thanks guys!

---

### Post by pavlosto on 2009-12-05
Maybe this is of some help:
I run 9.10 on a Lenovo T61p.
I confirm that unchecking the 'Disable touchpad when typing' box in System/Preferences/Mouse/Touchpad helps to avoid the toucpad waking up after it has been turned off.

The easiest way to turn it off for me turned out to be: [COLOR="Red"]type [Fn F8][/COLOR]. This button has e blue print showing a touchpad and a trackbutton among 3 keys (apparently g, h and b).

I don't know if this sticks after a reboot, but it's only one keypress... and to be honest: who needs a reboot? Not Linux surely ;-)

Cheers!
p

---

### Post by Vesukka on 2009-12-08
> **pavlosto said:**
> I don't know if this sticks after a reboot, but it's only one keypress... and to be honest: who needs a reboot? Not Linux surely ;-)

Well well... I checked my keyboard as well and guess what, I found a blue pic of mouse and keypad on F1. :oops:
So anyone with Zepto: 'Fn + F1'.

Haven't restarted yet, but the quickest solution for me now. \\:D/

---

### Post by szirakitamas on 2010-01-09
Hi,

this problem was VERY embarassing for me, too. I thought about the solutons listed here, almost made a quick launcher to disable the touchpad.
But I have found in System>Preferencies>Startup Prgograms that there is the touchpad in the list but uncommented/unchecked. I checked the command in Edit menü, amd it is the next one:

gsynaptics-init --sm-disable

I let it run, and it works! It is disabled. No extra solutions, extra buttons or commands, just the bases. :)
I do not know if it is originally there but it is there at me, so it is solution for me. Maybe some times before I have tried to "optimize", to "manage" the number of starting-up programs and then I stopped this. Now it is run and works.

---

### Post by smerral on 2010-01-09
As to the start up commmand I added it to etc/init.d/rc.local immediately after the first line viz:

#! /bin/sh
sudo modprobe -r psmouse

---

### Post by CodeRage on 2010-01-29
Several posts and google results leads aided in getting me to the following resolution on my Dell Inspiron 1501 laptop (purchased in 2007), which uses the Synaptics Touchpad.

**[EDIT]FYI: This is a fresh clean install of Ubuntu 9.10 Karmic Koala rather than an upgrade. As always, use at your own risk.[/EDIT]**

To ensure the target to blacklist does not affect anything else I use, such as my Logitech Nano USB mouse, I went into a terminal and typed: 
```
sudo modprobe -r psmouse
```
If the touchpad does not work, while your preferred mouse does, you're on the right track. So the next thing I did was go into a terminal and type: 
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
Then add the following to the file:
```
# Prevent TOUCHPAD from loading
blacklist psmouse
```
So a snippit of my blacklist.conf file looks like:
```
# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# Prevent TOUCHPAD from loading
blacklist psmouse
```
Save the blacklist.conf file and reboot your machine, and all should be well.

I hope this helps others and provides that persistent solution they are looking for.

Thank You and you're welcome! :popcorn:

---

### Post by Arnold Sideways on 2010-03-16
There is an even simpler solution to this problem. Crude and simplistic and decidedly inelegant though it may be - it works 100% with any program. How?  Stick a piece of stiff card over the mouse pad and use a USB or wireless mouse!

---

### Post by Joe Darkless on 2010-03-19
use package "gsynaptics" where the is the option "enable touchpad". Works with 9.10 great, gnome compatible.
Link for page: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by scebert on 2010-03-21
To be able to disable and enable the touchpad without entering your password, you can modify the sudoers file so that modprope doesn't require a password. Just add this to the end of /etc/sudoers, where username is your user name
```

Cmnd_Alias CMD=/sbin/modprobe
username ALL=NOPASSWD: CMD

```
Once you have done this, you can run this script to toggle the state of touchpad
```

#!/bin/bash

output=`sudo modprobe -v psmouse`
if [ "$output" == "" ]
	then
		sudo modprobe -r psmouse
fi

```
The script can be bound to a shortcut key to easily turn the touchpad on and off.

---

### Post by Kognit on 2010-03-23
If anyone will try to edit the file "sudoers" it should use "visudo" - do not change the permission of the sudoers file because otherwise you will not be able to use sudo command. I had quite a lot of problems yesterday because of it :)

---

