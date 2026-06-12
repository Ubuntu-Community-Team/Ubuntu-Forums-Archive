---
title: "Can't increase monitor refresh rate"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by Gesu` on 2007-02-14
Hi all.
I recently installed Ubuntu 6.10 (Edgy), on my new pc, but I can't change the monitor refresh rate. I read [the tutorial](http://ubuntuforums.org/showthread.php?t=83973) and searched for an answer in old posts, but I could not find anything. Probably the solution is really stupid but, alas, I have not been able to find it, yet.
My monitor is a 17'' CRT (BenQ V772) and my video card an ATI X1300. I work with a resolution of 1024*768@85Hz, but under Linux I have only 59Hz. I found the specifics of my monitor online and I changed HorizSync and VertRefresh, but nothing. So I added a custom modeline but still nothing. Finally, I used the command *dpkg-reconfigure xserver-xorg*, but nothing again. At this point I've really no clue of what else I could do.
Some idea?

Here the costum modeline I added:
```

 # V-freq: 85.00 Hz  // h-freq: 68.79 KHz
 Modeline "1024x768" 97.41  1024 1072 1192 1416   768  768  771  809 

```

And here is my actual xorg.conf:
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI X1300"
	Driver		"vesa"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"BenQ V772"
	Option		"DPMS"
	HorizSync	30-72
	VertRefresh	50-120
	# V-freq: 85.00 Hz  // h-freq: 68.79 KHz
	Modeline "1024x768" 97.41  1024 1072 1192 1416   768  768  771  809 
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI X1300"
	Monitor		"BenQ V772"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I really hope that this can be fixed, since I can't use Ubuntu otherwise...

Thank you in advance.

---

### Post by renzokuken on 2007-02-14
you could try this........but backup first

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

then

```
sudo gedit /etc/X11/xorg.conf
```
and change the screen section to look like this

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI X1300"
	Monitor		"BenQ V772"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768[color=red]_85[/color]" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768[color=red]_85[/color]" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768[color=red]_85[/color]" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768[color=red]_85[/color]" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768[color=red]_85[/color]" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768[color=red]_85[/color]" "800x600" "640x480"
	EndSubSection
EndSection

```

Ctrl+Alt+Backspace to restart X

---

### Post by ali780 on 2007-02-14
<hi
<I did every thing that you said, but <i could not save on xorg again.
what shall I do? My monitor has a  horrible vibration. Plesae help me as soon as you can
Thanks

---

### Post by mgmiller on 2007-02-14
Make sure you run gedit as sudo, as the previous poster said, otherwise you won't be able to save the xorg file.

Also, in your custom mode line, the vertical and horizontal sync line started with a "#".  This comments out that line so it does not run.  Try removing the "#". and restarting x.

Good luck

---

### Post by ali780 on 2007-02-14
<i am very bigginer in ubuntu how can I use sudo?

---

### Post by mgmiller on 2007-02-14
First, open a terminal by clicking on Applications>Accessories>Terminal.
Then, as the previous poster said enter the following command in a terminal to back up your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

When it asks for a password, use the same one you use to log onto your system.

Next enter the following command to allow you to edit the file:
```
sudo gedit /etc/X11/xorg.conf
```

Make the changes you want and click save.  You will need to restart x to make the changes take effect, so first, log off and then hit the key combination ctrl/alt/backspace.  (enter the keys the same way as you would do a ctrl/alt/del in windows).

A quick way to get the commands above from this post to your open terminal window is the use the left mouse button to highlight the command from the post and then place the cursor over the terminal window and click the middle mouse button.  Or you can use the same ctrl/c ctrl/v as the windows world uses.

---

### Post by Gesu` on 2007-02-14
Thank you for your kind answers, unfortunately none of the above suggestions worked.
I changed "1024x768" to "1024x768_85" but all I got was that resolution went to 800*600 (always with a low refresh rate).
Uncommenting that modeline line instead crashed xserver (it's really a comment, I suppose...).

So the problem still remains, refresh is always very low...

---

### Post by mgmiller on 2007-02-14
Try rerunning your hardware detect and answer the questions about refresh rates you want for your monitor.  Anything you don't know the answer to, just hit enter or tab/enter to go to the next question. When you do this, there will be 3 choices for the level of details the questions will be.  Use the middle choice.


**I suggest you print out these instructions as you will lose your graphical display for a bit while you are doing this.**

First, log off.  You should now be at the log on screen.
Next use the following key commands (all 3 keys at the same time) ctrl/alt/F1  (that's the F1 key on the top row of your keyboard.

This will put you into a command line terminal mode.
Next, enter the following command:
```
sudo /etc/init.d/gdm stop
```

I assume you are using Ubuntu, not Kubuntu.  If you are using Kubuntu, the command would be:
```
sudo /etc/init.d/kdm stop
```

When it asks for a password, use your regular log on password.

You should see a message echoed back to the terminal that gdm (or kdm) has been stopped.

Next, you will run the xorg reconfigure by typing:
```
sudo dpkg-reconfigure xserver-xorg
```

Remember, use the defaults for anything you are not sure of, when you get to the monitor/refresh rate parts, enter an x in all the modes you want to appear.  It should give you a nice list of resolutions and refresh rates.  **Make sure you only put an x by the choices you know are supported by both your graphics card and monitor.**

Just keep going till it dumps you back on the command line.

Finally, enter the following code to get back to graphical mode:
```
sudo /etc/init.d/gdm start
```

Or, if you are in Kubuntu:
```
sudo /etc/init.d/kdm start
```

If it won't restart, try typing:
```
startx
```

Or if need be reboot the machine:
```
sudo reboot
```

You should now have all the resolutions and refresh rates you want.  Access them at System>Preferences>Screen Resolution.

Hope this helps.

---

### Post by ali780 on 2007-02-14
thanks for fast reply
<I did.  Refresh rate fixed but the resolution has changed to 800 X 600. How can I fix this?
Thanks again

---

### Post by mgmiller on 2007-02-14
Did you look in System>Preferences>Screen Resolution.  What choices are listed there?  When you did the xorg reconfigure, did you put an x in the boxes next to higher resolutions than 800 x 600?  Are the resolutions you want showing up in /etc/X11/xorg.conf in the monitor section?

---

### Post by ali780 on 2007-02-14
My Screen section is below Is it OK?

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768_85" "1024x768_85" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768_85" "1024x768_85" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768_85" "1024x768_85" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768_85" "1024x768_85" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768_85" "1024x768_85" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768_85" "1024x768_85" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

---

### Post by ali780 on 2007-02-14
also in Resolution panel I can see just 640x480 and 800x600

---

### Post by mgmiller on 2007-02-14
I wonder why on all the mode lines  "1024x768_85" is entered twice?
Other than that, it looks ok.  try editing out one instance of "1024x768_85" from each line: 
```
sudo gedit /etc/X11/xorg.conf
```
Save the file and exit gedit.

Then, restart x by logging off and hitting ctrl/alt/backspace.

The drop down list at the Screen Resolution control panel only shows 800x600?

---

### Post by mgmiller on 2007-02-14
You can also try removing the _85 from the 1024x768 modes as well.  There should only be 1 instance of the resolution on each mode line.

---

### Post by Gesu` on 2007-02-14
> **mgmiller said:**
> Try rerunning your hardware detect and answer the questions about refresh rates you want for your monitor.  Anything you don't know the answer to, just hit enter or tab/enter to go to the next question. When you do this, there will be 3 choices for the level of details the questions will be.  Use the middle choice.
 
Thank you, mg but I already tried that and it did not work. I re-tried but still no luck. When I arrive to choose the resolution and the refresh there's no 1024*768@85Hz, only 1024*768@75Hz, and even if I choose that option, nothing changes. And under *System | Preferences | Screen Resolution* I already have 1024*768@85Hz, but obviously it's incorrect, and I can't change it. I tried also to choose the expert option, during the hardware detect, using the right ranges, but still nothing.
It's like Gnome thought that the resolution is already at 85Hz, even if it is not...

---

### Post by mgmiller on 2007-02-14
Now I'm confused.  You have 1024x768 as an available option in the screen resolution drop down box, and if you select it at a refresh rate of 85 Hz in the refresh rate drop down, what happens?

---

### Post by mgmiller on 2007-02-14
The other thing I am wondering about is that the choice for 1024x768 @ 85 hz was not a choice in the xorg reconfigure.  It makes me think this is not a supported combination for the driver/video card you are using.  What is your video card and which driver are you using for it?

---

### Post by Gesu` on 2007-02-14
I can't choose 85Hz in the dropdown menu because it's already selected and it can't be changed. I can choose other resolutions but, still, refresh is low.
 
My video card is a Sapphire Ati 1300x, it's a fresh new Ubuntu installation so I'm using the default drivers which come with Edgy release.
 
 
 (Curious, when I stopped gdm, in the console spaces where replaced by dots, not very good to see but at least readable. Instead if I use Ctrl+Alt+F*n* everything is fine...)

---

### Post by mgmiller on 2007-02-14
When you say "refresh is low"  even though 85 hz is selected, what exactly are you seeing on screen?  Is it flicker, or do you find the video response to be slow or laggy?  The default driver is usually the ati driver, which has pretty good accleration built in, but sometimes you get better results using fglrx.  Try installing easy ubuntu or automatix2 and look for the accerated drivers for ATI cards.  The other possibility is that ATI cards sometimes have known issues with Linux/Ubuntu.  I do have one system running Edgy with an ATI 9600 card in it, but it took a lot of tweaking to get it to work correctly.  You would probably have a much easier time getting an Nvidia card to work properly.   Sad to say, this about taps out my knowledge base for this kind of stuff.  Try searching the Ubuntu forums using ati as the search parameter and follow up with them.

Good Luck.

---

### Post by deaster2 on 2007-02-14
> **mgmiller said:**
> First, open a terminal by clicking on Applications>Accessories>Terminal.
Then, as the previous poster said enter the following command in a terminal to back up your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

When it asks for a password, use the same one you use to log onto your system.

Next enter the following command to allow you to edit the file:
```
sudo gedit /etc/X11/xorg.conf
```

Make the changes you want and click save.  You will need to restart x to make the changes take effect, so first, log off and then hit the key combination ctrl/alt/backspace.  (enter the keys the same way as you would do a ctrl/alt/del in windows).

A quick way to get the commands above from this post to your open terminal window is the use the left mouse button to highlight the command from the post and then place the cursor over the terminal window and click the middle mouse button.  Or you can use the same ctrl/c ctrl/v as the windows world uses.

Many thanks for these instructions...
They fixed my monitor "shaking" (went from 60hz to 75hz refresh rate).

---

### Post by mgmiller on 2007-02-14
Glad I could help.

---

### Post by ali780 on 2007-02-15
Thank you everybody
My problem is fixed now

---

### Post by Gesu` on 2007-02-15
> **mgmiller said:**
> When you say "refresh is low"  even though 85 hz is selected, what exactly are you seeing on screen?  Is it flicker, or do you find the video response to be slow or laggy? 
 
 
It flickers.
 
 
> The default driver is usually the ati driver, which has pretty good accleration built in, but sometimes you get better results using fglrx.  Try installing easy ubuntu or automatix2 and look for the accerated drivers for ATI cards.  The other possibility is that ATI cards sometimes have known issues with Linux/Ubuntu. 
 
 
 
Yeah, I went to launchpad and found out that my video card has [some problem]("https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/68075") with Linux, basically there's no support still, since the driver are closed source and none has reversed-engineered them. So I've to use proprietary drivers, until someone is able to write a decent open source one... This sucks, and that's probably the last time that I buy an ATI video card...
 
 
Thank you again for all your help :-)

---

### Post by renzokuken on 2007-02-15
the fglrx driver should work fine.....it is a driver released by ATI themselves specially for linux.

---

