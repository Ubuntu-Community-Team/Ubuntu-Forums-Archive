---
title: "HOWTO: MX5000 Bluetooth Keyboard and MX1000 Laser Mouse Combo in Hardy"
date: 2008-04-25
forum: Hardware
---

### Post by Curtisc on 2008-04-25
I had a ton of problems with this set in Gutsy, but it went much more smoothly in Hardy, so I thought I'd post what I did to get them working just right.

**Pairing the Bluetooth Devices**
[LIST=1]
[*]I needed an extra mouse and keyboard to set this up.  If you get it working without these, please let me know!
[*]Right click on the bluetooth icon in your notification panel (if your adapter is correctly detected, it should be there), and choose preferences.  Go to the "General" tab, and check "Automatically authorize incoming requests".
[*]Click on the "Services" tab, then "input services".  A blank box should appear at the bottom.
[*]Click the "add" button.  If your mouse is on the list that pops up, select it and click "connect".  If not, press the red connection button on the mouse, and it should show up.  You might have to press the red button on the mouse several times.
[*]Do the same thing to add the keyboard.  This time, a notification will appear with a button to enter your passkey.  Click on it, and a box will pop up.  On your extra keyboard, type in your passkey.  Mine seems to want "3501", but I've heard that "1234" is the default.
[*]The LCD on the keyboard should be prompting you for a passkey.  Type in the same number as before, using the number row (not the numpad) and hit Enter.
[/LIST]
That's all it took for my keyboard and mouse to start working, even connecting whenever I reboot.  However, I wanted to get the buttons on the mouse working just right.  I tried using btnx, but I kept on having issues with the thumb button sending the same event as the middle button, so I eventually just went with a slightly modified version of [this very useful howto](https://help.ubuntu.com/community/MX1000Mouse).  I'll condense information from that page a little, with a few changes for Hardy.

**Configuring the MX1000 mouse and custom buttons**
[LIST=1]
[*]Make sure you have the necessary programs installed:```
sudo apt-get install xbindkeys xvkbd
```
[*]To figure out which event controls your mouse, type in: ```
cat /proc/bus/input/devices
```
A number of devices will probably show up.  Look through the output until you find something that looks like the MX1000 - on mine, it's:
```
I: Bus=0005 Vendor=046d Product=b003 Version=4320
N: Name="Logitech MX1000 mouse"
P: Phys=00:07:61:7B:33:3D
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2.1/1-2.1:1.0/hci0/acl00076180018D/input/input14
U: Uniq=00:07:61:80:01:8D
H: Handlers=mouse3 event8 
B: EV=17
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10
```
The important part of this output is event listed in "Handlers".  In my case, it's event8.

[*]Make a backup of xorg.conf: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
[*]Open xorg.conf for editing: ```
gksudo gedit /etc/X11/xorg.conf
```
[*]Delete (or comment out) everything in the section with the identifier "Default Mouse" or "Configured Mouse" (between and including Section "Input Device" ... EndSection)
[*]Add the following lines after your keyboard section: ```
Section "InputDevice"
	Identifier	"Logitech MX1000"
	Driver		"evdev"
	Option		"Device"	"/dev/input/event8" 
	# If your event handler is something other than event8, 
	# change it to the appropriate value
	Option 		"RelHWHEELMapTo"	"Buttons 7 6"
EndSection
```
[*]In the "ServerLayout" add: ```
InputDevice	"Logitech MX1000"	"CorePointer"
```
If you don't want the MX1000 to be your Core Pointer, you could change this to "SendCoreEvents" instead.

[*]Save what you've done so far as well as any other work in other programs you have open, and restart X (ctrl + alt + backspace)

[*]If you can log in and use your mouse, all is well so far.  Just a few more steps to get the thumb buttons working.

[*]Create a file in your home directory called ".xbindkeysrc", and open it in gedit: ```
gedit .xbindkeysrc
```
[*]Paste in the following lines:```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
```
Save and close the file.

[*]```
xbindkeys &
```
[*]If your forward and back buttons work (in firefox, nautilus, Eye of GNOME, etc), then the xbindkeys configuration worked.  Vertical and Horizontal scrolling should work without any further configuration (I've tested it in Firefox 3 and Inkscape).

[*]Add xbindkeys to your startup programs (System->Preferences->Sessions)

[*]The little round side button is Button10 (or b:10 in xbindkeys).  I map it to the scale plugin in compizconfig-configuration-manager, but you might prefer to map it to something else. 
[/LIST]
And that should be it.  It seems like a fair bit of work, but it actually was easier than in Gutsy.

I hope this is clear - it's my first howto, so any constructive criticism is greatly appreciated.

Edit: if you lose some buttons at start up or get disconnected after some time away, check out [puffyzcad's post (#34)](http://ubuntuforums.org/showpost.php?p=5101296&postcount=34) for a solution

---

### Post by dhollman on 2008-04-27
Hi,
      I have followed your instructions, and have gotten both the keyboard and mouse to work.  I don't have problems with detection upon reboot or logout anymore.  However, I still cannot get the thumb buttons to work as back/forward in my browser.  Any ideas?

---

### Post by Curtisc on 2008-04-27
> **dhollman said:**
> Hi,
      I have followed your instructions, and have gotten both the keyboard and mouse to work.  I don't have problems with detection upon reboot or logout anymore.  However, I still cannot get the thumb buttons to work as back/forward in my browser.  Any ideas?

Glad to hear the bluetooth stuff is working for you.  As to the thumb buttons, let's try checking to see if xbindkeys is configured properly.  Try typing this in:
```
xbindkeys -k
```
When the little window pops up, click on the back button of the mouse.  If the output says "Alt + Left", then xbindkeys is configured properly and the problem is somewhere else.  If not, please post the output here and we can try to figure it out from there.

---

### Post by jellygoeswobble on 2008-04-28
Hi! First of all, thankyou again for this post - it did seem much easier than in 7.10! Secondly, I just thought I'd share with you that I dont actually use the xbindkeys configuration, I use the thumb buttons to initiate the rotation of the desktop cube, and to initiate expo, respectively. Just thought Id share because this is a very useful configuration! I find it is more useful to use the rocker-left and rocker-right motions to navigate backwards and forwards in firefox, and I too use the round button for Scale. Try it out! If you use the cube and expo, that is.

---

### Post by Curtisc on 2008-04-28
> **jellygoeswobble said:**
> Hi! First of all, thankyou again for this post - it did seem much easier than in 7.10! Secondly, I just thought I'd share with you that I dont actually use the xbindkeys configuration, I use the thumb buttons to initiate the rotation of the desktop cube, and to initiate expo, respectively. Just thought Id share because this is a very useful configuration! I find it is more useful to use the rocker-left and rocker-right motions to navigate backwards and forwards in firefox, and I too use the round button for Scale. Try it out! If you use the cube and expo, that is.

Hi!  You bring up a very good point - xbindkeys isn't necessary if you want to bind the mouse buttons to compiz functions.  I don't actually use multiple desktops (I have a bad habit of forgetting about them), but I can definitely see how those buttons would be useful for that.

---

### Post by specs10 on 2008-04-28
Have you had problems with the connection getting dropped after the devices go idle or after the screensaver is activated?  Whenever I step away from my computer for a while, I lose all functionality from both my keyboard and mouse.  Only a reboot seems to fix it.

---

### Post by puffyzacd on 2008-04-29
I was very excited to see your post since I've been struggling with getting this set up for days. Unfortunately I was unable to get things working with your instructions. Pairing is no problem, but getting the mouse buttons working in still giving me trouble. The thumb button still shows up as button 2 (the scroll wheel button) in xev, and left and right scroll do not show up at all.

The only difference I can see between what we did is that I set my mouse as "SendCoreEvents" and not "CorePointer". I've never gotten things to work properly using the "CorePointer" option. In Hardy my mouse just doesn't move, in previous versions X would crash.

Do you have any advice as to what I should try next? Thanks! :)

---

### Post by nhasian on 2008-04-29
I finally took the plunge and installed Ubuntu 8.04 Hardy Heron on my HP dv9500t laptop today.  The first thing i wanted to do was to get my bluetooth Microsoft Laser Mouse 8000 working since the built in touchpad has sucked since day one.

Thanks for the step by step instructions to bind the mouse to the laptop.  all the buttons worked right away and i didnt have to fuss with it.

---

### Post by puffyzacd on 2008-05-01
> **puffyzacd said:**
> I was very excited to see your post since I've been struggling with getting this set up for days. Unfortunately I was unable to get things working with your instructions. Pairing is no problem, but getting the mouse buttons working in still giving me trouble. The thumb button still shows up as button 2 (the scroll wheel button) in xev, and left and right scroll do not show up at all.

The only difference I can see between what we did is that I set my mouse as "SendCoreEvents" and not "CorePointer". I've never gotten things to work properly using the "CorePointer" option. In Hardy my mouse just doesn't move, in previous versions X would crash.

Do you have any advice as to what I should try next? Thanks! :)

I was able to solve my mouse problems by writing a udev rule in /etc/udev/rules.d/10-local.rules:

```
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{uniq}=="00:07:61:35:2B:0F", NAME="input/mx1000"
```

I believe that ATTRS{uniq} key is the bluetooth address, but you can also find it under your mouse by running

```
cat /proc/bus/input/devices
```

The only problem I have now is that my mouse stops working when it goes to sleep...but I'm still working on it. I'll post if I have any success.

---

### Post by DaveBG on 2008-05-02
OK i did as mentioned in the info in 1st post but no go :(

```
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB RECEIVER"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	InputDevice	"Logitech MX1000"	"CorePointer"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

Here is my xorg.conf that my mouse not works with :(

Can someone advise where i am mistaken?

I have wired mouse that works OK, but when i do this both do not work...

I maybe have to remove it?

---

### Post by puffyzacd on 2008-05-02
> **DaveBG said:**
> Here is my xorg.conf that my mouse not works with :(

Can someone advise where i am mistaken?

I have wired mouse that works OK, but when i do this both do not work...

I maybe have to remove it?

I think the problem with your xorg.conf is this part:
```
        Option          "Name"          "Logitech USB RECEIVER"

``` 

The new evdev driver doesn't seem to like the "Name" option, instead you should try using the "Device" "/dev/input/event*" option. Good luck!

---

### Post by DaveBG on 2008-05-03
> **puffyzacd said:**
> I think the problem with your xorg.conf is this part:
```
        Option          "Name"          "Logitech USB RECEIVER"

``` 

The new evdev driver doesn't seem to like the "Name" option, instead you should try using the "Device" "/dev/input/event*" option. Good luck!

Does not work either. Both mouses no go again :(

---

### Post by chikkensoop on 2008-05-03
> **Curtisc said:**
> When the little window pops up, click on the back button of the mouse.  If the output says "Alt + Left", then xbindkeys is configured properly and the problem is somewhere else.  If not, please post the output here and we can try to figure it out from there.

Hiya, firstly thanks for the Howto, works a charm other than the back/forward buttons... here is my output from xbindkeys -k:

```
Press combination of keys or/and click under the window.
You can use one of the two lines after "NoCommand"
in $HOME/.xbindkeysrc to bind a key.
"NoCommand"
    m:0x8 + c:64
    Alt + Alt_L
```

Been trying to fiddle with .xbindkeysrc to figure it out but it's eluding me atm!

---

### Post by mankyd on 2008-05-03
Tweak to the first post, and in response to the above post, xvkbd is picky about capitalization. I had to make .xbindkeysrc equal to the following:

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
```

Then everything worked like a charm.

---

### Post by chikkensoop on 2008-05-03
The text you posted is identical to that on the first page and in my .xbindkeysrc file, so no change I'm afraid... still not working!

---

### Post by Curtisc on 2008-05-03
> **chikkensoop said:**
> Hiya, firstly thanks for the Howto, works a charm other than the back/forward buttons... here is my output from xbindkeys -k:

```
Press combination of keys or/and click under the window.
You can use one of the two lines after "NoCommand"
in $HOME/.xbindkeysrc to bind a key.
"NoCommand"
    m:0x8 + c:64
    Alt + Alt_L
```

Been trying to fiddle with .xbindkeysrc to figure it out but it's eluding me atm!

That is a very strange result.  On my computer, without the xbindkeys configuration, I get no output from xbindkeys -k.  If it's the same with your system, then it seems as though the keybinding is working, but instead of "Left" it's giving you "Alt_L".  Maybe you could try the lowercase version that mankyd posted?  Mine seems to like the capitalization,  but maybe yours would prefer lowercase.

[QUOTE=puffyzcad]The only problem I have now is that my mouse stops working when it goes to sleep...but I'm still working on it. I'll post if I have any success.[/QUOTE]
Mine does that too occasionally.  However, it also does it in windows, so I had chalked it up to the device going to sleep rather than any kind of configuration issue that we have control over.  If you google "mx5000 lose connection" you get tons of people talking about the problem.  However, it'd be awesome if there were some sort of solution.  I find that banging the mouse down on the table sometimes works (seriously).

@DaveBG: From the xorg.conf file that you posted, it seems as though the device that you're configuring is the Bluetooth dongle, not the mouse.  Did you unplug the dongle and plug it back in?  If you do this, then the mouse and keyboard will not show up under /proc/bus/input/devices.  If you reboot the computer, making sure that the Bluetooth dongle is plugged in the whole time, and then do "cat /proc/bus/input/devices", you should get three Logitech related devices (actually, I get four, because I have two listings for the dongle, but I'm not sure if that's normal).  Then you can get the device number for the mouse and add that to xorg.conf.

---

### Post by blindman4556 on 2008-05-04
my forward and back keys worked without xbindkeys..the only thing i needed to bind was the little round button on the side, it works.....the only problem i have is have xbindkeys start up when i turn on computer, and to those ppl that are going to say go to sessions and add it, i did.

---

### Post by DaveBG on 2008-05-05
> **puffyzacd said:**
> I think the problem with your xorg.conf is this part:
```
        Option          "Name"          "Logitech USB RECEIVER"

``` 

The new evdev driver doesn't seem to like the "Name" option, instead you should try using the "Device" "/dev/input/event*" option. Good luck!

I try but i cant understand which it is :(

So i have:

Section "InputDevice"
    # generated from default
	Identifier	"Logitech MX1000"
	Driver		"evdev"
	Option		"Device"	"/dev/input/event**[COLOR="Red"]*[/COLOR]**" 
	Option 		"RelHWHEELMapTo"	"Buttons 7 6"
EndSection


Bu see how many event**[COLOR="Red"]*[/COLOR]** i have:

[[IMG]http://img176.imageshack.us/img176/7938/screenshotep1.th.png[/IMG]](http://img176.imageshack.us/my.php?image=screenshotep1.png)

How do i identify it?

---

### Post by Curtisc on 2008-05-06
> **DaveBG said:**
> 
How do i identify it?

Open up a terminal, and type in "cat /proc/bus/input/devices".  This should spit out a list of devices and tell you which event controls which.  The line you need for is "Handlers=mousex, eventy".

---

### Post by DaveBG on 2008-05-06
> **Curtisc said:**
> Open up a terminal, and type in "cat /proc/bus/input/devices".  This should spit out a list of devices and tell you which event controls which.  The line you need for is "Handlers=mousex, eventy".

Thank you i found that it is event2.

I entered it and then the same. Old mouse works MX1000 not.

Also the whole X was broken and run in low graphics mode :(

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Logitech USB RECEIVER" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
	Identifier	"Logitech USB RECEIVER"
	Driver		"evdev"
	Option		"Device"	"/dev/input/event2" 
	Option 		"RelHWHEELMapTo"	"Buttons 7 6"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


```
dave@dave-desktop:~$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c50e Version=0111
N: Name="Logitech USB RECEIVER"
P: Phys=usb-0000:00:0b.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb1/1-2/1-2:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=20017
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10
B: LED=ff00

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0001 Version=0001
N: Name="PS/2 Logitech Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse2 event6 
B: EV=7
B: KEY=30000 0 0 0 0 0 0 0 0
B: REL=3

```

I think its some conflict and the old mouse messes us things...

---

### Post by Curtisc on 2008-05-06
> **DaveBG said:**
> Thank you i found that it is event2.

I entered it and then the same. Old mouse works MX1000 not.

Also the whole X was broken and run in low graphics mode :(

I think its some conflict and the old mouse messes us things...

I think the thing that's breaking your X is the line 'InputDevice    "Mouse0" "CorePointer"'.  You have no device named "Mouse0" in your configuration file, so it's going to complain when it looks for it.  I think that X *should* work if you delete this line.

However, it's still weird that your mouse is called "Logitech USB Receiver".  Do you have the Bluetooth version?  If so, make sure that you don't unplug the receiver after booting up the computer, because this puts it into USB emulation mode and it won't configure properly (basically you're telling the computer that the Bluetooth dongle is a mouse).  If you've got the wired MX1000, then I think you're okay.

---

### Post by DaveBG on 2008-05-06
It is USB to the PC, i have it attached to USB with cable to charge station and the mouse is wireless i think it is Bluetooth to the station because it is definitely not infra..
I never unplug the charging station from the USB port.

---

### Post by Curtisc on 2008-05-07
> **DaveBG said:**
> It is USB to the PC, i have it attached to USB with cable to charge station and the mouse is wireless i think it is Bluetooth to the station because it is definitely not infra..
I never unplug the charging station from the USB port.

It could be RF (I believe logitech has an RF version).  Is your mouse detected when you use the bluetooth preferences to pair the devices (as per the first post in this thread)?  If not, then it might be straight RF, in which case your "USB Logitech Receiver" device could be the right one.

Does removing 'InputDevice "Mouse0" "CorePointer"' fix your X breakage?

---

### Post by begemot. on 2008-05-11
**[puffyzacd]("http://ubuntuforums.org/showpost.php?p=4864182&postcount=11")**, **[Curtisc]("http://ubuntuforums.org/showpost.php?p=4894714&postcount=19")**
Thank You, Gentlemans! 
Your advices solved my problem. I have got unworked my sweet "A4Tech X7" with **evdev** driver in 8.04 Hardy, but i commented "Name" line and indicated "Device" option - that's all! (:

Many thanks again.

---

### Post by Skerit on 2008-05-12
I've always had the boot- or the screensaver-problem, but when I reconnected the 2 devices using the bluetooth manager it always worked.

Now, however, I can reconnect them, but the mouse can't control my cursor and the keyboard can't do anything either, even though they're perfectly connected.

---

### Post by Curtisc on 2008-05-12
> **Skerit said:**
> I've always had the boot- or the screensaver-problem, but when I reconnected the 2 devices using the bluetooth manager it always worked.

Now, however, I can reconnect them, but the mouse can't control my cursor and the keyboard can't do anything either, even though they're perfectly connected.

I've got this same problem (at least with the mouse, not sure why your keyboard would stop working).  I think it's because when the mouse goes to sleep (to save batteries) the evdev driver is unloaded.  Try looking at  /var/log/Xorg.0.log to see if there's anything about evdev being unloaded.

Unfortunately, I have no idea how to fix this problem... anyone else?

---

### Post by DaveBG on 2008-05-17
> **Curtisc said:**
> Does removing 'InputDevice "Mouse0" "CorePointer"' fix your X breakage?

Yes! 10x

That fixed it. Now only the XM1000 works ... but again only the first 5 seconds after i move it first time then it stops responding...

As it gets to sleep :(

---

### Post by aseem on 2008-05-18
> **jellygoeswobble said:**
> Hi! First of all, thankyou again for this post - it did seem much easier than in 7.10! Secondly, I just thought I'd share with you that I dont actually use the xbindkeys configuration, I use the thumb buttons to initiate the rotation of the desktop cube, and to initiate expo, respectively. Just thought Id share because this is a very useful configuration! I find it is more useful to use the rocker-left and rocker-right motions to navigate backwards and forwards in firefox, and I too use the round button for Scale. Try it out! If you use the cube and expo, that is.


I have managed to set up the thumb buttons to rotate the Compiz cube, and i like this setup a lot.  Scroll wheel tilt buttons are used for back/forward in Firefox.  However, I am unable to set up the center thumb button in Compiz.  When I use the CompizConfig Setting Manager, the list of mouse buttons ends at Button-9 and the center button is 10.

---

### Post by Curtisc on 2008-05-18
> **aseem said:**
> I have managed to set up the thumb buttons to rotate the Compiz cube, and i like this setup a lot.  Scroll wheel tilt buttons are used for back/forward in Firefox.  However, I am unable to set up the center thumb button in Compiz.  When I use the CompizConfig Setting Manager, the list of mouse buttons ends at Button-9 and the center button is 10.

Even though the list only goes to Button9, try just typing in Button10 - it should work fine.

---

### Post by aseem on 2008-05-22
No that didn't work in CompizConfig Settings Manager, but if I use Gnome Conf Editor, I could just type "Button10".

---

### Post by fsm on 2008-05-24
Does anyone have a problem with the event # changing on reboots?  

I am trying to debug a similar setup (non-bluetooth mouse, but same technique works).  I used this in my xorg.conf:

Option		"Device"	"/dev/input/event6" 

Problem is when I boot, I sometimes the mouse handler is on event6, sometimes event7 (swaps with something else).  Similarly, my video devices (webcam and tuner) also swap positions.

Is there a way to force my devices to always be on the same event handler, or bind them to some other constant device?

---

### Post by puffyzacd on 2008-05-24
> **fsm said:**
> Is there a way to force my devices to always be on the same event handler, or bind them to some other constant device?

This is the purpose of the udev rule that I described in an earlier post (on page 1 of this thread). It maps the mouse to the device /dev/input/mx1000

Hopefully this helps!

---

### Post by puffyzacd on 2008-05-24
> **Curtisc said:**
> I've got this same problem (at least with the mouse, not sure why your keyboard would stop working).  I think it's because when the mouse goes to sleep (to save batteries) the evdev driver is unloaded.  Try looking at  /var/log/Xorg.0.log to see if there's anything about evdev being unloaded.

Unfortunately, I have no idea how to fix this problem... anyone else?

I've noticed this same problem, although for me it is most notable during startup. If I'm not moving the mouse while X is starting up, it won't find the mouse and so it unloads evdev (I can verify this in the /var/log/Xorg.0.log file). My mouse works after, but I lose some of my buttons. :(

I have no idea how to approach this problem, definitely out of my league...

---

### Post by puffyzacd on 2008-06-02
> **Curtisc said:**
> I've got this same problem (at least with the mouse, not sure why your keyboard would stop working).  I think it's because when the mouse goes to sleep (to save batteries) the evdev driver is unloaded.  Try looking at  /var/log/Xorg.0.log to see if there's anything about evdev being unloaded.

Unfortunately, I have no idea how to fix this problem... anyone else?

I don't know if anyone is still reading this thread, but I think I've found a solution to this problem.

Apparently the problem is that xserver-xorg doesn't support hotplugging of devices, so the evdev driver is either loaded when X starts, or not loaded at all. If a device is "unplugged" (or in this case goes to sleep), even when it is reconnected the evdev driver is not reloaded.

Well it turns out the devs are working on supporting this hotplugging behavior, maybe for Hardy+1, but the adventurous can enable it now by following the steps laid out in [this post]("http://ubuntuforums.org/showpost.php?p=4816326&postcount=4").

So, I changed my xorg.conf mouse section to
```
Section "InputDevice"
	Identifier	"Logitech MX1000"
	Driver		"mouse"
	Option		"Protocol"	"auto"
	Option		"Device"	"/dev/input/mice"
	Option 		"RelHWHEELMapTo"	"Buttons 7 6"
EndSection
```

And added the following into /etc/hal/fdi/policy/10-x11-input.fdi
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <merge key="input.x11_driver" type="string">mouse</merge>
      <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name"
             string="Linux">
        <merge key="input.x11_driver" type="string">evdev</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

Now all my buttons work every time, even when booting up or coming back to the computer after several hours.

Also, this approach makes the udev rule unneccessary since it takes care of loading evdev for the proper device for us! Anyway, hope someone else who stumbles across this might find it useful.

---

### Post by Curtisc on 2008-06-03
puffyzcad, that's amazing, I'd given up on that problem!  I found that the fdi stuff also works when added to /etc/hal/fdi/policy/preferences.fdi in case you want to have everything in one file.  Thanks a lot, I'll update the first post in case any looks.

---

### Post by Curtisc on 2008-06-06
puffyzcad (or anyone else that's reading this):
I found a bit of a problem with that fdi policy.  Apparently the BT receiver reports itself as having mouse capabilities, so I was getting all kinds of crazy input (single click was acting as double, everything moving at twice the speed, etc).  So, here's my new fdi policy:
```
  <device>
    <match key="info.product" string="Logitech MX1000 mouse">
	  <merge key="input.device.set" type="string">/dev/input/mx1000</merge>
      <merge key="input.x11_driver" type="string">mouse</merge>
      <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name" string="Linux">
        <merge key="input.x11_driver" type="string">evdev</merge>
      </match>
    </match>
  </device>
```
As you can see, I also changed the device from /dev/input/mouse to /dev/input/mx1000, so that needs to be changed in xorg.conf.  I don't even know if this is necessary, but I figured I'd give it its own special device instead of using the generic "mice" device.

Now the last thing to solve is the bluetooth connection problem...

---

### Post by Kiwi-Hawk on 2008-07-15
Hi

Been fighting with this for a bit,..

I can see keyboard but no mouse and when I select connect I get

------------------------------------------------------
Couldn't display "obex://[00:07:61:98:ec:0c]/"

error: host down
Please select another viewer and try again
-------------------------------------------------

The other day it was Mouse that showed and not the Keyboard

--------------------------------------------------
Couldn't display "obex://[00:07:61:98:c1:a2]/"

error: host down
Please select another viewer and try again
----------------------------------------------

am I right in thinking these are mac address's if so I'm still not close
to getting it going,.. strangely enough I looked at Mythbuntu and it worked fine there, anbody knw what the difference is in under garage?

Cheers
Kiwi-Hawk

---

### Post by Kiwi-Hawk on 2008-07-16
Hi

Second message same as first,..

I have followed the howto's and put the text in policy also

and it has made no difference at all


------------------------------------------------------
Couldn't display "obex://[00:07:61:98:ec:0c]/"

error: host down
Please select another viewer and try again
-------------------------------------------------

--------------------------------------------------
Couldn't display "obex://[00:07:61:98:c1:a2]/"

error: host down
Please select another viewer and try again
----------------------------------------------

Is all I get


Cheers
Kiwi-Hawk

---

### Post by EnlistedSquire on 2008-07-31
Hi,

I used this How To to set up my stand alone, RF (not bluetooth) MX1000 after updgrading to Hardy and apart from the previously mentioned problem of the event number changing from time to time it worked fine.

However, I came back to my PC after a few days of not using it earlier this week and it's gone totally to pot. I can no longer get the horizontal scrolling to work - the left and right mouse wheel buttons don't give a button number in xev and they seem to have picked up the same output as the volume + and - on my keyboard (which have been working fine from day one).

The cruise buttons now give the same button number as scrolling the mouse wheel up and down (buttons 4 and 5) when they were previously different as I had the cruise buttons assigned to Page Up and Page Down. I tried install lomoco and disabling SmartScroll and the cruise buttons no longer get a button assignment in xev either. This is what xev gives for my crusie button with SmartScroll disabled:

```
MotionNotify event, serial 31, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 867717, (64,36), root:(1775,221),
    state 0x10, is_hint 0, same_screen YES
```

Here is what my previously working xorg.conf looks like:

```
Section "InputDevice"
	Identifier	"Logitech MX1000"
	Driver		"evdev"
	Option		"Device"	"/dev/input/event2" 
	# If your event handler is something other than event8, 
	# change it to the appropriate value
	Option 		"RelHWHEELMapTo"	"Buttons 7 6"
EndSection
```

Can anyone offer an idea as to what's gone wrong and how to fix it? I've tried powering everything off to give the mouse a hard-reset and started these instructions totally from scratch from a default xorg.conf.

I had a go using BtnX but couldn't get the horizontal mouse wheel action to work (I assume because it's not compatible with evdev so I was using the standard mouse driver).

Thanks. :)

---

### Post by EnlistedSquire on 2008-08-08
Bump, I could really do with some help here. I've been experimenting with xmodmap with no joy either. My button assignments seem to change every few boots with out me doing anything. What could be causing that?

Thanks.

---

### Post by Spif on 2008-08-29
Thanks a lot for this guide.

Just a few tips on authenticating and connecting the keyboard:

1. The passkey is impossible to know. Keep trying with "1234", at some point it will accept it. 
2. You don't need a spare keyboard. Use the Character Map program to type "1234", mark it with your mouse, right click, press copy and insert it as passkey.
3. When your keyboard passkey is accepted, the screen on the mx5000 keyboard will say "Passkay........". Type 1234 and press enter. Remember to use the numbers above the letters. The numpad can cause issues.
4. After this go to the Bluetooth applet, find the "Input service" and look for the keyboard. Try to connect it. I had to do it a few times.
5. Under Bluetooth preferences, set both devices as trusted.
6. Enjoy your shitty keyboard and mouse in Ubuntu :)

My keyboard and mouse are now working perfectly. Even when I turn on my computer, they are both connected without me doing anything.

---

### Post by tlepes on 2008-09-14
okay this thread looks promising here. my brother has a spare set that will soon be on a a linux media center we're building (mythbox) so i am playing with it on my computer to see how it works for things like my cell phone...

does anyone know how this dongle works for doing things like pairing with cell phones, esp. file transfer (music and pics both ways) and audio gateway (so i can have the cell phone use the computer's speakers and possibly a mic too (i have a headset).  if it can work for those things, as well as for the kbd/mouse, then i might buy one for my linux desktop.

thanks!

tim

---

### Post by prashime on 2008-09-25
Look at this [www.hidpoint.com](www.hidpoint.com)

---

