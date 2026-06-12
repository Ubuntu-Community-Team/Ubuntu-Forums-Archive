---
title: "Horizontal scroll on Logitech Cordless Click! Plus, help!"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by AstarothCY on 2007-01-30
Ubuntu 6.10 Edgy Eft x86 32bit
Logitech Cordless Desktop LX500 (which includes the Cordless Click! Plus mouse)


I have followed [this Tutorial]("http://ubuntuforums.org/showthread.php?t=65471&highlight=mouse+wheel+horizontal+scroll") as well as other ones that pretty much all say the same thing, and I am really getting nowhere. I can't find any decent help on how to use IMWheel or Xmodmap and it's impossible to get horizontal scroll to work.

First of all, it should be noted that running xev or imwheel --config registers "left" as some button, the actual number of the button varies according to settings in Xmodmap, HOWEVER **"right" has never worked at all**. No matter what xorg, Xmodmap or IMWheel configuration, "right" has never registered in xev, yet I know it works fine because I use it in windows. That's one problem that I don't even know how to begin fixing.

Also, I have tried all sorts of USB/PS2 configurations (such as: both on USB, both on PS2, mouse on PS2 and KB on USB) but it doesnt really seem to make a difference.


_My cat output:_
```
I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:03.1-1/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="**Logitech USB Receiver**"
P: Phys=usb-0000:00:03.1-1/input1
S: Sysfs=/class/input/input2
H: Handlers=**_*kbd*_ mouse0** event2 ts0 
B: EV=7
B: KEY=7fffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=143


```

"kbd" always appears with "mouse 0" regardless of the USB/PS2 configuration. Is this normal?



Here are my configs:


_xorg.conf_
```
Section "InputDevice"
	Identifier      "Configured Mouse"
	Driver		"evdev"
	Option 		"Protocol" 	"ExplorerPS/2"
	Option          "SendCoreEvents"
	Option          "Dev Name"              "Logitech USB Receiver"
	Option          "Dev Phys"              "usb-*/input1"
	Option          "Device"                "/dev/input/mice"
	Option          "Buttons"               "10"
	Option          "ZAxisMapping"          "4 5"
	Option         "ButtonMapping" "1 2 3 4 5 6 7 8 9 10"
EndSection
```


_Xmodmap_
```
pointer = 1 2 3 4 5 6 7 9 10 8
```

_IMWheel_
```
# IMWheel Configuration file ($HOME/.imwheelrc or /etc/imwheelrc)
# (GPL)Jon Atkins <jcatki@jonatkins.org>
# Please read the README and/or imwheel(1) manpage for info
# and this is best operated on using vim (as I said: It's crunchy)

#
# This is only for demonstration of the priority command...
# See the other global Exclude command below for the one you want to use!
# If this is activated it will only apps that have a lower priority
# priority is based first on the priority command, then the position in this
# file - the higher the line is in a file the higher in a priority class it is
# thus for a default priority you can see that the position in the file is
# important, but the priority command CAN appear anywahere in a window's list
# of translations, and the priority will be assigned to all translations below
# it until either a new window is defined or the priority is set again.
#
#".*"
#@Priority=-1000 #the default priority is zero, higher numbers take precedence
#@Exclude
#@Repeat

# want it to type something?
# this would type "Rofl" and press Return in any window
#".*"
#,Up,Shift_L|R|-R|-Shift_L|O|-O|F|-F|L|-L|Return



# This one rule can send button events, as if you used ZAxisMapping "4 5"
# Make sure your XF86Config allows for the max buttons needed...
# otherwise the events will NOT even be generated...
#".*"
#, Up, Button4
#, Down, Button5
#, Left, Button6
#, Right, Button7
#, Thumb1, Button6
#, Thumb2, Button7
# alternatively with Button numbers
#".*"
#, Button4, Button4
#, Button5, Button5
#, Button6, Button6
#, Button7, Button7
#, Button6, Button6
#, Button7, Button7

#Thanks to Mathias Weyland <mathias@weyland-wtal.de>
"^mutt.*"
None,           Up,     Up
None,           Down,   Down
Control_L,      Up,     Page_Up
Control_L,      Down,   Page_Down

#Thanks to Mathias Weyland <mathias@weyland-wtal.de>
"^aterm"
None,           Up,     Shift_L|Page_Up
None,           Down,   Shift_L|Page_Down
Control_L,      Up,     Up
Control_L,      Down,   Down

#Thanks to Mathias Weyland <mathias@weyland-wtal.de>
"^Xplns"
None,           Up,     Left
None,           Down,   Right
Control_L,      Up,     Up
Control_L,      Down,   Down

"^kvt"
None,		Up,		Shift_L|Page_Up
None,		Down,	Shift_L|Page_Down

"^Konsole"
None,		Up,		Shift_L|Page_Up
None,		Down,	Shift_L|Page_Down

"^XMcd"
None,		Up,		C
None,		Down,	Shift_L|C

"^XMMS_Player"
Shift_L,		Up,		Right
Shift_L,		Down,	Left

"^XMMS_Playlist"
Shift_L,	Up,		Page_Up
Shift_L,	Down,	Page_Down

"^xmms"
Alt_L,		Up,		Z
Alt_L,		Down,	B
Control_L,	Up,		V
Control_L,	Down,	C

"^XATITV-GATOS"
None,       Down,	KP_Subtract
None,       Up,		KP_Add

"^Xman"
None,		Down,	F
Shift_L,	Down,	3
None,		Up,		B

"^Gvi(m|ew)"
Alt_L,	Up,		Page_Up
Alt_L,	Down,	Page_Down
Shift_L,	Up,		Control_L|Y
Shift_L,	Down,	Control_L|E
#None,		Up,		Page_Up
#None,		Down,	Page_Down
#,	Up,	Button4
#,	Down,	Button5
,	Left,	Shift_L|Left
,	Right,	Shift_L|Right
,	Thumb1,	Shift_L|Left
,	Thumb2,	Shift_L|Right

"^VIM"
Shift_L,	Up,		Control_L|Y
Shift_L,	Down,	Control_L|E
#None,		Up,		Page_Up
#None,		Down,	Page_Down

"^Eterm"
Alt_L,		Up,		Up
Alt_L,		Down,	Down
#Alt_L,   	Up,     Shift_L|Page_Up
#Alt_L,   	Down,   Shift_L|Page_Down

#"^GnomeTerminal"
#@Exclude
#@Repeat
#None,		Up,		Shift_L|Page_Up
#None,		Down,	Shift_L|Page_Down

"^NXTerm"
None,   	Up,     Shift_L|Page_Up
None,   	Down,   Shift_L|Page_Down

"^rxvt"
Alt_L,  	Up,		Shift_L|Page_Up
Alt_L,  	Down,	Shift_L|Page_Down

"^XTerm"
Alt_L,		Up,		Shift_R|Page_Up
Alt_L,		Down,	Shift_R|Page_Down
Alt_L,		Left,	Control_L|A
Alt_L,		Right,	Control_L|E
#Shift_L,	Down,	Shift_L|1

"^VMware"
@Exclude
#@Repeat

"^Mozilla-bin$"
#,	Up,	Button4
#,	Down,	Button5
#,	Left,	Alt_L|Left
#,	Right,	Alt_L|Right
#
# If you want to scroll by a few lines then uncomment these 4 lines
# and comment out the paging 4 lines below these!
#
Shift_L,	Down,	Page_Down,			1#,	1000,	1000
Shift_L,	Up,		Page_Up,			1#,	1000,	1000
#None,		Down,	Down,				7#,	1000,	1000
#None,		Up,		Up,					7#,	1000,	1000
#
# If you don't like page scrolling then comment these out and uncomment above!
#
#Shift_L,	Down,	Down,				7,
#Shift_L,	Up,		Up,					7,
#None,		Down,	Page_Down,			1,
#None,		Up,		Page_Up,			1,
# Left/Right & Thumb stuff
None,		Left,	Left,				7,
None,		Right,	Right,				7,
None,		Thumb1,	Down,				7,
Shift_L,	Thumb1,	Up,					7,
None,		Thumb2,	Up,					7,
Shift_L,	Thumb2,	Down,				7,

"^Freespace.*"
,	Up,		Y
,	Down,	X
,	Thumb1,	H
,	Thumb2,	R

"^SDL_App"
#,	Up,		Button4
#,	Down,	Button5
,	Thumb1,	Home	#many apps don't understand Button > 5
,	Thumb2, End		#many apps don't understand Button > 5

# Thanks to shewp <shewplx@pblx.net>
"^Opera" 
#@Repeat    # let qt do it
None,       Down,   Down,               4,  100,    100
None,       Up,     Up,                 4,  100,    100
None,       Thumb1, Right
None,       Thumb2, Left

"^Netscape.*"
, Thumb1, Alt_L|KP_Left
, Thumb2, Alt_L|KP_Right
#, Up, Button4
#, Down, Button5

"^Netscape"
#
# If you don't want to scroll by a few lines then comment out these 4 lines
# and uncomment the paging 4 lines below these!
#
Shift_L,	Down,	Page_Down,			1,	1000,	1000
Shift_L,	Up,		Page_Up,			1,	1000,	1000
None,		Down,	Down,				7,	1000,	1000
None,		Up,		Up,					7,	1000,	1000
#
# If you don't like page scrolling then uncomment these
# and comment out the 4 lines above!
#
#Shift_L,	Down,	Shift_L|Down,		7,	1000,	1000
#Shift_L,	Up,		Shift_L|Up,			7,	1000,	1000
#None,		Down,	Page_Down,			1,	1000,	1000
#None,		Up,		Page_Up,			1,	1000,	1000
# Left/Right & Thumb stuff
None,		Left,	Left,				7,	1000,	1000
None,		Right,	Right,				7,	1000,	1000
None,		Thumb1,	Down,				7,	1000,	1000
Shift_L,	Thumb1,	Up,					7,	1000,	1000
None,		Thumb2,	Up,					7,	1000,	1000
Shift_L,	Thumb2,	Down,				7,	1000,	1000

"^Navigator"
#Alt_L,		Down,	Alt_L|Right
#Alt_L,		Up,		Alt_L|Left
Alt_L,		Down,	Right,				10,	1000,	1000
Alt_L,		Up,		Left,				10,	1000,	1000

# Thanks to Paul J Collins <sneakums@usa.net>
"^emacs"
Shift_L,	Up,		Page_Up
Shift_L,	Down,	Page_Down
# you may need Alt instead of Meta....
None,		Down,	Control_L|Meta_L|Shift_L|parenright
None,		Up,		Control_L|Meta_L|Shift_L|parenleft

# Thanks to etienne grossmann <etienne@isr.ist.utl.pt>
"^Xftp"
,			Down,	j
,			Up,		k

".* - Pan$"
,	Left,	Control_L|Button1
,	Thumb1,	Control_L|Button1
#,	Up,	Button4
#,	Down,	Button5

# Thanks to etienne grossmann <etienne@isr.ist.utl.pt>
"^gv[ :]"
None,		Up,		Shift_L|space
None,		Down,	space

#"^Event Tester"
#@Repeat
#@Exclude
#,	Left,	Button6
#,	Right,	Button7
#,	Thumb1,	Button8
#,	Thumb2,	Button9

"^xv grab"
@Priority=1
@Exclude

"^XV.*"
None,	Down,	Tab
None,	Up,		Delete

"^Untitled"
# if using wheel fifo, you may switch these.
#,	Up,		Button4
#,	Down,	Button5
#with these
,	Up,		Page_Up
,	Down,	Page_Down
# (end of switch)
,   Thumb1, Home
,   Thumb2, End

"^No Title"
# if using wheel fifo, you may switch these.
#,	Up,		Button4
#,	Down,	Button5
#with these
,	Up,		Page_Up
,	Down,	Page_Down
# (end of switch)
,   Left, Home
,   Right, End
,   Thumb1, Home
,   Thumb2, End

#"\(null\)"
# if using wheel fifo, you may want the 2nd group
#,	Up,		Button4
#,	Down,	Button5
#,	Left, Button6
#,	Right, Button7
#,	Thumb1, Button8
#,	Thumb2, Button9
# 2nd group (old keys...)
#,	Up,		Page_Up
#,	Down,	Page_Down
#,	Left, Home
#,	Right, End
#,	Thumb1, Home
#,	Thumb2, End
# (end of switch)

# send event to the window manager when in the root window...
"\(root\)"
,	Up,		Control_L|N
,	Down,	Control_L|P
,   Thumb1,	Alt_L|Left
,	Thumb2,	Alt_L|Right

#
# Uncommment the following to exclude by default.
# Then you will have to add new apps all the time, but will retain any built-in
# wheel functionality contained in some KDE and other newer programs.
# This kinda defeats the original purpose of the program! ;)
#
#".*"
#@Priority=-1000
#@Exclude
#@Repeat

#
# These are the defaults, but note that the defaults for the right side of the
# keyboard are still handled within the program, unless you add the
# combinations desired here. (except for the None modifier of course!)
# If this section is deleted then the hardcoded defaults will be used, which
# are the same thing.
# Modifying these has global effects, but doesn't override what is above.
#
#".*"
#@Priority=-1001
#,	Up,	Button4
#,	Down,	Button5
#None,							Left,	Left
#None,							Right,	Right
#None,							Up,		Page_Up
#None,							Down,	Page_Down
#Shift_L,						Left,	Left
#Shift_L,						Right,	Right
#Shift_L,						Up,		Up
#Shift_L,						Down,	Down
#        Control_L,				Left,	Left,		2
#        Control_L,				Right,	Right,		2
#        Control_L,				Up,		Page_Up,	2
#        Control_L,				Down,	Page_Down,	2
#Shift_L|Control_L,				Left,	Left,		5
#Shift_L|Control_L,				Right,	Right,		5
#Shift_L|Control_L,				Up,		Page_Up,	5
#Shift_L|Control_L,				Down,	Page_Down,	5
#                  Alt_L,		Left,	Left,		10
#                  Alt_L,		Right,	Right,		10
#                  Alt_L,		Up,		Left,		10
#                  Alt_L,		Down,	Right,		10
#Shift_L|          Alt_L,		Left,	Left
#Shift_L|          Alt_L,		Right,	Right
#Shift_L|          Alt_L,		Up,		Left
#Shift_L|          Alt_L,		Down,	Right
#        Control_L|Alt_L,		Left,	Left.		20
#        Control_L|Alt_L,		Right,	Right.		20
#        Control_L|Alt_L,		Up,		Left.		20
#        Control_L|Alt_L,		Down,	Right.		20
#Shift_L|Control_L|Alt_L,		Left,	Left,		50
#Shift_L|Control_L|Alt_L,		Right,	Right,		50
#Shift_L|Control_L|Alt_L,		Up,		Left,		50
#Shift_L|Control_L|Alt_L,		Down,	Right,		50
#,   Thumb1, Home
#,   Thumb2, End

# vim:ts=4:shiftwidth=4:syntax=sh

".*"
None, Left, Alt_L|Left
None, Right, Alt_L|Right

```


With the above config, I have full function of left mouse button, right mouse button, middle mouse button, and vertical scroll. Horizontal scroll is non-functional in any application BUT it registers as "button 9" in xev. Actually, here is how the buttons register in xev:

left click: "button 1"
middle click: "button 2"
right click: "button 3"
scroll up: "button 4"
scroll down: "button 5"
scroll left: "button 9"
**task switch: "button 1"**   (this one drives me crazy as well, why is it registering as button 1?!)

EDIT: I should note that at some point, "scroll left" was in fact functional as "Home", but isn't anymore after I changed the Xmodmap config.

All I have been doing so far has been trial-and-error, since Xmodmap and IMWheel work in mysterious ways. I have followed pretty much every HowTo out there to the letter, i have followed them with slight variation, I have experimented by myself, but nothing. Help will be greatly appreciated.

---

### Post by AstarothCY on 2007-01-30
bump

---

### Post by AstarothCY on 2007-01-31
> **AstarothCY said:**
> bump

what he said

---

### Post by AstarothCY on 2007-02-02
> **AstarothCY said:**
> what he said

yet again

---

### Post by rajan on 2007-02-04
> 
With the above config, I have full function of left mouse button, right mouse button, middle mouse button, and vertical scroll. Horizontal scroll is non-functional in any application BUT it registers as "button 9" in xev. Actually, here is how the buttons register in xev:


so you have almost full functionality with your mouse?

---

### Post by AstarothCY on 2007-02-04
Not at all. Horizontal scroll and task switch do not work at all, despite the fact that they are detected by xev.

---

### Post by AstarothCY on 2007-02-06
bump :(

---

### Post by Nikron on 2007-02-06
Section "InputDevice"
	Identifier      "Configured Mouse"
	Driver		"evdev"
	Option 		"Protocol" 	"ExplorerPS/2"
	Option          "SendCoreEvents"
	Option          "Dev Name"              "Logitech USB Receiver"
	Option          "Dev Phys"              "usb-*/input1"
	Option          "Device"                "/dev/input/mice"
	Option          "Buttons"               "10"
	Option          "ZAxisMapping"          "4 5"
	Option         "ButtonMapping" "1 2 3 4 5 8 9 10"
        Option          "HWheelRelativeAxisButtons"     "7 6"
EndSection       

Try that if you want..

Also, I use xbindkeys as suggested in the tutorial you pointed too

---

### Post by AstarothCY on 2007-02-08
Thanks, but it still doesn't work.

I just want to point out the fact that [scroll right] is still not registered in any way, not even in xev. It's as if the button is dead, but it works fine in windows.

---

### Post by Sevmpe on 2007-02-12
Hi,

That is also the behaviour of my mouse (the one that comes with the logitech S510 media remote). The right horizontal scroll doesn't show when using xev.

I have been testing the buttons using evtest to see whether the right scroll worked and it reported an event code, so it's been recognized but somehow it does report the wrong code (279) when the event list says that the forward mouse button is 277.

I am still "googling" into this. Meanwhile, you could try to use evtest to see if you are having the same issue,

```
sudo evtest /dev/input/eventX
```

changing X to the event number associated to your mouse.

Regards.

---

### Post by AstarothCY on 2007-02-12
Thanks, please let me know if you find anything.

I can't run evtest, the command doesn't exist, but I do have udevtest which however doesn't work either.

```
 sudo udevtest /dev/input/event0
main: unable to open '/dev/input/event0'

```
Same result with event1/2/3 and mice.

---

### Post by Sevmpe on 2007-02-15
The program evtest is in the package dvb-utils. I tried different things and I got the horizontal wheel scroll working using the evdev driver for the mouse but then the multimedia keys of the keyboard stopped working. Then I wanted to use the evdev driver for keyboard and mouse but found some nasty bugs in Ubuntu's Xorg (reported in launchpad). So, no easy solution for me yet. Maybe you want to try what this guy did: [http://blog.cgamesplay.com/archives/12-Logitech-Cordless-Desktop-LX-501.html]("http://blog.cgamesplay.com/archives/12-Logitech-Cordless-Desktop-LX-501.html")
and see if it could be of any help to you.

Cheers.

---

