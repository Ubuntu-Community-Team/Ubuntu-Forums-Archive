---
title: "wacom cinteq 21 uk driver not loaded anymore"
date: 2010-07-05
forum: Hardware
---

### Post by ewientje on 2010-07-05
Hi I installed my wacom a couple of weeks ago, worked fine, but today my pen stopped working.
After checking my driver list Wacom driver is not loaded properly anymore.

I used to be :

corrie@corrie-desktop:~$ dmesg | grep wacom
[   19.099158] usbcore: registered new interface driver wacom
[   19.099165] wacom: v1.52-pc-0.3:USB Wacom tablet driver
corrie@corrie-desktop:~$ dmesg | grep Wacom
[   17.425477] input: Wacom Cintiq 21UX2 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input5
[   19.099165] wacom: v1.52-pc-0.3:USB Wacom tablet driver
corrie@corrie-desktop:~$ ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root 9 2010-06-07 19:27 pci-0000:00:1d.2-usb-0:2:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2010-06-07 19:27 pci-0000:00:1d.2-usb-0:2:1.0-wacom -> ../event5
lrwxrwxrwx 1 root root 9 2010-06-07 19:27 pci-0000:00:1d.7-event-mouse -> ../event7
lrwxrwxrwx 1 root root 9 2010-06-07 19:27 pci-0000:00:1d.7-mouse -> ../mouse3
lrwxrwxrwx 1 root root 9 2010-06-07 19:27 platform-i8042-serio-0-event-kbd -> ../event4
lrwxrwxrwx 1 root root 9 2010-06-07 19:27 platform-i8042-serio-1-event-mouse -> ../event6
lrwxrwxrwx 1 root root 9 2010-06-07 19:27 platform-i8042-serio-1-mouse -> ../mouse2
corrie@corrie-desktop:~$ 


Now it is 

corrie@corrie-desktop:~$ dmesg | grep wacom
[   15.958092] usbcore: registered new interface driver wacom
[   15.958818] wacom: v1.52:USB Wacom tablet driver
corrie@corrie-desktop:~$ dmesg |grep Wacom
[   15.958818] wacom: v1.52:USB Wacom tablet driver
corrie@corrie-desktop:~$ 

The 
[   17.425477] input: Wacom Cintiq 21UX2 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input5
[   19.099165] wacom: v1.52-pc-0.3:USB Wacom tablet driver
is missing.

I checked to see if ubuntu was loading wacom, and if it is in etc/modules. Which it is, but it is not the one I installed.

Somehow the driver is gone, so what do I do.
The xorg.conf file is still there.
my kernel is 2.6.32-23-generic

corrie@corrie-desktop:~$ lsmod |grep wacom
wacom                  21745  0

---

### Post by Favux on 2010-07-05
Hi ewientje,

When a kernel update happens the new kernel comes with the default wacom.ko in it's modules directory.  You either need to copy the compiled wacom.ko into place or recompile.

See I. here:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

---

### Post by ewientje on 2010-07-06
Right I recompiled the driver, and now I don't have my desktop anymore.
I'm logging in from another computer, my ubuntu is prompt login only now.

in failsafe mode, the screens have no usable configuration.
So how do I get that back.

Good i have put up a second screen, I can enter the desktop now, the stylus works sort of on the wacom, but I have low resolution, and the stylud drags.

---

### Post by ewientje on 2010-07-06
from the x-server logfile failed to open /dev/input/by-path/pci-0000:00:1d.2-usb-0:2:1.0-event-mouse

---

### Post by Favux on 2010-07-06
Hi ewientje,

Compiling shouldn't have done that.  Did you do something else?  Not booting may be a video driver problem.  It sounds like maybe you changed your video section in xorg.conf.  Low resolution could indicate a VESA driver.  What is your video chipset?:
```
lspci | grep VGA
```

I assumed you're on Lucid, is that correct?

---

### Post by ewientje on 2010-07-06
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6700 XL] (rev a2

ubuntu 10.04

corrie@corrie-desktop:~$ lsmod | grep wacom
wacom                  30210  0 


I had a cannot open console 7 input/output error xf86org
There were more in the log.

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux corrie-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686
Kernel command line: root=UUID=dac25330-8a25-42fb-8278-b8b60d2c021b ro quiet splash 
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul  6 16:40:59 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
Data incomplete in file /etc/X11/xorg.conf
	Undefined InputDevice "pad" referenced by ServerLayout "Default Layout".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log

---

### Post by Favux on 2010-07-06
OK, it looks like you did something to your xorg.conf.  You have a Nvidia chipset.  Are you using the Nvidia proprietary drivers?

We'll have to look at xorg.conf.  It's at '/etc/X11/xorg.conf.

---

### Post by ewientje on 2010-07-06
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

Section "InputDevice" 
    Identifier     "stylus" 
    Driver         "Wacom" 
    Option         "Device" "/dev/input/by-path/pci-0000:00:1d.2-usb-0:2:1.0-event-wacom" 
    Option         "Device"	"/dev/input/wacom" 
    Option         "Type" "stylus" 
    Option         "USB" "on" 
    Option         "Button2" "3" # make side-switch a right button 
EndSection 

Section "InputDevice" 
    Identifier     "eraser" 
    Driver         "Wacom" 
    Option         "Device" "/dev/input/by-path/pci-0000:00:1d.2:1.0-event-wacom" 
    Option	   "Device"	"/dev/input/wacom" 
    Option         "Type" "eraser" 
    Option         "USB" "on" 
EndSection 

#Section "InputDevice" 
#	Driver		"Wacom" 
#	Identifier	"pad" 
#	Option 		"Device"	"/dev/input/Wacom" 
#	Option "Device" "/dev/input/by-path/pci-0000:00:1d.2-usb-0:2:1.0-event-mouse" 
#	Option 		"Device"	"/dev/input/wacom" 
#	Option 		"Type"		"pad" 
#	Option 		"USB" 		"on" 
#EndSection 

#Section "InputDevice" 
#    Identifier     "touch" 
#    Driver         "wacom" 
#    Option         "Device" "/dev/input/by-path/pci-0000:00:1d.2-usb-0:2:1.1-event-" 
#    Option         "Type" "touch" 
#    Option         "USB" "on" 
#    Option         "TopX" "200" 
#    Option         "TopY" "225" 
#    Option         "BottomX" "4000" 
#    Option         "BottomY" "3875" 
#EndSection 



# nvidia-settings: X configuration file generated by nvidia-settings 
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010 

Section "Monitor" 

# HorizSync source: edid, VertRefresh source: edid 
    Identifier     "Monitor0" 
    VendorName     "Unknown" 
    ModelName      "Samsung SyncMaster" 
    HorizSync       30.0 - 81.0 
    VertRefresh     56.0 - 85.0 
    Option         "DPMS" 
EndSection 

Section "Monitor" 

# HorizSync source: edid, VertRefresh source: edid 
    Identifier     "Monitor1" 
    VendorName     "Unknown" 
    ModelName      "WAC Cintiq 21UX 2" 
    HorizSync       30.0 - 80.0 
    VertRefresh     50.0 - 75.0 
    Option         "DPMS" 
EndSection 

Section "Device" 
    Identifier     "Device0" 
    Driver         "nvidia" 
    VendorName     "NVIDIA Corporation" 
    BoardName      "GeForce 6700 XL" 
    BusID          "PCI:1:0:0" 
    Screen          0 
EndSection 

Section "Device" 
    Identifier     "Device1" 
    Driver         "nvidia" 
    VendorName     "NVIDIA Corporation" 
    BoardName      "GeForce 6700 XL" 
    BusID          "PCI:1:0:0" 
    Screen          1 
EndSection 

Section "Screen" 
    Identifier     "Default Screen" 
    Device         "Device0" 
    Monitor        "Monitor0" 
EndSection 

Section "Screen" 
    Identifier     "Screen0" 
    Device         "Device0" 
    Monitor        "Monitor0" 
    DefaultDepth    24 
    Option         "TwinView" "0" 
    Option         "TwinViewXineramaInfoOrder" "CRT-0" 
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0" 
    SubSection     "Display" 
        Depth       24 
    EndSubSection 
EndSection 

Section "Screen" 
    Identifier     "Screen1" 
    Device         "Device1" 
    Monitor        "Monitor1" 
    DefaultDepth    24 
    Option         "TwinView" "0" 
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0" 
    SubSection     "Display" 
        Depth       24 
    EndSubSection 
EndSection 

Section "ServerLayout" 
	Identifier	"Default Layout" 
#	Identifier     "Layout0"? 
	Screen		0 "Screen0" 0 0 
	Screen		1 "Screen1" RightOf "Screen0" 
	Option		"Xinerama" "0" 
	Inputdevice	"stylus" 
	Inputdevice	"eraser" 
	InputDevice     "pad" 
#	Inputdevice	"touch" 
EndSection 



But i don't have nvidia loaded, and it won't install.

---

### Post by Favux on 2010-07-06
OK, the xorg.conf has been set up by nVidia settings.

In Lucid you do not need to use xorg.conf for Wacom.  You can use the 10-wacom.conf at /usr/lib/X11/xorg.conf.d/ and a xsetwacom script.  Did you make any changes to the wacom.conf?

I'll take a look at your xorg.conf.  Do you have a backup when the video worked?  If not this will take a while.

Edit:  Never mind.  I found the test3 we came up with in June.  Are you saying in Administration > Hardware Drivers there isn't a nVidia accerated driver available?

---

### Post by ewientje on 2010-07-06
Administration > Hardware Drivers there isn't a nVidia accerated driver available?
If I try to do that i get this :
Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid.

and 10-wacom.conf is empty

---

### Post by Favux on 2010-07-06
OK.  Check in /etc/X11 and see if there is a back up of one of your working xorg.conf's.  Always make a backup of your default and current working xorg.conf's.  Default (fresh install):
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.default
```
current
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
to restore from command line:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

This should be a valid xorg.conf, as long as the nvidia driver is installed.

---

### Post by ewientje on 2010-07-06
I used your xorg.conf and I have my nvidiadriver back, 2 screens, one normal, the wacom works sort of with the stylus. 
So the displayproperties are ok.
The stylus is not on the screen, and drags the colour with it, the eraser doesn't work.
You blanked them out. 
I have to find out the by-path now.

---

### Post by Favux on 2010-07-06
I'd suggest we try to use the 10-wacom.conf and not the xorg.conf.

---

### Post by ewientje on 2010-07-06
I don't have a 10 wacom.conf, can I copy the xorg.conf there, or do I have to do something else.

---

### Post by Favux on 2010-07-06
Just to be sure you're in Lucid 10.4, correct?

The 10-wacom.conf should be there.  It comes default with the Lucid xserver-xorg-input-wacom.  It still should be there even if we compiled the drivers.  Oh well.

Enter in a terminal:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
and copy and paste the following into it:
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
Then Save and reboot.  With a .conf file, just like xorg.conf, you can break X.  So be ready to rename 10-wacom.conf from the command line if it breaks X.  And if it works, it should, make a back up.

---

### Post by ewientje on 2010-07-06
I did, what you said, and now my stylus works in mypaint, but only on the right half of the screen.

---

### Post by Favux on 2010-07-06
Can you tell me what versions of the wacom drivers you have installed or when you installed them?

The screen thing probably just means we need to add an xsetwacom command.

You have 16 express buttons.  Two touch strips on the back, where?  And are those two D-rings breaking up the buttons or what?

---

### Post by ewientje on 2010-07-06
corrie@corrie-desktop:~$ modinfo -n wacom
/lib/modules/2.6.32-23-generic/kernel/drivers/input/tablet/wacom.ko
corrie@corrie-desktop:~$ modinfo -d wacom
USB Wacom tablet driver
USB Wacom tablet driver

I have 16 buttons 8 left, 8 right. I have 2 touchstrips on the back, didn't even know they were there, If I touch them the one screen open window scrolls, and i have 2 rings in the middle.

The left second top button responds as right mouse click.


I turned the one monitor off, and now I have the stylus and eraser working in mypaint.Not the pad, buttons or touch. 
If I knew where the wacom driver is located, I could copy it to a folder, together with the xorg.conf file, so if there again a kernel update. I could recopy them back.

---

### Post by Favux on 2010-07-06
Are the "rings" in the middle of each grp of eight buttons toggle switches or D-rings?

I've got a preliminary script almost ready.

---

### Post by ewientje on 2010-07-06
They are round rings, one press goes one down, there are 4 options each, I don;t know what toggle or d-ring is.

---

### Post by Favux on 2010-07-06
OK, we'll have to figure that out because I'm not sure either.  That may change the button mappings or numbers.

Follow section IV. here to get the script installed:  [http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1)


Edit:  Oops I forgot.  I need to see the output of:
```
xinput --list
```
in a terminal.  Thanks.

---

### Post by ewientje on 2010-07-06
corrie@corrie-desktop:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Cintiq 21UX2 eraser               	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Cintiq 21UX2 cursor               	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Cintiq 21UX2 pad                  	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Cintiq 21UX2 stylus               	id=12	[slave  pointer  (2)]
&#9116;   &#8627; X10 WTI RF receiver                     	id=13	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
corrie@corrie-desktop:~$

---

### Post by Favux on 2010-07-06
Does the Cintiq actually have a cursor, which is a Wacom tablet mouse?  I thought it did not have one.  Do you have any active Wacom sections in xorg.conf.  All Wacom stuff should be commented out.

---

### Post by ewientje on 2010-07-06
I have all of the wacom stuff in etc/x11/xorg.conf unmarked with #
The stylus works as a mouse. If I go over the screen now, the cursor follows, and I open things with it.

I did what you said with the chmosd script. xsetwacom and I have rebooted.


edited I'm going to bed, it is very late here. the stylys works reasonable in mypaint, so i can draw again. If you could tell me how to avoid that the driver is unloaded from my system, I would really appreciate it.

---

### Post by Favux on 2010-07-06
I'm sorry, this is the script I want you to use.  Don't use it though, I haven't finished it.  I'll post the finished version here in a few minutes.  But it gives you the idea.

I have the video stuff commented out for now.

Edit:  Than you for the thank you.  That's nice!  Right this is the script to use and you need to make it executable.  Remeber it's a rough draft and we need to refine it.

---

### Post by ewientje on 2010-07-06
By the way, this is a thank you note for your help.

So I have to use the finished script like the other chmod script in my home folder ?


Ok i chmod the .xsetwacom.sh script.
The stylus as a mouse works much better now. 
Button 2 on the pad works as a right mouse click, and the pad at the back of the monitor you can scroll with.
With the left ring you can select a group of words, sentence and highlight it, and I managed to copy something with it.

---

### Post by Favux on 2010-07-06
Good!  We're getting there.  Once you get it working you can play with it.  Try removing the comments in front of the video options in stylus and eraser, etc..  And then we can try and figure out the circular "buttons".

---

### Post by ewientje on 2010-07-07
The touchpads on the back are for scrolling a page up/down. Which is nice.

The left middle round button highlights a word or sentence.

If you something in the clipboard memory the button 1 = Ctrl V

Button 2 = right mouse click(menu appear under the cursor)

The other buttons all work as left mouse click if the cursor is on a menu

---

### Post by Favux on 2010-07-07
I think the reason I'm not following the button mapping you are describing is the wacom drivers you have installed are not working correctly.  The "pad" is now mostly working with xf86-input-wacom 0.10.7 because of the additions and fixes to xsetwacom.  I think the default Lucid 0.10.5 xf86-input-wacom and 0.8.4-4 linuxwacom aren't getting your pad to work right.

The other buttons should have different functions.  What we're trying to learn is if the map is, on the left side:

touch strip
1
2
3
4
mystery round thing
5
6
7
8

or, since you say it has 4 options

touch strip
1
2
3
4

D-ring; which may be 4 buttons
5
6
7
8

9 instead of 5
10 instead of 6
11 instead of 7
12 instead of 8

I think the only way to figure this out is to bring your wacom drivers up to the latest versions.  See I. and II. in the [Bamboo HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  You'll have to decide if you want to try it.

---

### Post by ewientje on 2010-07-08
Allright I'll give it a try later this evening.
The mystery round thing has 4 leds, so you can click it 4 times.

---

### Post by ewientje on 2010-07-08
I have recompiled the wacom-driver, rebooted the xf86 and the xorg-macros rebooted, and run xsetwacomscript. rebooted.


xsetwacom set "Wacom Cintiq 21UX2 pad" StripLDn "key Prior"  # pagedown
xsetwacom set "Wacom Cintiq 21UX2 pad" StripLUp "key Next"  # pageup
That is correct

xsetwacom set "Wacom Cintiq 21UX2 pad" StripRDn "key KP_Add"  # NumpadPlus
xsetwacom set "Wacom Cintiq 21UX2 pad" StripRUp "key KP_Subtrac"key KP_Add"t"  # NumpadMinus  

This is not correct they are pagedown/pageup

xsetwacom set "Wacom Cintiq 21UX2 pad" Button1 "key ctrl"   No
xsetwacom set "Wacom Cintiq 21UX2 pad" Button2 "key alt"    No  this is Right/click Mouse (right click menu appears)
xsetwacom set "Wacom Cintiq 21UX2 pad" Button3 "key shift"  No if I click on this button, while I'm in Firefox I get back a page (go back a page in the browser) 
xsetwacom set "Wacom Cintiq 21UX2 pad" Button4 "key tab"    No this is not working as a tab

## Need to figure out circle "button".

This selects highlights, first a word, then the whole sentence, like several left mouseclicks do.

The stylus and eraser now works fine in the Gimp.
The stylus points, paints, there is pressure, erasure works, the buttons works in mypaint like left, right and middle click mouse should.

---

