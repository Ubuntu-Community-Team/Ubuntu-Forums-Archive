---
title: "Touchpad Button Issues (Ubuntu MATE 22.04 LTS)"
date: 2024-02-15
forum: Hardware
---

### Post by mdrone on 2024-02-15
[SIZE=3][COLOR=#141414][FONT=&quot]Machine:[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Type: Laptop[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]System: Micro-Star (MSI)[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Product: Modern 15 H B13M v: REV:1.0[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Desktop: MATE 1.26.0[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Device 'PNP0C50:00 04F3:3282 Touchpad'[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]I'm having one heck of a time using the left and right "mouse click" buttons at the bottom of the touchpad. The left-click button is almost impossible to find. It keeps wanting to be a right-click button. I have checked things using 'sudo libinput debug-gui' and found that the mapping for those buttons seems to be all over the place. [Insert head scratch here][/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]I'm seeking advice and a solution if one exists. It's a fine machine otherwise, but the touchpad is forcing me to plug in a USB mouse to get any serious work done.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]I realize that MSI products are tailored to run various versions of the Microsoft OS. I have the laptop set up in dual-boot mode and have no problems with the touchpad when using Windows 11 (which I despise).[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]This is surely an issue with the libinput or xinput modules, but am hoping that there is some configuration setting that can remedy the problem.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Thanks in advance for any light that can be shed on this. Google has been a black hole for solutions. An MSI forum user recommended that I post here.
[/FONT][/COLOR]
More information:

[/SIZE]Device 'PNP0C50:00 04F3:3282 Touchpad':
	Device Enabled (190):	1
	Coordinate Transformation Matrix (192):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	libinput Tapping Enabled (347):	1
	libinput Tapping Enabled Default (348):	0
	libinput Tapping Drag Enabled (349):	1
	libinput Tapping Drag Enabled Default (350):	1
	libinput Tapping Drag Lock Enabled (351):	0
	libinput Tapping Drag Lock Enabled Default (352):	0
	libinput Tapping Button Mapping Enabled (353):	1, 0
	libinput Tapping Button Mapping Default (354):	1, 0
	libinput Natural Scrolling Enabled (326):	0
	libinput Natural Scrolling Enabled Default (327):	0
	libinput Disable While Typing Enabled (355):	1
	libinput Disable While Typing Enabled Default (356):	1
	libinput Scroll Methods Available (328):	1, 1, 0
	libinput Scroll Method Enabled (329):	1, 0, 0
	libinput Scroll Method Enabled Default (330):	1, 0, 0
	libinput Click Methods Available (357):	1, 1
	libinput Click Method Enabled (358):	1, 0
	libinput Click Method Enabled Default (359):	1, 0
	libinput Middle Emulation Enabled (360):	0
	libinput Middle Emulation Enabled Default (361):	0
	libinput Accel Speed (335):	0.000000
	libinput Accel Speed Default (336):	0.000000
	libinput Accel Profiles Available (337):	1, 1
	libinput Accel Profile Enabled (338):	1, 0
	libinput Accel Profile Enabled Default (339):	1, 0
	libinput Left Handed Enabled (340):	0
	libinput Left Handed Enabled Default (341):	0
	libinput Send Events Modes Available (311):	1, 1
	libinput Send Events Mode Enabled (312):	0, 0
	libinput Send Events Mode Enabled Default (313):	0, 0
	Device Node (314):	"/dev/input/event10"
	Device Product ID (315):	1267, 12930
	libinput Drag Lock Buttons (342):	<no items>
	libinput Horizontal Scroll Enabled (343):	0
	libinput Scrolling Pixel Distance (344):	15
	libinput Scrolling Pixel Distance Default (345):	15
	libinput High Resolution Wheel Scroll Enabled (346):	1[SIZE=3]
[COLOR=#141414][FONT=&quot]-MD[/FONT][/COLOR][/SIZE]

---

### Post by him610 on 2024-02-17
I have the same issue whenever I use my wife's laptop.
This works for me ...
```
# Disable/enable touchpad when mouse connected
#disable
synclient TouchpadOff=1
#enable
synclient TouchpadOff=0
 
```
I defined a couple of aliases in my .bash_aliases file. Whenever you open a terminal the file is called by .bashrc then you just type in the alias on the CLI.

---

### Post by mdrone on 2024-02-18
Thanks for the response. I'm guessing this would require that I install the synaptics driver (sudo apt install xserver-xorg-input-synaptics). I'm not sure what impact that will have on the overall operation of my input devices (touchpad & keyboard). Right now, I don't have a problem with the touchpad being enabled/disabled whenever a mouse is connected. I just can't seem to locate the blasted left-click button on the touchpad.

---

### Post by him610 on 2024-02-18
In your User Manual, page 2-14...
> Touchpad
Press to enable or disable the touchpad function.
To find out exactly where the left and right buttons are, you may want to contact MSI support.
[https://www.msi.com/support]("https://www.msi.com/support")

---

### Post by mdrone on 2024-02-20
I have the User Manual. Read it cover-to-cover. Chatted with a MSI Tech Service agent who apologized and said  "We don't deal with Linux, nor do I know others in the office that does. We all mostly deal with windows OS at work and at home." I decided to try a live version of another flavor to see what happens, so I booted up ZorinOS and found that the left-click button works just fine with that distro. Guessing since it's based on Ubuntu, it has to be using the same touchpad driver. I'm not savvy enough to know if the Desktop environment has anything to do with the configuration of things like this (Gnome3 vs XFCE 4 vs MATE).

---

### Post by mdrone on 2024-02-21
I ran 'xinput' and 'xinput list-props' on the ZorinOS live distro and saved and compared the output to the same output on my Ubuntu MATE 22.04 installation. What I found was a discrepancy between the "libinput Click Method Enabled" section. On the ZorinOS live distro, it was set to (0, 1) and on my Ubuntu MATE 22.04 install, it was set to (1, 0).


I decided to change the "Click Method" property on my Ubuntu MATE 22.04 installation with the following command:


[FONT=courier new]sudo xinput --set-prop "PNP0C50:00 04F3:3282 Touchpad" "libinput Click Method Enabled" 0 1[/FONT]


Amazingly, it worked!


To find the name of the Touchpad (and its ID number):
$ xinput
This reveals the following:
PNP0C50:00 04F3:3282 Touchpad   id=10


To list the properties of the Touchpad (ID=10):
[FONT=courier new]$ xinput list-props 10[/FONT]


To change a specific property of the Touchpad:
[FONT=courier new]$ sudo xinput --set-prop "PNP0C50:00 04F3:3282 Touchpad" "libinput Click Method Enabled" 0 1[/FONT]


To verify that the property of the Touchpad were changed:
[FONT=courier new]$ xinput list-props 10[/FONT]


To apply the change permanently:
Hit the "Windows" key on the keyboard
Type "Start" and click the "Startup Applications Preferences" icon.
In the "Startup Applications Preferences" window, click the "Add" button.
Enter a "Name" in the name field
Enter "sudo xinput --set-prop "PNP0C50:00 04F3:3282 Touchpad" "libinput Click Method Enabled" 0 1" in the "Command" field
Give it a brief description in the "Description" field
Click "Add"


This should add the Touchpad modification to the startup command sequence.


Alternatively, create the following file and add the code snippet below it (using sudo):


/usr/share/X11/xorg.conf.d/99-configuration.conf


[FONT=courier new]Section "InputClass"[/FONT]
[FONT=courier new]    Identifier  "libinput click method"[/FONT]
[FONT=courier new]    MatchProduct    "PNP0C50:00 04F3:3282 Touchpad"[/FONT]
[FONT=courier new]    Option "Click Method Enabled" "0 1"[/FONT]
[FONT=courier new]EndSection[/FONT]

I'm hoping this will help anyone who has similar problems with a finicky touchpad.

---

### Post by him610 on 2024-02-21
@mdrone
Congratulations on figuring out a way to solve your problem. Your solution may help others in the future.

---

