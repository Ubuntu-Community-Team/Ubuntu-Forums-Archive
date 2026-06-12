---
title: "Left Handed and Using a Wacom Bamboo"
date: 2010-05-21
forum: Hardware
---

### Post by bitterbug on 2010-05-21
Sorry if the solution is posted somewhere. I've found the question asked in another general Wacom thread but couldn't find an answer posted.

I'm a left-handed mouse user, and the Wacom bamboo assigns as left-handed as well. So touching the stylus to the tablet is equivalent to a right click, and to draw I have to hold in the button and draw on or above the tablet.

Is there a native solution in 10.4, or am I going to have to find an input mapper to do the job?

On the plus side the tablet response is silky smooth in Ubuntu. In both XP and Windows 7 it's been very jerky and frustrating.

---

### Post by Favux on 2010-05-21
Hi bitterbug,

I'm not sure I understand what you're asking.  What model Bamboo do you have?  Anyway to make it left handed you can use in a terminal:
```
xsetwacom set stylus rotate HALF
xsetwacom set eraser rotate HALF

```
Since the device naming has changed, with Lucid you need to find out what stylus and eraser are now called.  So enter in a terminal:
```
xinput --list
```
Then substitute the longer more descriptive device name in for stylus, with quotes around it, etc..

---

### Post by bitterbug on 2010-05-22
Thanks for that, it will be useful. But the rotation is not what I meant.
I will clarify the description, so that anyone looking for a solution will see that this is what they're looking for. I'll check into the above command and see if I can get the buttons to swap that way.

(The X and Y axis on the tablet have remained the same) 

--------------------------------------------------------

Issue:
When I set the mouse to being left handed it flipped the buttons on the Wacom so it performs as if the buttons on it were backward to.

Normal: ```
Drawing on the tablet with stylus = drawn image

```
New behavior: D```
rawing on tablet with stylus = acts like right click, draws nothing. 
```

Normal: ```
Clicking on stylus button in air above tablet = right click
```

New behavior: ```
Clicking on stylus button in air above tablet = draw image in mid air.
```

---

### Post by bitterbug on 2010-05-22
Thanks to Favux pointing out the commands to use, it didn't take long to find the necessary commands:

This sets the stylus tip to draw on contact with the Bamboo tablet.
```
xsetwacom set 'Wacom Bamboo' button1 1

```

This sets the rocker button nearest the tip to grabbing/panning on desktop and gimp.
```
xsetwacom set 'Wacom Bamboo' button2 2

```

And this gives the upper rocker button the right click, opening context menus:
```
xsetwacom set 'Wacom Bamboo' button3 3

```


Useful links:
[http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)
[http://www.seafriends.org.nz/linux/pen_tablet.htm](http://www.seafriends.org.nz/linux/pen_tablet.htm)
[http://www.thinkwiki.org/wiki/Wacom_Serial_Tablet_PC_Stylus](http://www.thinkwiki.org/wiki/Wacom_Serial_Tablet_PC_Stylus)

And an old forum post that I didn't find until knowing to search for 'xsetwacom'.
[http://ubuntuforums.org/archive/index.php/t-450955.html](http://ubuntuforums.org/archive/index.php/t-450955.html)

One last thing to do is to get the eraser on the stylus acting like an eraser. Then we're golden.

---

### Post by Favux on 2010-05-22
Hi bitterbug,

Looking good!  :)

For Gimp, Inkscape, etc. for eraser you need to configure the extended input devices.  See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").  Then just point the eraser end to the little eraser icon and Save.

---

### Post by Ghostlove on 2011-03-20
I've been trying to use the fix stated here but in terminal I'm getting the error:

```
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'stylus'
```

Any ideas?

---

### Post by Favux on 2011-03-20
Hi Ghostlove,

Sure.  The xsetwacom command uses the "device name" now instead of stylus or eraser or whatever.  You'd only get "stylus" nowdays using a xorg.conf.  So enter in a terminal:
```
xinput list
```
That will tell you the "device name" to substitute for *stylus*, and use the quotes.

---

### Post by Ghostlove on 2011-03-20
I did that, it gave me a device name of 'Wacom BambooPT 2FG Small Pen'. I no longer get the error when I put those lines into the terminal, but neither does it make any difference, I'm still getting the 'right click' menu when I put stylus to tablet. :( Any ideas? Thanks for trying to help!

---

### Post by Favux on 2011-03-20
Enter in a terminal:
```
xsetwacom set "Wacom BambooPT 2FG Small Pen" Button1 1
```
and see if that fixes it.  That should be the default setting for Button1 i.e. the stylus tip.  And it doesn't say stylus after Pen?  Which release of Ubuntu are you using?

---

### Post by Ghostlove on 2011-03-20
I did that, it made no difference. Interestingly (or not) the tablet works fine (with stylus at least) if I go into my mouse settings and set it to right-handed.

ETA No it doesn't say stylus. It shows two entries that could be the tablet, that one and the same but with 'Finger' instead of 'Pen'. I'm using Ubuntu 10.10.

---

### Post by Favux on 2011-03-20
It's more helpful if you actually post the *xinput list* output rather than describe it.

It seems like your button mapping isn't working and from what you describe of the device names your Wacom drivers aren't installed correctly.  That sounds like the naming nomenclature of a while ago.

I gather you have a Wacom Bamboo Pen and Touch tablet.  What's the model number on the label on the bottom of the tablet?

To get a Bamboo P & T working in Maverick you had to do something other than the default Maverick install.  What did you do?

---

### Post by Ghostlove on 2011-03-21
Okay, my ximput list is:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG Small Pen            	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG Small Finger         	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Logitech Logitech USB Keyboard          	id=9	[slave  keyboard (3)]
    &#8627; Logitech Logitech USB Keyboard          	id=10	[slave  keyboard (3)]
    &#8627; Vendor strings are placed here.   Nuforce   µDAC 	id=14	[slave  keyboard (3)]
```

The model number is CTH-461.

I tried many different ways of installing the drivers and I'm not sure which one it was that made it work. I do remember that I tried one way and it kept asking for dependencies that I couldn't find in Synaptic Package Manager.

Thanks so much! Any more ideas?

---

### Post by Favux on 2011-03-21
You are using Maverick, correct?  Let's do a simple diagnostic to find out which driver is being used:
```
xinput list-props "Wacom BambooPT 2FG Small Pen"
```

Is your CTH-461 the Bamboo Craft product ID = 0xd2 one of the 5 original models?  Or the CTH461/S (lablel on the back of the tablet) Bamboo Fun Small product ID = 0xd7, one of the 5 new models?  Enter *xinput list* in a terminal to get the product ID.

---

### Post by Ghostlove on 2011-03-21
```
Device 'Wacom BambooPT 2FG Small Pen':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (257):	0
	Device Accel Constant Deceleration (258):	1.000000
	Device Accel Adaptive Deceleration (259):	1.000000
	Device Accel Velocity Scaling (260):	10.000000
	Evdev Reopen Attempts (241):	10
	Evdev Axis Inversion (261):	0, 0
	Evdev Axis Calibration (262):	<no items>
	Evdev Axes Swap (263):	0
	Axis Labels (264):	"Abs X" (266), "Abs Y" (267), "Abs Pressure" (268), "None" (0)
	Button Labels (265):	"Button Unknown" (242), "Button Unknown" (242), "Button Unknown" (242), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130)
	Evdev Middle Button Emulation (244):	2
	Evdev Middle Button Timeout (245):	50
	Evdev Wheel Emulation (246):	0
	Evdev Wheel Emulation Axes (247):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (248):	10
	Evdev Wheel Emulation Timeout (249):	200
	Evdev Wheel Emulation Button (250):	4
	Evdev Drag Lock Buttons (251):	0
```

It's the CTH-461/S(A) apparently. *xinput list* gives me the list I gave above.

---

### Post by Favux on 2011-03-21
So you have one of the 5 new models released in October 2011.

Alright, you are on the evdev driver not the Wacom drivers.  Let's make sure the configuration file is intact.  Go to /usr/share/X11/xorg.conf.d and see if there is a file called 50-wacom.conf there.  If so post the contents.

If it is a driver problem it would help if you could tell me how you got the tablet working originally.  Did you use a PPA?  If so whose?

---

### Post by Ghostlove on 2011-03-21
50-wacom.conf is there, the contents are:

```
Section "InputClass"
        Identifier "Wacom class"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        #Option "Button2" "2"
        #Option "Button3" "3"
        Option "KeepShape" "on"
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

I really can't remember how I got the tablet working originally. I searched "Wacom Bamboo Ubuntu" and tried three or four different methods before it worked at all, but I can't remember which one it was I used last, sorry... :/

---

### Post by Favux on 2011-03-21
Oops, double post.

---

### Post by Favux on 2011-03-21
The wacom.conf looks OK, it should be doing the match and placing the tablet on the wacom X driver.  So there is likely a problem with the wacom usb driver.

If you go to the [Bamboo Pen and Touch HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") just before part I., where you compile linuxwacom, are links to two PPA's.  Do either of them look familiar?

---

### Post by Ghostlove on 2011-03-21
I don't recognise either of those, no. Should I maybe try one of them?

---

### Post by Favux on 2011-03-21
Sure.  Since you have a new model try IRIE's.  He uses input-wacom, which has the wacom.ko with the 5 new models.

The thing is if you used a method that utilized dkms (dynamic kernel module support) it might interfere with installing a new usb kernel driver (wacom.ko).  That's one of the things I was trying to find out.

---

### Post by Ghostlove on 2011-03-21
Okay, let's assume I'm not that bright. Which of those three files do I need to download, and is it standard unpack, ./configure, make, make install?

EDIT: Yes, I'm not that bright. I added that PPA to my sources list, but I can't find those packages.

---

### Post by Favux on 2011-03-21
In a terminal enter:
```
sudo add-apt-repository ppa:irie/wacom

sudo apt-get update
```
Then go to Administration > Update Manager and it should have new packages to install.  Make a note of the package(s) name(s).

---

### Post by Ghostlove on 2011-03-21
I already did that; that's what I meant by I can't find the packages. The list at Irie's PPA page shows input-wacom, wacom-source and xf86-input-wacom. None of those three is showing up in my Synaptic Package Manager package list, even when I get it to just show me the packages from Irie's PPA. When I go to the update manager nothing shows up.

I'm really sorry I'm being so rubbish, I really appreciate all your help!

---

### Post by Favux on 2011-03-21
Well what is the Synaptic Package Manager package list showing you when it shows the packages from Irie's PPA?  What are the package names in other words?

---

### Post by Ghostlove on 2011-03-21
Oh wait, I've obviously done something right! Now when I do *xinput list* it shows me:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG Small Pen stylus     	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG Small Finger touch   	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG Small Pen eraser     	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG Small Finger pad     	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Logitech Logitech USB Keyboard          	id=9	[slave  keyboard (3)]
    &#8627; Logitech Logitech USB Keyboard          	id=10	[slave  keyboard (3)]
    &#8627; Vendor strings are placed here.   Nuforce   µDAC 	id=14	[slave  keyboard (3)]
```

---

### Post by Favux on 2011-03-21
That looks correct finally!

Is it working now?

---

### Post by Ghostlove on 2011-03-21
I'm really, really sorry but no. :/ I tried doing the things at the top of this post, with my new device name, and I'm still getting a 'right click' menu upon putting stylus to tablet, and I'm still unable to rotate the tablet. :(

---

### Post by Favux on 2011-03-21
Well lets check the *list-props* and see if you are now on the wacom driver.
```
xinput list-props "Wacom BambooPT 2FG Small Pen stylus"
```
If not check the 50-wacom.conf and make sure it's still there and has its contents.

---

### Post by Ghostlove on 2011-03-21
```
Device 'Wacom BambooPT 2FG Small Pen stylus':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (257):	0
	Device Accel Constant Deceleration (258):	1.000000
	Device Accel Adaptive Deceleration (259):	1.000000
	Device Accel Velocity Scaling (260):	10.000000
	Wacom Tablet Area (273):	0, 0, 14720, 9200
	Wacom Rotation (274):	0
	Wacom Pressurecurve (275):	0, 0, 100, 100
	Wacom Serial IDs (276):	215, 0, 2, 0
	Wacom Capacity (277):	-1
	Wacom Pressure Threshold (278):	27
	Wacom Sample and Suppress (279):	2, 4
	Wacom Enable Touch (280):	0
	Wacom Hover Click (281):	0
	Wacom Enable Touch Gesture (282):	0
	Wacom Touch Gesture Parameters (283):	50, 20, 250
	Wacom Tool Type (284):	"STYLUS" (266)
	Wacom Button Actions (285):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Wacom Debug Levels (286):	0, 0
```

I can't see if that's different from before...

---

### Post by Ghostlove on 2011-03-21
50-wacom.conf now says:

```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM|Hanwang"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection
```

---

### Post by Favux on 2011-03-21
Well you are on the wacom drivers now instead of evdev so it should be working.

Why don't you try the xsetwacom configuration script attached to the bottom of the HOW TO.  Remember a bunch of parameter names have changed for xf86-input-wacom, see the HOW TO part IV. for an explanation on HOW TO install one and other details and the warning at the beginning of part II. for a link to the new names.

---

### Post by Ghostlove on 2011-03-22
I'm not sure which one to use. I know you've spent a lot of time here helping me and I really appreciate it, but would you be able to walk me through this please? I really am a beginner at this sort of thing. :/

ETA: I've found which one it is I need. How do I run it?

---

### Post by Ghostlove on 2011-03-22
A quick Google showed me how to run it. Really sorry to have asked such a silly question. I just have to figure out what to replace the device names with now. :)

---

### Post by Ghostlove on 2011-03-22
Now I'm getting:

```
Set: Value for 'ClickForce' (27) out of range (1 - 21)
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Pen stylus value for 'PressCurve'
Set: Value for 'ClickForce' (27) out of range (1 - 21)
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Pen eraser value for 'PressCurve'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger touch value for 'Suppress'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger touch value for 'RawSample'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger touch value for 'CursorProx'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger touch value for 'Button1'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger touch value for 'Button2'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger touch value for 'Button3'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger pad value for 'Button1'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger pad value for 'Button2'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger pad value for 'AbsWDn'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger pad value for 'AbsWUp'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger pad value for 'Button3'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger pad value for 'Button4'
```

---

### Post by Favux on 2011-03-22
Hi Ghostlove,

Since you used Irie's PPA you have xsetwacom 0.10.11 or 0.10.11+.  Many of the xsetwacom parameter names changed with 0.10.11 so you need to change the old parameter names to the new ones.  I give a warning and link in part II. and part IV. I think.

If you enter each *set* command individually or use the *get* command in a terminal it will tell you the new name.  Or you could look at the table at the Linux Wacom Project mediawiki:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names)

---

### Post by Ghostlove on 2011-03-22
I have changed them all but it says the new names are invalid:

```
Set: Unknown parameter 'PressureCurve'
Set: Unknown parameter 'TabletPCButton'
Set: Unknown parameter 'Button 1'
Set: Unknown parameter 'Button 2'
Set: Unknown parameter 'Button 3'
Set: Unknown parameter 'PressureCurve'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger touch value for 'Suppress'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger touch value for 'RawSample'
Set: Unknown parameter 'CursorProximity'
Set: Unknown parameter 'Button 1'
Set: Unknown parameter 'Button 2'
Set: Unknown parameter 'Button 3'
Set: Unknown parameter 'Button 1'
Set: Unknown parameter 'Button 2'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger pad value for 'AbsWDn'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooPT 2FG Small Finger pad value for 'AbsWUp'
Set: Unknown parameter 'Button 3'
Set: Unknown parameter 'Button 4'
```

---

### Post by Favux on 2011-03-24
This isn't making much sense.  About the only thing I can come up with is that xsetwacom didn't install for some reason.  Or there are two of them conflicting.  Check in /usr/local/bin for a xsetwacom executable/binary (it should be in /usr/bin). This may mean the '--prefix=/usr' flag was left off on the xf86-input-wacom configure line. In which case you may have a xsetwacom executable in both locations and are experiencing version conflict. Delete the one in the wrong location, i.e. /usr/local/bin and reboot.  Do you see at least one?  If so where is it?

---

### Post by Ghostlove on 2011-03-24
I did indeed have xsetwacom in both /usr/bin and /usr/local/bin. I have deleted the one from /usr/local/bin and rebooted. What should I do now? Re-try the script?

Thank you, by the way, for being so endlessly patient with me, and so helpful!

---

### Post by Ghostlove on 2011-03-24
Okay, so I just tried to run that script again and this time I got:

```
Parameter 'Button 1' is no longer in use. It was replaced with 'Button'.
Parameter 'Button 2' is no longer in use. It was replaced with 'Button'.
Parameter 'Button 3' is no longer in use. It was replaced with 'Button'.
Parameter 'Button1' is no longer in use. It was replaced with 'Button'.
Property 'Wacom Proximity Threshold' does not exist on device.
Parameter 'Button 1' is no longer in use. It was replaced with 'Button'.
Parameter 'Button 2' is no longer in use. It was replaced with 'Button'.
Parameter 'Button 3' is no longer in use. It was replaced with 'Button'.
Parameter 'Button 1' is no longer in use. It was replaced with 'Button'.
Parameter 'Button 2' is no longer in use. It was replaced with 'Button'.
Unknown parameter name 'AbsWDn'.
Unknown parameter name 'AbsWUp'.
Parameter 'Button 3' is no longer in use. It was replaced with 'Button'.
Parameter 'Button 4' is no longer in use. It was replaced with 'Button'.
```

---

### Post by Favux on 2011-03-24
That looks like progress.

Try entering a parameter line one at a time and fixing each one rather than a whole script if there are problems.

For example AbsWDn & AbsWUp are probably AbsWheelDown & AbsWheelUp now.

As you can see it tries to tell you how the name changed.  Although it doesn't work for Button does it?

Don't really understand your other problems.  I'd need to know how many tablet buttons your Bamboo has.  Does it have a scroll wheel?  Then I'd need to see the output of *xinput list* and also the script you are trying to use.  Also what is the model number on the bottom of your tablet?

---

