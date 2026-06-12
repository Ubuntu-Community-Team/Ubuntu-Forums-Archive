---
title: "Help with Logitech LX8 wireless laser mouse"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by hAvAAck on 2008-02-01
Hi all, pretty big newbie here,  Running 7.10. I did quite a bit of searching on these forums and google, and found little to no help for my problem, from a newb perspective.

I have a wireless Logitech LX8 mouse, and I want to try to get my buttons working. Currently left click, right click, middle click, and scroll wheel all work excellent.  However I want my back and forward buttons to work as they ar intended in firefox and other such programs.

Currently my back button does nothing and my forward button acts like right-click.

I tried using btnx, but I am kind of at a loss as to how to configure it, or if it even installed correctly because I used .deb for i386, but I'm running 64-bit and had to force it to install.  Any guidance would be appreciated, as I'm looking to really get my hands dirty with Ubuntu.

Thanks

---

### Post by hAvAAck on 2008-02-03
I reinstalled using 32bit and still no luck

---

### Post by pieisgood4589 on 2008-02-03
Drivers, anyone?

---

### Post by hAvAAck on 2008-02-10
I'm not usually one to bump, but I'm getting kinda itchy over here for some help :P

---

### Post by goexplode on 2008-03-05
hAvAAck, I feel your pain. I use the Logitech LX8 cordless mouse too with the Logitech Desktop Wave keyboard, but I haven't had any luck getting the mouse to work properly. I am running Ubuntu 7.10, 64 bit.

I tried [this]("http://ubuntuforums.org/showthread.php?t=65471"), but using "evdev" as the Protocol in xorg.conf caused X to fail several times after restarting with an error that it could not detect my display/video card (which should not be related to the mouse in any way).

Using the "xev" tool, I was able to determine the following:

Left mouse button -> Button 1
Right mouse button -> Button 3
Scroll wheel click -> Button 2
Scroll wheel up -> Button 4
Scroll wheel down -> Button 5
Back button -> Button 2
Forward button -> Button 3
Left and right horizontal scrolling produces the same effect as pressing the left or right arrow keys on the keyboard.

Here is the relevant section from "/etc/X11/xorg.conf"

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"Buttons"	"9"
	Option		"ButtonMapping"	"1 2 3 5 6 7 8 9"
	Option		"ZAxisMapping"	"4 5"
	Option		"Resolution"	"800"
	Option		"Emulate3Buttons"	"false"
EndSection
```


For some reason the back and forward buttons are being detected as Buttons 2 and 3 respectively. This explains why pressing the back button will have the same effect as a scroll wheel click, and the forward button has the same effect as a right click (considering that the mouse is configured for the right hand). It is possible that this is just a problem with the drivers being used and may be fixed in a future update. Once the back and forward buttons can be correctly detected as Buttons 6 and 7 (or anything unique from the other buttons), there should be no problem using xvkbd and xbindkeys to cause them to actually send "Back" and "Forward" events in programs such as Nautilus or Firefox.

I'm hoping that someone with a higher level of experience may be able to offer their suggestions as to how to get this mouse to work. I hope all this is of any help.

---

### Post by goexplode on 2008-03-05
[COLOR="Red"][SIZE="5"]UPDATE:[/SIZE][/COLOR]
It seems that all of the buttons on the LX8 now work by default in Hardy Heron. Furthermore, if you are also using a desktop wave keyboard, most of the multimedia buttons also work by default in Hardy Heron. Although, some of the keys still do not function properly, such as the "zoom" keys, along with some of the keys that require the "Fn" combination, e.g. "Fn + a". This may be an issue addressed in a separate forum topic, although it really isn't a big deal to me if those keys don't function properly for me since I really do not use them too often.




I am hoping that hAvAAck and everyone else that has been looking for help with getting the LX8 working have not given up and are still checking back here for updates.

In any case, after doing some digging, I have come up with the following **solution:** :)

[SIZE="5"]Configuring Logitech LX8 Wireless Mouse[/SIZE]

First of all, I should note that most of this solution consists of bits and pieces from the following:

[INDENT]1. [HOWTO Advanced Mouse]("http://gentoo-wiki.com/HOWTO_Mouse_Nav_Buttons")[/INDENT]
[INDENT]2. [Configuring Logitech Mice]("http://ubuntuforums.org/showthread.php?t=65471")[/INDENT]

**_1. evdev_**
[INDENT]Fire up your favorite terminal and run the following command:

```
cat /proc/bus/input/devices
```

You should receive output that is similar to the following. I have highlighted what we need to pay attention to in bold:

```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120003
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-2/input1
S: Sysfs=/class/input/input2
U: Uniq=
**H: Handlers=kbd mouse1 event2 **
B: EV=f
B: KEY=7fff042c332f bf08444000000000 ff0001 1f848837cc00 667bfadd71dfed 9e000000000000 0
B: REL=1c3
B: ABS=100000000
```

There are several ways to add the information we need to "/etc/X11/xorg.conf", but I have found that the following method is the most simple. Run the following command in a terminal:

```
sudo gedit /etc/X11/xorg.conf
```

Find the mouse section and comment out each line with a "#" so that it is similar to the following:

```
#Section "InputDevice"
#    Identifier    "Configured Mouse"
#    Driver        "mouse"
#    Option        "CorePointer"
#    Option        "Device"        "/dev/input/mice"
#    Option        "Protocol"        "ImPS/2"
#    Option        "Emulate3Buttons"    "true"
#    Option        "ZAxisMapping"        "4 5"
#EndSection
```

Next add the following. It may be easier to just copy and paste:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event2"
	Option		"Buttons"	"9"
	Option		"ZAxisMapping"	"4 5"
	Option		"Resolution"	"800"
EndSection
```

"Device" should be the event number that is given in the "Handlers" line, for me it was "Handlers=kbd mouse1 event2", so I will use event2, but your's may vary. The full path will be "/dev/input/event#", substituting whatever number you got. You may also verify that your "ZAxisMapping" is correct by firing up "xev" in the terminal and scrolling up and down in the window that pops up and taking note of which buttons are triggered.

Finally, save all of the edits that you have made to xorg.conf. You can either perform a full reboot or hold down ctrl-alt-backspace for the changes to take effect.[/INDENT]

**_2. Side (Back/Forward) Buttons With Nautilus & Firefox_**

[INDENT]Confirm that the side buttons are working with "xev". Pressing the back and forward buttons in the window that pops up should show them now being "Button 8" and "Button 9" respectively.

Next, "xvkbd" and "xbindkeys" can be used to bind the side buttons to "ALT + LEFT" and "ALT + RIGHT" so they will work as Back and Forward in Nautilus both and Firefox.

Install "xvkbd" and "xbindkeys":

```
sudo apt-get install xvkbd xbindkeys
```

Create the necessary configuration file:

```
gedit ~/.xbindkeysrc
```

Paste the following:

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:8
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:9
```

Note that the "L" and "R" in the words "left" and "right" in the brackets above should be capitalized (forum bug changes them to lowercase). If "xev" showed the side buttons as being something other than 8 and 9, change the lines "b:8" and "b:9" respectively.

Be sure to keep the quotation marks, save the file and run "xbindkeys" in the terminal. Test to see if the side buttons work in Nautilus or Firefox.

Finally, once everything is working, open up "System -> Preferences -> Sessions" and click on the "Startup Programs" tab. Click "Add" and enter "xbindkeys" for the command. "xbindkeys" should now run each time you log in.[/INDENT]

If everything went well, your Logitech LX8 wireless laser mouse should be fully functioning!

If you have any questions or problems, feel free to let me know. I put this together using what I could find based on other guides that have been written, so credit should go to where it is deserved.

---

### Post by tadtoll on 2008-03-06
GOEXPLOAD said: "...using "evdev" as the Protocol in xorg.conf caused X to fail several times after restarting with an error that it could not detect my display/video card (which should not be related to the mouse in any way)."

I've been trying the solution you posted and also found the posts you referenced, but no matter what I do with evdev, I still have X failing. How did you get around that?

EDIT: I got it. I had pasted "Section "InputDevice" twice. I have it working now with my LX8 mouse. Thanks! All I had wanted to do was disable the "forward" button on the right-hand side of the mouse, which was bound as a right-click.

---

### Post by goexplode on 2008-03-06
I should also note, for any of you also using the LX8 along with the Logitech Cordless Desktop Wave keyboard, using "evdev" for the mouse will also cause the keyboard to use "evdev", even if the "kbd" driver is defined in "xorg.conf". This also causes the multimedia keys to stop working on the keyboard. I'm looking for a solution to this problem but haven't any luck so far. I'll let everyone know if I find anything.

EDIT: By causing the multimedia keys to "stop working", I mean they don't even trigger any sort of events in "xev".

---

### Post by bryonak on 2008-04-02
Excellent post **goexplode**!

Just one minor addition: don't use event handlers to identify your mouse...
Because event numbers change if you plug in other USB devices and/or replug the receiver to a different port, your mouse will stop working without any warning or indication that it might be mapped to a different event. For me, it changes between event6 and event7 if I plug in my USB scanner.

Instead, look again at the output of
```
cat /proc/bus/input/devices
```

The parameters we're looking for are Name and Phys. (In the entry which has a mouse event)

```

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120003
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
**N: Name="Logitech USB Receiver"**
**P: Phys=usb-0000:00:02.0-2/input1**
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2
B: EV=f
B: KEY=7fff042c332f bf08444000000000 ff0001 1f848837cc00 667bfadd71dfed 9e000000000000 0
B: REL=1c3
B: ABS=100000000
```

Now when editing the xorg.conf, notice that you can use wildcards for matching, so "usb-*/input1" will match "usb-0000:00:1a.0-2/input1" or whatever string your specific USB hardware creates for the USB input1.

By the way, I don't think it's necessary to preset the resolution to 800 in xorg.conf, since everyone likes different mouse behaviour ;)

Thus I recommend changing this:

> **goexplode said:**
> 
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event2"
	Option		"Buttons"	"9"
	Option		"ZAxisMapping"	"4 5"
	Option		"Resolution"	"800"
EndSection
```

to this:

```

Section "InputDevice"
        Identifier     "Configured Mouse"
        Driver         "evdev"
        Option         "CorePointer"
        Option         "Name" "Logitech USB Receiver"
        Option         "Phys" "usb-*/input1"
        Option         "Buttons"        "9"
        Option         "ZAxisMapping"   "4 5"
EndSection
```

---

### Post by lenmburu on 2008-04-21
> **bryonak said:**
> Excellent post **goexplode**!

Just one minor addition: don't use event handlers to identify your mouse...
Because event numbers change if you plug in other USB devices and/or replug the receiver to a different port, your mouse will stop working without any warning or indication that it might be mapped to a different event. For me, it changes between event6 and event7 if I plug in my USB scanner.

Instead, look again at the output of
```
cat /proc/bus/input/devices
```

The parameters we're looking for are Name and Phys. (In the entry which has a mouse event)

```

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120003
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-2/input1
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2
B: EV=f
B: KEY=7fff042c332f bf08444000000000 ff0001 1f848837cc00 667bfadd71dfed 9e000000000000 0
B: REL=1c3
B: ABS=100000000
```

Now when editing the xorg.conf, notice that you can use wildcards for matching, so "usb-*/input1" will match "usb-0000:00:1a.0-2/input1" or whatever string your specific USB hardware creates for the USB input1.

By the way, I don't think it's necessary to preset the resolution to 800 in xorg.conf, since everyone likes different mouse behaviour ;)

Thus I recommend changing this:



to this:

```

Section "InputDevice"
        Identifier     "Configured Mouse"
        Driver         "evdev"
        Option         "CorePointer"
        Option         "Name" "Logitech USB Receiver"
        Option         "Phys" "usb-*/input1"
        Option         "Buttons"        "9"
        Option         "ZAxisMapping"   "4 5"
EndSection
```

Help!! I'm also using a Logitech Desktop Wave keyboard mouse set on an Alienware Area 51-5500. The mouse is an LX8. It only works for a few seconds after login into Ubuntu 7.10 then freezes. The keyboard is working ok. I have tried all the configurations on this page and the problem persists. I have run cat /proc/bus/input/devices and the results are: 

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120003
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
**N: Name="Logitech USB Receiver"**
**P: Phys=usb-0000:00:02.0-2/input1**
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2
B: EV=f
B: KEY=7fff042c332f bf08444000000000 ff0001 1f848837cc00 667bfadd71dfed 9e000000000000 0
B: REL=1c3
B: ABS=100000000

I cant do anything with xev because by the time I try to run it, the mouse has hang. I have reinstalled ubuntu twice, and even formatted the partition just to be sure because previously I was using a standard keyboard & microsoft optical wireless mouse, I didn't have any problems then. Am getting so frustrated by this, can somebody please help!!


:guitar: Hey! I fixed the problem! I updated the BIOS on my m/board, its an ASUS P5ND2-SLI. However using 'evdev' as driver doesn't seem to work for me so I used 'mouse' a driver it selected on its own and then adopted bryonak's xorg.conf format above. Now, not only is the mouse not hanging anymore, but all buttons are working as they should including the back & forward buttons. Here is a snippet from my xorg.conf 

```

Section "InputDevice"
        Identifier     "Configured Mouse"
        Driver         "mouse"
        Option         "CorePointer"
        Option         "Name" "Logitech USB Receiver"
        Option         "Phys" "usb-*/input1"
        Option         "Buttons"        "9"
        Option         "ZAxisMapping"   "4 5"
EndSection
```

:)

---

### Post by hazza96 on 2008-04-24
> **goexplode said:**
> This also causes the multimedia keys to stop working on the keyboard. I'm looking for a solution to this problem but haven't any luck so far. I'll let everyone know if I find anything.
I found a solution, use the "mouse" driver instead. The back and forward buttons work fine and so do the multimedia keys on the keyboard.

---

### Post by hAvAAck on 2008-06-02
I'm back, and having a bit of trouble with this.
I appreciate all the help, at this point xev is notifying me that

1 LB 
2 MB 
3 RB 
4 MB scroll up 
5 MB scroll down

2 back button
3 forward button

MB scroll right/left gives
> 
KKeyRelease event, serial 31, synthetic NO, window 0x3400001,
    root 0x13b, subw 0x0, time 6451355, (125,74), root:(132,125),
    state 0x10, keycode 78 (keysym 0xff14, Scroll_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x3400001,
    root 0x13b, subw 0x0, time 6451371, (125,74), root:(132,125),
    state 0x10, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


Obviously there's several things wrong. Any guidance? I got caught up with school work (last semester is a bitch, stuck on vista) and now I'm back with ubuntu, trying to convert
Oh, I'm on 8.04 32bit now. New install.

Thanks

---

### Post by goexplode on 2008-06-02
> **hAvAAck said:**
> I'm back, and having a bit of trouble with this.
I appreciate all the help, at this point xev is notifying me that

1 LB 
2 MB 
3 RB 
4 MB scroll up 
5 MB scroll down

2 back button
3 forward button

MB scroll right/left gives


Obviously there's several things wrong. Any guidance? I got caught up with school work (last semester is a bitch, stuck on vista) and now I'm back with ubuntu, trying to convert
Oh, I'm on 8.04 32bit now. New install.

Thanks
hAvAAck, with Ubuntu 8.04, all of the buttons on the mouse seem to "just work." For some reason pressing the left or right scroll on the mouse wheel seems to give the same output in xev as pressing the left or right arrows on the keyboard, although this should not be a problem since pressing those buttons will result in horizontal scrolling. Unfortunately, I am unaware of any method for changing the speed of horizontal scrolling.

Furthermore, the left and right (back and forward) buttons on the mouse will work automatically with Firefox 3b2 in Ubuntu 8.04, but who knows if this will change in the future. In any case, if you would like to enable the left and right buttons for Nautilus in 8.04, you only need to follow the steps under "**2. Side (Back/Forward) Buttons With Nautilus & Firefox**" in my first post.

---

### Post by hAvAAck on 2008-06-02
Thanks, my problem is that forward and back are the same "button" as middle and right click. I'm on 8.04 with FF3b2 and they're not working.

---

### Post by goexplode on 2008-06-02
> **hAvAAck said:**
> Thanks, my problem is that forward and back are the same "button" as middle and right click. I'm on 8.04 with FF3b2 and they're not working.
Are you on a fresh install of 8.04? My experience has been that the buttons work automatically on a fresh install, therefore I have not tested any of the instructions that I previously posted.

I should also note that I have switched to Fedora 9 after a couple of years of Ubuntu, since Hardy Heron has let me down in so many ways. :-/ We'll see if 8.10 will win me back.

---

### Post by goexplode on 2008-06-02
> **hAvAAck said:**
> Thanks, my problem is that forward and back are the same "button" as middle and right click. I'm on 8.04 with FF3b2 and they're not working.
Also, did you follow the instructions from my first post? If so, I cannot guarantee that they will work in 8.04. Can you post the contents of xorg.conf? If I remember correctly, 8.04 attempts to autodetect the mouse and keyboard and should (keyword: should), automatically load the correct driver.

---

### Post by hAvAAck on 2008-06-02
My handler showed the same as yours, but when I entered your xorg.conf for the mouse, I lost all ability to move the mouse horizontally.

contents of xorg.conf
> 
# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600 GT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection


---

### Post by goexplode on 2008-06-02
> **hAvAAck said:**
> My handler showed the same as yours, but when I entered your xorg.conf for the mouse, I lost all ability to move the mouse horizontally.

contents of xorg.conf
See [this post]("http://ubuntuforums.org/showpost.php?p=4636059&postcount=9"). Your "Configured Mouse" section in your xorg.conf will end up looking similar to the following:

```
Section "InputDevice"
        Identifier     "Configured Mouse"
        Driver         "evdev"
        Option         "CorePointer"
        Option         "Name" "Logitech USB Receiver"
        Option         "Phys" "usb-*/input1"
        Option         "Buttons"        "9"
        Option         "ZAxisMapping"   "4 5"
EndSection
```

Although, I'm not sure how well the "evdev" driver is working in 8.04. You might try changing "evdev" to "mouse" as the driver instead.

---

### Post by hAvAAck on 2008-06-03
Ah yes, that actually worked no problem. I had to check my input and use "mouse" driver and now everything *just works*
Thanks again!

---

### Post by goexplode on 2008-06-03
> **hAvAAck said:**
> Ah yes, that actually worked no problem. I had to check my input and use "mouse" driver and now everything *just works*
Thanks again!
Glad I could help!

---

### Post by hazza96 on 2008-06-04
On the 24th of April:
> **hazza96 said:**
> I found a solution, use the "mouse" driver instead. The back and forward buttons work fine and so do the multimedia keys on the keyboard.

**41 days** later:
> **goexplode said:**
> Although, I'm not sure how well the "evdev" driver is working in 8.04. You might try changing "evdev" to "mouse" as the driver instead.

Instead of reading the thread you get someone to repeat the solution I already posted over a month a go, then you thank *them*? *sigh*

---

### Post by goexplode on 2008-06-04
> **hazza96 said:**
> On the 24th of April:


**41 days** later:


Instead of reading the thread you get someone to repeat the solution I already posted over a month a go, then you thank *them*? *sigh*
hazza96, perhaps hAvAAck was just having a momentary lapse in sanity while he was scrolling through all of the posts searching for a solution and accidentally overlooked your post. :tongue:

In any case, *thank you*! :D

---

### Post by hAvAAck on 2008-06-05
> **hazza96 said:**
> On the 24th of April:


**41 days** later:


Instead of reading the thread you get someone to repeat the solution I already posted over a month a go, then you thank *them*? *sigh*

I did read the thread, but managed to miss a lot of things. Not to mention half the posts are too old to "thank" so please forgive me if I overlooked a 1 sentence post in a jumble of code.

---

### Post by hazza96 on 2008-06-05
ha ha... it's fine, I have been overwhelmed reading some long threads and missed the solution amongst all the ramblings and tangents.

---

