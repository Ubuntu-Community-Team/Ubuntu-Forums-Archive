---
title: "Configuring A Wacom Tablet In Lucid Lynx (i.e., Area)"
date: 2010-04-25
forum: Hardware
---

### Post by partymetroid on 2010-04-25
Hello all.  I am running Ubuntu 10.04 Lucid Lynx.  I want to use Ubuntu as my main operating system; however, I cannot figure out how to match my tablet's (Wacom Intuos3 6x8 ) working area to match my monitor's aspect ratio (19:10, 1920x1200).  Obviously, the tablet's aspect ratio is 4:3.  I want to cut some of the top and/or bottom off digitally so that the area is of an aspect ratio of 19:10.

I have tried editing the HAL fdi policy for Wacom tablets; however, it is not available.  I suppose this is because HAL was removed from the Ubuntu boot process?

Any help would be greatly appreciate. :)

---

### Post by Fir3chi3f on 2010-04-25
Good to see artists using ubuntu. Don_Dragon is asking about the Wacom as well, there might be something in his thread that can help
[http://ubuntuforums.org/showthread.php?t=1461978](http://ubuntuforums.org/showthread.php?t=1461978)

Another thread of interest from a quick google:
[http://ubuntuforums.org/showthread.php?t=1383752](http://ubuntuforums.org/showthread.php?t=1383752)

---

### Post by partymetroid on 2010-04-25
Neither of those threads contained enough information. :(

I figured out that I need to edit /usr/lib/X11/xorg.conf.d/10-wacom.conf... but I don't know *how* to edit; or, that is to say, what to put in it for my particular configuration.

Here's what it currently says:

```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection
```

---

### Post by partymetroid on 2010-04-25
Alright, after a thorough digging-around, I found that the file that (apparently) needs to be changed is /lib/udev/rules.d/69-xserver-xorg-input-wacom.rules.  That appears to be the extent of my knowledge with the problem.

I also found out that the xorg.conf file option is
```
Option "KeepShape" "on"
```With this information provided, could anyone please help me to "Keep" the "Shape" of the tablet to match the shape of my 16:10 monitor? :D

Thanks! :)

---

### Post by Favux on 2010-04-25
Hi partymetroid,

Usually folks want to map the tablet aspect onto the screen, not the other way around.  That way they don't lose any active area on their tablets.  I don't know if cutting off active area on the tablet is doable.

Not real familiar with xorg.conf.d "snippets" yet.  I believe it's executed after xorg.conf so you could put changes in either.

So I think it should look something like:
```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "KeepShape" "on"
EndSection
```
As per the [HOWTO at LWP]("http://linuxwacom.sourceforge.net/index.php/howto/inputdev").  You might have to play with bottom X and Y too.  Be sure to back up the file(s) before editing them.

---

### Post by partymetroid on 2010-04-25
> **Favux said:**
> Hi partymetroid,

Usually folks want to map the tablet aspect onto the screen, not the other way around.  That way they don't lose any active area on their tablets.  I don't know if cutting off active area on the tablet is doable.

Not real familiar with xorg.conf.d "snippets" yet.  I believe it's executed after xorg.conf so you could put changes in either.

So I think it should look something like:
```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "KeepShape" "on"
EndSection
```As per the [HOWTO at LWP]("http://linuxwacom.sourceforge.net/index.php/howto/inputdev").  You might have to play with bottom X and Y too.  Be sure to back up the file(s) before editing them.
That worked! :D  Thanks!!!

---

### Post by Favux on 2010-04-25
Great!  Glad you're setup.

---

### Post by Don_Dragon on 2010-04-28
I'm sorry but, where exactly did you add that code to?  I'm still having trouble setting up my own tablet to map it to only one screen.  So far I've only managed to write code that does nothing, or to destroy xorg.conf, requiring me to reinstall my Nvidia drivers.

---

### Post by Favux on 2010-04-28
Hi Don_Dragon,

It's the new 10-wacom.conf in /usr/lib/X11/xorg.conf.d.  That's executed after xorg.conf.  It's now the "preferred" method althouugh you can still use xorg.conf if you want to.  You're probably breaking it by not putting in the "ServerLayout" correctly.  To edit 10-wacom.conf you can use:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
For a little more info. see c) in Section 2) at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by Don_Dragon on 2010-04-29
Wow, that threw me for one hell of a loop.  I added the following lines of code to Xorg.conf.d/10-wacom.conf

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  # USB ONLY
  Option        "Twinview"      "horizontal"
  Option        "ScreenNo"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  # USB ONLY
  Option        "Twinview"      "horizontal"
  Option        "ScreenNo"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "cursor"
  Option        "USB"           "on"                  # USB ONLY
  Option        "Twinview"      "horizontal"
  Option        "ScreenNo"      "0"
EndSection

# This section is for Intuos3, CintiqV5, Graphire4, or Bamboo without touch
Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection
```

Turns out, it broke X.  I tried restoring it, failed.  I tried moving xorg.conf.d, and it broke both mouse and keyboard functions.  I ended up using the VI editor in bash to take out the extra code, and BAM, Xorg is back in business.  This isn't the first time WACOM code has messed up my Xorg.  Why is this code so damn destructive?  All I want to do is restrict the wacom to one screen using the ScreenNo option.  What am I doing wrong?

---

### Post by Favux on 2010-04-29
Hi Don_Dragon,

Well unfortunately sometimes we have to break things to learn.  :(

With the caveat that the 10-wacom.conf and xorg.conf.d are still very new and I am not 100% on the syntax:

Those are three full xorg.conf sections and the syntax is a little different in xorg.conf.d.  So I'm not too surprised that broke X.  But as near as I can tell the options are the same.

So in 10-wacom.conf you'll see 3 sections, the wacom usb, the wacom serial, and the N-trig.  We want the wacom usb, correct?  So add the options to that section or snippet.  I think it would look like:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Twinview" "horizontal"
	Option "ScreenNo" "0"
EndSection
```
If you want to go the xorg.conf route I need to see your current, working xorg.conf.

---

### Post by Don_Dragon on 2010-04-29
Alas, I've kept hacking at it, but either the wacom stops working, or I simply don't see any change.  Unless something else comes up, I guess we may as well try the xorg.conf route.  My current set up is as follows.

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Favux on 2010-04-29
OK, could you tell me what Wacom tablet you have?  Also what devices does it have?

Stylus; stylus buttons, how many?; eraser; cursor (the Wacom tablet mouse); pad (buttons on the tablet).

Your current xorg.conf has some sections Lucid doesn't need.  Are you sure you use Xinerama in "ServerLayout"?  Did you configure the video setup through the Nvidia control panel?

---

### Post by Don_Dragon on 2010-04-30
I'm using a USB 6X8 intuos 3 with two finger pads and 8 buttons.  Standard Stylus has 2 buttons.  It also has an eraser, which never worked in Ubuntu until 10.04.

Technically, I use Twinview, configured from the Nvidia panel, but I did try out a few configurations, including Xinerama.


Thanks for the help BTW.  Every time I switch to a new version of Ubuntu, I always have a few bugs to squash.  Networking, unknown monitor, etc.  I usually find my way by learning from other people's struggles with similar bugs, but this time, I seem to be among the early birds facing this problem.

---

### Post by Favux on 2010-04-30
Hi Don_Dragon,

You're welcome.  Hope we get this working.
> I seem to be among the early birds facing this problem. 
Yep, looks like.
 
Ok, an Intous3.  I found and brushed the dust off my old sample Intuos3 xorg.conf.  Made some minor modifications for Lucid and incorporated it into yours.  Also added the screen localization lines.

My guess is that the "0" in:
```
    Option         "Xinerama" "0"
```
is Boolean for off, so maybe we should comment that line out in "ServerLayout", i.e.:
```
#    Option         "Xinerama" "0"
```

Remember to back up your current working xorg.conf and be prepared to restore the back up from the command line as this might break X.

---

### Post by Don_Dragon on 2010-05-01
Well, the good news is that nothing broke beyond a quick repair or two.  The bad news is that things are really not working out as planned.  No matter what options I mess with, the Wacom seems almost insensitive to change when it comes to monitors (I even changed twinview to vertical for kicks, to no visible effect)

One interesting discovery is that when I switch the ScreenNo to "1", and reboot, the wacom's cursor appears at the very edge of my second monitor, stuck there, as if setting it to zero somehow encompasses both screens, perhaps causing the problem in the first place.

According to the Nvidia settings, both screens are set up as Screen number 0, but are set as display DFP-1, and DFP-0

I've tried renaming the second monitor as 1 in xorg.conf, and succeeded in doing little more then breaking xorg.

Perhaps there is some way of differentiating the monitors?

---

### Post by capraMambrica on 2010-05-02
Hey Guys, I thought I'd just jump in this thread and mention that I have managed to change the button order of a wacom pen; switching the right-click and middle-click around.

First getting:
```
$ xsetwacom list
Wacom Intuos3 6x8 eraser ERASER    
Wacom Intuos3 6x8 cursor CURSOR    
Wacom Intuos3 6x8 pad PAD       
Wacom Intuos3 6x8 STYLUS
```Then:```

$ xsetwacom set "Wacom Intuos3 6x8" Button3 2
$ xsetwacom set "Wacom Intuos3 6x8" Button2 3
```Of course, this will all reset when you reboot ubuntu. It's worth automating these lines at startup.

I'm just posting here because this is one of the more popular threads about configuring wacoms in lynx, thanks to the title no doubt, and it took me ages to search for enough information to work this out.

---

### Post by Don_Dragon on 2010-05-04
Interesting.  I had stumbled across the command line route, but hadn't really considered automating it as a workaround.  I have to admit I wouldn't know if it could solve my problem, as its now become clear that  under Twinview both screens are currently recognized as being screen 0, making it nearly impossible to separate them, no matter the place I insert code, or commands.  Anyone have any idea on how to separate them?

Here's my current xorg.conf

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by JanMalte on 2010-05-05
After plugging the tablet and reboot it works out of the box. Only the keys making some trouble. They always set the pointer to the upper left corner of the screen. Running several xsetwacom commands i changed the buttons to my need. Only the "touch ring" wont work. I can set it to every core key but it don't work. I just want to have it as a normal scroll wheel. So does anyone has the right settings for me?
```
janmalte@desktop:~$ xinput --list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; CHESEN PS2 to USB Converter               id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 6x9 eraser                  id=10   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 6x9 cursor                  id=11   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 6x9 pad                     id=12   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 6x9                         id=13   [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation          id=14   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; CHESEN PS2 to USB Converter               id=8    [slave  keyboard (3)]

janmalte@desktop:~$ xsetwacom --list 
Wacom Intuos4 6x9 eraser ERASER    
Wacom Intuos4 6x9 cursor CURSOR    
Wacom Intuos4 6x9 pad PAD       
Wacom Intuos4 6x9 STYLUS
```
This one don't work as expected:```
janmalte@desktop:~$ xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWDn "+ "
janmalte@desktop:~$ xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWUp "- "

```

---

### Post by Don_Dragon on 2010-05-06
I've been offered a nifty little workaround on my other thread.  For now, its solved my problem.

[http://ubuntuforums.org/showthread.php?t=1461978](http://ubuntuforums.org/showthread.php?t=1461978)

---

### Post by Sawer on 2010-08-20
I hope this is the right place to post this.
My Wacom Bamboo Fun CTE-450 worked out of the box. The only thing I don't  understand is how to  get the 4 key function and the scroll ring to work.
Any help would be appreciated.
Thanks

---

### Post by Favux on 2010-08-20
Hi Sawer,

Scroll wheel and strips just got added to xf86-input-wacom.  So you may need to update it along with the wacom.ko.  Then you'll need an xsetwacom script.  I don't have one for the old Bamboos yet, but should be easy.  For updating and sample .xsetwacom.sh's see the [Bamboo P&T]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

### Post by Jammet2 on 2010-11-08
Oh dear. My USB Bamboo CTH 640 used to work, I think, for several months, a year ago, and I had help getting this far. Now I'm in need of it again, but I have to admit that I pretty much forgot everything about how I got it to work.

And now I am looking at this incredible wall of text. The **mini** how-to is so big, and even that still seems to try and explain everything it does, along the way, or describe what will happen, I'm completely demotivated just looking at it. My own fault, I guess. Maybe I'm a little spoiled, but I am desperately looking for "Just make it work right now!"-Button. I would've thought a disto like Ubuntu would've arrived there, by now. :) Guess I was wrong.

My sincere apologies. Normally I'm quite adept with bash, compiling, and fiddling around with technical issues, but looking at this, -again-, I can't even force myself to. It's just too much right now. I'll check back in a couple of weeks if I can muster up the willpower to do all this ... again. :)

Again, I'm sorry. Don't think of this as complaining, please. I admire your hard work and the help and support you have given.

PS: Strike that. All good. :) Thank you, Favux!

---

### Post by smws on 2010-12-27
I've been happy that my older serial Wacom ArtzII tablet works with various versions of Ubuntu (tweaking neccesary). So, hopefully somebody can give me some insight on getting it to work with 10.04 Lucid. Here is the story:

In Karmic, I had the tablet/stylus/eraser working through a Keyspan serial->USB adapter, and the following lines in my xorg.conf:
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/ttyUSB0"
	Option		"Type"		"stylus"
	Option          "USB"           "on"                  #USB ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/ttyUSB0"
	Option		"Type"		"eraser"
	Option          "USB"           "on"                  #USB ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/ttyUSB0"
	Option		"Type"		"cursor"
	Option          "USB"           "on"                  #USB ONLY
EndSection
```
and in the server layout section:
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

Since I've upgraded, the new xorg.conf written by the update manager reads, for those sections:
```
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/ttyUSB0"
#	Option		"Type"		"stylus"
#	Option          "USB"           "on"                  #USB ONLY
#EndSection
```
and so on for the rest of the wacom devices, and at the end
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#	InputDevice	"Generic Keyboard"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#	InputDevice	"Configured Mouse"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#	InputDevice     "stylus"	"SendCoreEvents"
# commented out by update-manager, HAL is now used and auto-detects devices
...<etc>...
EndSection
```

So, I read around, and tried updating [FONT="Fixedsys"]/usr/lib/X11/xorg.conf.d/10-wacom.conf[/FONT] but the format seems different and I'm having no luck. I tried changing ```
MatchDevicePath "/dev/input/event*"
```
to
```
MatchDevicePath "/dev/ttyUSB0"
```
but, no luck.

I've also tried using the old xorg.conf; it didn't help.

FWIW, I can still see the tablet responding through wacdump (why was wacom-tools removed as a package? grrr.).

Thanks in advance!

---

### Post by Favux on 2010-12-27
Hi smws,

Starting with Lucid (10.04) Xorg took over the Wacom X driver wacom_drv.so for X servers 1.7 (the Lucid version) and up.  The Xorg version is called xf86-input-wacom.  They dropped wacdump, xidump, and wacomcpl and rewrote xsetwacom.  Also serial tablet (but not serial tablet pc) support was dropped.  Serial tablets were dropped due to lack of developer resources, not policy.

Some coders came up with a couple of patches to restore serial tablets to xf86-input-wacom.  The second set seems pretty good.  Unfortunately the patches only work on xf86-input-wacom 0.10.5 (the Lucid default) and 0.10.6.  So you would want to download the 0.10.6 tar.  Apply the patches and then compile it.

See the near the top of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") "Notice for Serial Graphics Tablet Users" for a brief discussion and links.

Your xorg.conf should be good unless you don't have a Wacom tablet mouse.  In that case you could remove the cursor section and the cursor line in "ServerLayout".  We could try setting up through 10-wacom.conf if you wanted.

---

### Post by smws on 2010-12-28
Hello, Favux! Thanks for your quick reply.

I am sorry to hear about dropping support for that stuff, but I completely understand the kinds of priorities that drive decisions like that. Perhaps the community can eventually fill in support.

I had often wondered about the "cursor" section in xorg. I removed it as you suggested.

With the help of a programmer (which I am not) I was able to download source for xf86-input-wacom-0.10.5, apply the patches, and rebuild the package (a process I am documenting for any that follow, should I succeed) but it didn't work. I think the errors I am getting are new errors, however, so that's good. I will list them here, in case people have any ideas. From "less /var/log/Xorg.0.log":
```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
dlopen: /usr/lib/xorg/modules/input/wacom_drv.so: undefined symbol: gWacomSerialDevice
(EE) Failed to load /usr/lib/xorg/modules/input/wacom_drv.so
(II) UnloadModule: "wacom"
(EE) Failed to load module "wacom" (loader failed, 7)
```

and the same several more times

---

### Post by Favux on 2010-12-28
Hi smws,

Looks like you two have gotten pretty far.  Nice work.

I don't recognize that error.  I don't remember if any one else was using a serial to usb cable.  What happens if you add this option:
```
	Option          "USB"           "on"                  #USB ONLY
	Option          "ForceDevice"      "SERIAL"

```
below or instead of the usb line?

Some folks are reporting their serial tablet won't initialize unless they run wacdump briefly.  That seems to initialize it.  If they run wacdump too long it'll segfault.  Don't know why this works.  They add wacump to a start up script.

Your writing a HOW TO would be a good thing.  I've been hoping someone would.  I'll try to pull together all of the serial threads dealing with Lucid and Maverick.  There's a few more the links don't take you to.

---

### Post by smws on 2010-12-28
Hi Favux,

Thanks for your help so far. I did notice that John Tsiombikas, one of the guys who wrote the original patch, was indeed using a serial-to-USB adapter, so I'm hopeful for that reason; after all, he got his tablet to work.

After some installation of packages and wrangling with autogen, there's a new bug showing in Xorg.0.log:
```
(**) Option "Device" "/dev/ttyUSB0"
(EE) stylus: wcmDeviceTypeKeys unable to ioctl USB key bits.
```

I did try setting the USB option both ways and the ForceDevice option. Thinking of things to try next...

---

### Post by Favux on 2010-12-28
You might want to consider downloading the 0.10.6 tar and patching that.  Aso are you using the second patch set?

---

### Post by smws on 2010-12-29
So, I got it working! Yay. 12-year-old hardware support FTW.

I will have a more detailed post later, but for now I wanted to post the Keyspan USB serial driver kernel patch to add a dummy TIOCGSERIAL ioctl so that the wacom driver works. (*phew*) This is based on John Tsiombikas' PL2303 patch linked from [his post]("http://codelab.wordpress.com/2010/02/21/wacom-hacking/"). It is attached.

---

### Post by Favux on 2010-12-29
Wow!!!  Nice finds!  Congratulations.

I'm looking forward eagerly to your tutorial.

---

### Post by smws on 2010-12-29
**The Saga of Support for Wacom ArtZII/ArtZ2 Serial Tablet using a Keyspan Serial->USB Adapter under Ubuntu 10.04 "Lucid Lynx" **
In Karmic, I had the tablet/stylus/eraser working through a Keyspan serial->USB adapter (You can see details a few posts back in this thread.) When I upgraded to Lucid, it stopped working. With help from my brother the programmer, it works now.  What follows is a work in progress, and very specific; but hopefully some of it can help some of you. I have omitted a lot of dead ends, wrong edits, mistakes, and kernel panics, and whatnot.

From [this post talking about Lucid and wacom on sourceforge]("http://sourceforge.net/mailarchive/forum.php?thread_name=4BEB198B.9030809%40sleif.de&forum_name=linuxwacom-discuss"), I got [patch 1]("http://sourceforge.net/mailarchive/attachment.php?list_name=linuxwacom-discuss&message_id=4BFAD268.7010608%40sleif.de&counter=1") and [patch 2]("http://sourceforge.net/mailarchive/attachment.php?list_name=linuxwacom-discuss&message_id=4BFAD268.7010608%40sleif.de&counter=2")
Then, install a huge cluster of crap
```
sudo apt-get install debhelper xserver-xorg-dev libxi-dev quilt libtool autoconf
```
Get input driver for the tablet
```
apt-get source xserver-xorg-input-wacom
```
Apply the patches
```
cd xf86-input-wacom-0.10.5/
patch -p1 < ../0001-rename-wcmICDV4Speed-to-wcmSerialSpeed.patch 
patch -p1 < ../0002-reenable-support-for-legacy-serial-tablets.patch 
```
I had a problem here and had to appy some changes manually from the rejected hunk file
```
gedit src/xf86WacomDefs.h src/xf86WacomDefs.h.rej 

```
Regenerate makefile.am
```
bash ./autogen.sh
```
Build the wacom driver package
```
dpkg-buildpackage
```
Install the wacom driver package
```
sudo dpkg -i ../xserver-xorg-input-wacom_0.10.5-0ubuntu4_i386.deb
```
Reading John Tsiombikas' [post]("http://codelab.wordpress.com/2010/02/21/wacom-hacking/"), I realize that if I have a kernel older than linux 2.6.34, I need to patch the kernel ioctl implementation. To find my kernel version:
```
uname -r
```
I have 2.6.32, so I get his [URL="http://nuclear.dnsalias.com/tmp/pl2303-ioctl_cgserial.patch
"]PL2303patch here.[/URL]
Need to patch the kernel, so I mostly follow steps from [this howtogeeks post]("http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/")
Downloaded packages for kernel source modification
```
sudo apt-get install linux-source-2.6.32 kernel-package libncurses5-dev fakeroot
```
Dangerously become root because of all the commands I need to run
```
sudo /bin/bash
```

Here, my narrative gets lost because my brother the programmer mostly took over, and also the root shell doesn't seem to save history the same way.

Do a bunch of stuff like applying John's patch, recompiling the kernel (takes a long time), updating initrd, updating the GRUB bootloader, reboot, and... the moment of truth:

It doesn't work.

Turns out that John's patch works for his particular serial->USB adapter, and since I have a keyspan serial->USB adapter, it needs a different patch.

My brother the programmer goes in, and looking at the patch to the PL2303 driver, makes a patch for the Keyspan driver. The larger problem is that ioctl support in USB serial drivers is spotty, and there are only a few that have it; but Lucid, unlike Karmic, expects the serial devices to pass some kind of test. The patch is [here]("http://ubuntuforums.org/attachment.php?attachmentid=179620&d=1293646003").

Apply the Keyspan patch 
```
patch -p1 < /home/smws/Downloads/keyspan-ioctl_cgserial.patch.txt

```
Then do all the compiling and what not again, and add this to the device section of xorg.conf:
```
Option "ForceDevice" "SERIAL"
```
At one point I also commented out the entire /usr/lib/X11/xorg.conf.d/10-wacom.conf, with # at the start of every line, but I don't know if that was necessary or not.

That's the story so far, I'll probably streamline the process later with some edits. Many thanks to Favux, John Tsiombikas and the other kernel hackers, person at Howtogeek, and my brother the programmer, and everyone else who helped.

Hey, linux kernel module people: please add dummy TIOCGSERIAL ioctl to all the serial->USB drivers in your copious free time! Thanks. ;)

---

