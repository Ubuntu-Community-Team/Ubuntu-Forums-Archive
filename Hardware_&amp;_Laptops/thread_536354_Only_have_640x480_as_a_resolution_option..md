---
title: "Only have 640x480 as a resolution option."
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by Jason.TJ.Johnson on 2007-08-27
I've searched the forums. I know that there's dozens on threads on the same topic, but I still wasn't able to find a solution.

So here's the deal.

This is a fresh Ubuntu Feisty Fawn (7.04 - Ubuntu Ultimate) installation (dual booting with WinXP if it matters)

It's an older computer. Specifically a Sony Vaio PCV-RX260DS.

The video card is the onboard vga adapter, but I have no idea what chipset it uses.

I've tried adding the resolutions to my xorg.conf file and restarted x. Still only that one resolution is available.

I've tried the 915resolution application. Still no luck.

I've tried installing envy, but envy said my card wasn't supported.

I've checked the IRC channel. The only suggestion I got was to remove any resolution higher than 1024*768 and removing the sync lines and restarting x. That yielded no results either.

I don't know what else to do.
Oh, and on a side note, the xorg.conf lists this video card as generic...

Help PLEASE!

--
P.S. This isn't my computer, I'm trying to get him into Ubuntu and he likes it so far but we need to get over this hurdle.

---

### Post by stinger30au on 2007-08-27
this will help

[http://ubuntuforums.org/showthread.php?t=504059&page=2](http://ubuntuforums.org/showthread.php?t=504059&page=2)


inparticular, this little bit

---------------------------------------------------------------------------------------------------------------------------
If your monitor is giving you a hard time and not showing the right resolutions this little trick may fix it
sudo nano /etc/X11/xorg.conf
scroll down using the arrow keys till you find this section
Section "Monitor"
at the bottom of this section add these two lines

HorizSync 30-110
VertRefresh 50-70

now quit and save and restart. with a bit of luck, should be all good!
---------------------------------------------------------------------------------------------------------------------------

---

### Post by Jason.TJ.Johnson on 2007-08-27
:(
Didn't work.

---

### Post by ddrichardson on 2007-08-27
Oh dear - we might have to try a manual xorg.conf. Haven't done that in a while. Can you find out the model number of your monitor? If you still have the manual - we need the horizontal and vertical refresh rates.

It's on board card is an Intel 810.

---

### Post by Jason.TJ.Johnson on 2007-08-27
Looking into that right now. Give me just a second please.

---

### Post by Jason.TJ.Johnson on 2007-08-27
It's a Dell 1703FP

---

### Post by ddrichardson on 2007-08-27
OK:

Horizontal scan range      31 kHz to 80 kHz (automatic)              Vertical scan range      56 Hz to 76 Hz (automatic)

---

### Post by ddrichardson on 2007-08-27
First off create a skeleton xorg.conf and test it```

Xorg -configure
Xorg -config xorg.conf.new
```
If successful you'll get a grey screen, CTRL+ALT+Backspace out of it. If no let me know the output.

---

### Post by glotz on 2007-08-27
How about simple ```
sudo dpkg -reconfigure xserver-xorg
```

---

### Post by Jason.TJ.Johnson on 2007-08-27
Ok, I'll try that now, let me reboot into Linux

---

### Post by ddrichardson on 2007-08-27
> **glotz said:**
> How about simple ```
sudo dpkg -reconfigure xserver-xorg
```

Xorg is only configuring the one modeline though. Didn't check the link he posted - I thought it was the canned response about reconfiguring X.

---

### Post by glotz on 2007-08-27
I'm no expert on the subject at all. I just took a cheap shot. :)

---

### Post by Jason.TJ.Johnson on 2007-08-27
> **glotz said:**
> How about simple ```
sudo dpkg -reconfigure xserver-xorg
```

Tried that already, didn't work either.

Also
```

spcmn012@ubuntu-install:~$ Xorg -configure

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

spcmn012@ubuntu-install:~$ Xorg -config xorg.conf.new

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

spcmn012@ubuntu-install:~$ 

```
So I'm assuming I shouldn't be in X when attempting this...
I'll try it that way.

---

### Post by ddrichardson on 2007-08-27
Yes you need to not be in X

---

### Post by ddrichardson on 2007-08-27
To pre-empt your next question:CTRL+ALT+F2, login and ```
sudo /etc/init.d/gdm stop
```

---

### Post by Jason.TJ.Johnson on 2007-08-27
Ok, I'll type what seems important (since I can't copy and paste)

What I did was I rebooted into recovery mode (in order to avoid loading x)
Anyway, I did

sudo Xorg -configure

and it said it was sucessful

I then did

sudo Xorg -config xorg.conf.new

And it flashed and returned this:
(EE) I810(0): Given bpp (32) is not supported by i810 driver
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


And it throws me back to the prompt

---

### Post by ddrichardson on 2007-08-27
Yep fine, next alter the monitor entry:```

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync    31-80
        VertRefresh  56-76
EndSection
```

Next change the screens section:```

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 16
        SubSection "Display"
                Viewport  0 0
                Depth     16
                Modes     "1024x768"
        EndSubSection
EndSection
```

Obviously Card0 must agree with whatever name your card was detected with in Xorg.

---

### Post by Jason.TJ.Johnson on 2007-08-27
Ok, I did that
One thing to mention
I left the Device field to "Generic Video Card" because I wasn't sure what you meant
Is that fine?

---

### Post by ddrichardson on 2007-08-27
Yes that's fine. Now try running it with```
sudo Xorg -config xorg.conf.new
``` If it fails then you can use xorgcfg to alter any parameters.

---

### Post by Jason.TJ.Johnson on 2007-08-27
Ok, so I ran that line and got the same error as before
I then ran "xorgcfg" and got a "command not found"

---

### Post by ddrichardson on 2007-08-27
The error should say 16bpp where it said 32 before, the xorgcfg util may not be in Ubuntu.

---

### Post by Jason.TJ.Johnson on 2007-08-27
Ok so I double-checked the error and it does say 32.
I reopened te xorg.conf file and it only has 16 as the default depth and as the depth

I opened xorg.conf.new and the file is empty (contains nothing at all)

if I run "startx" I get

```

Data incomplete in file /etc/X11/xorg.conf
               Undefined Screen "Default Screen" referenced by ServerLayout "Default Layout".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Faal server error:
no screens found
X10: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

```

Sorry if there's any errors, all typed by hand

Did I do something wrong with the config file?

---

### Post by ddrichardson on 2007-08-27
startx wont work - we've only created a local xorg.conf

---

### Post by Jason.TJ.Johnson on 2007-08-27
Ok so what do I do at this point? I double and triple checked, I don't even have the numbers "32" in my xorg.conf.new file and I'm still getting "Given bpp )32) is not supported by i810 driver"

Any ideas?

---

### Post by ddrichardson on 2007-08-27
move the old one:```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then post the output of```
Xorg -config xorg.conf.new
```

---

### Post by Jason.TJ.Johnson on 2007-08-27
Ok, I started X so I can copy and paste the xorg.conf.new
Please hold...

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "glx"
	Load  "record"
	Load  "xtrap"
	Load  "extmod"
	Load  "GLcore"
	Load  "dri"
	Load  "dbe"
	Load  "type1"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"	
	Identifier   "Monitor0"
	VendorName   "DEL"
	ModelName    "DELL 1703FP"
 ### Comment all HorizSync and VertRefresh values to use DDC:
	HorizSync    31.0 - 80.0
	VertRefresh  56.0 - 76.0
 ###	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "i810"
	VendorName  "Intel Corporation"
	BoardName   "82810E DC-133 CGC [Chipset Graphics Controller]"
	BusID       "PCI:0:1:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes "1024x768"
	EndSubSection
EndSection

```

Now I will kill X and move the old file....

---

### Post by Jason.TJ.Johnson on 2007-08-27
Ok, I killed X, renamed the old file to xorg.conf.working (because I have a couple of backups)

So what do I do now?

---

### Post by ddrichardson on 2007-08-27
Xorg -config xorg.conf.new

---

### Post by Jason.TJ.Johnson on 2007-08-27
same 32bpp error

---

### Post by ddrichardson on 2007-08-27
I'm at a loss - there is no 32 bpp mode defined yet, only a 16 bpp, so where it's getting that from I don't know.

Looking over the specs for the card and monitor it appears that the default mode detected is the refresh at 640x480. I think we may need a defined modeline, I've got the specs so will have a look into it further in the morning - its getting a bit late for an old fa** like me.

---

### Post by nicarley on 2007-08-27
Thanks for the help.  I have a Dell M728p Monitor. I had the same problem described, went to Dell's website and found the horizontal and vertical sync rates and plugged them into my Xorg.conf and all worked!!  Thanks!

---

### Post by Jason.TJ.Johnson on 2007-08-27
Note that the post above isn't mine, so I'm still having this issue.
Nicarley, could you post you xorg.conf please?

Thanks for all your helpddrichardson. I had to go home also, I'm going to see if I can VNC in and do it from here, if not then I'll try again probably tomorrow.

---

