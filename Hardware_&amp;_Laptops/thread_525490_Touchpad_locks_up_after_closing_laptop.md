---
title: "Touchpad locks up after closing laptop"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by jonlemur on 2007-08-14
Hello,

I'm having some issues with my touchpad.  When I close the screen of my laptop and reopen it, the touchpad stops working.  I've tried restarting the X server and logging out and back in, but the only thing that gets it back is to reboot.  Here is the excerpt from my xorg.conf.

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
	Option		"RightEdge"		"5900"
	Option 		"VertEdgeScroll"	"true"
EndSection
```

I have a few touchpad applications installed.  If it would help to know what they are, I can find out.  Any ideas?

---

### Post by jonlemur on 2007-08-22
Like a vending machine, I'm bumping this.

---

### Post by isaacj87 on 2007-08-22
Did you add these lines to this sections of the xorg.conf?

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
        **Load    "synaptics"**
EndSection

and

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
       ** InputDevice     "Synaptics Touchpad"**
EndSection

---

### Post by spier on 2007-08-22
> **jonlemur said:**
> Hello,

I'm having some issues with my touchpad.  When I close the screen of my laptop and reopen it, the touchpad stops working.

What is your ubuntu version? I`m asking because I had this issue with Edgy Eft.  It was fixed since Feisty Fawn release.

---

### Post by jonlemur on 2007-08-22
> Did you add these lines to this sections of the xorg.conf?

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
Load "synaptics"
EndSection

and

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

I just put those in, rebooted and tested it.  Unfortunately, it still does not work after I close the lid and reopen it.

> What is your ubuntu version?

I am using Feisty Fawn.  I didn't have the issue in Drake.

Thanks very much for the suggestions.

---

### Post by isaacj87 on 2007-08-22
I don't want to make any assumptions...but I hope you only added the **bold lines**! If you added* all* the lines you could screw up your laptop. I only put entire sections from *my* xorg.conf file as something you could reference to. Can I ask the model of your laptop? If it's a toshiba....I don't know if I can help you..lol

---

### Post by spier on 2007-08-22
Following isaacj87`s route, some thougths:

During my Edgy`s touchpad challenge, I commented out  synaptics load in Module section and everything related with Wacom devices, as  I still don`t know what it is:

```
Section "Module"
        # ...
        # Load  "synaptics"
EndSection
```

```
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
```

---

### Post by isaacj87 on 2007-08-22
I think everyone has though lines (probably only laptops)

I have it too...

```

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

```

Probably just defaults for computers have these devices...

and the part about "synaptics" is related to your touchpad...Did you have that by default? Because I didn't...I had to add "load synaptics."

I found lots of info here that could be helpful...

[Hardware Support Wiki]("https://wiki.ubuntu.com/HardwareSupport")

All I had to do was search for my brand and model and I got loads of helpful info and correcting hardware issues. :)

---

### Post by spier on 2007-08-22
> and the part about "synaptics" is related to your touchpad...Did you have that by default? Because I didn't...I had to add "load synaptics."

Well, I might have inserted it, but my touchpad works through suspend & hibernate cycles with the Load "synaptics" line commented out (with a dash). As for the wacom thing, if you do not have this device, better leave it commented.

---

### Post by isaacj87 on 2007-08-22
> **spier said:**
> Well, I might have inserted it, but my touchpad works through suspend & hibernate cycles with the Load "synaptics" line commented out (with a dash). **As for the wacom thing, if you do not have this device, better leave it commented.**

Is it harmful to my laptop? I don't want to damage my laptop! :(

---

### Post by spier on 2007-08-22
> **isaacj87 said:**
> Is it harmful to my laptop? I don't want to damage my laptop! :(

No that I`m aware.  If I remember what I read while in Edgy time, there was an issue with those settings (a conflict with  touchpad, maybe). Ever since I leave them commented out. While trying "softly" with these settings, you can`t get worst than a device not working properly.

---

### Post by jonlemur on 2007-08-23
> I don't want to make any assumptions...but I hope you only added the bold lines! If you added all the lines you could screw up your laptop. I only put entire sections from my xorg.conf file as something you could reference to. Can I ask the model of your laptop? If it's a toshiba....I don't know if I can help you..lol


I only added the bold lines, and the laptop is a Gateway M460.  


> I found lots of info here that could be helpful...

Hardware Support Wiki

Thanks for the site.  I checked out the [[COLOR="Orange"]_M480 page_[/COLOR]]("https://wiki.ubuntu.com/LaptopTestingTeam/GatewayM680") (they didn't have the 460, but maybe the 480 is similar?) and they seemed to have the same issue with the touchpad being unresponsive when woken up from sleep.  Is there another place on that site I can go to get tips on how to fix it?

Thanks for your help

---

### Post by isaacj87 on 2007-08-24
Is there anything else that is unresponsive? Every other thing is working right and your system isn't locking up?

I found this guy's blog about his Gateway M460 and he didn't mention about anything related to his touchpad. I'll keep digging, but you can look at his xorg.conf file that he posted. Maybe find something touchpad related that you don't have?? I wouldn't copy anything related to video card configurations because I'm not sure what driver you're using.

Anyways, here his blog and I'll keep looking. :)

[Blog with xorg.conf for M460]("http://www.cinnamonpirate.com/blog/414/")

**EDIT**: You may or may not want to scratch that idea...

I checked the Hardware Support site for other Gateways and other laptop models besides the M680 have similar problems...Unfortunately, you maybe out of luck :(
But like I said, I'll look.

---

### Post by isaacj87 on 2007-08-24
Okay...I had a look at this:

[Synaptic Bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/59867")

Another Gateway user filed a bug and at the bottom of the page there is a comment about a workaround.

The comment also states that it should be fixed for 2.6.21-rc3. Well, 2.6.22-10 is out already, so you might want to consider upgrading you kernel. It could fix your problem. Unfortunately, upgrading the kernel can go either way. For example, when I upgrading to the latest kernel my suspend stop working! But, it's something you could definitely consider.

---

