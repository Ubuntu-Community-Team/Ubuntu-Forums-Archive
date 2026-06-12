---
title: "Public Notes on Installing Ubuntu Intrepid on an HP TX2635us (tx2500 series)"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by oznozz on 2009-01-26
Notes on Installing Intreped on the HP Pavillion TX2635us (tx2500 series , confusingly labeled as "HP Pavillion tx2000 in lower lefthand corner")

=============================

This machine has an AMD dual core processor, ATI video, USB wacom tablet with touch, broadcom wifi and a suyin webcam.

I installed 32-bit Ubuntu Intrepid (8.10) i386 from the LiveCD, download circa January 18, 2009.

=============================

What do I care about?

* GUI
* wireless internet
* Wacom tablet stylus
* sound
* webcam

What works after a fresh install?

* the GUI
* wireless internet (enable the restricted drivers, restart, perform updates, restart again)
* webcam (install ekiga)

What requires work?

* the sound
* the Wacom

==============================

I. Wireless Internet

This Just Worked for me.  I think I had to follow the GUI prompts about installing/enabling some restricted drivers.  I have not tried the wireless with secure networks, so I cannot comment on that.

-------------------------------

II. Webcam

ekiga --
  $ sudo aptitude upgrade
  $ sudo aptitude install ekiga
  $ ekiga&

The last line will start ekiga.  You do not need to start it this way, it is in the menu, but this is a fast way of going about it if you are already typing commands into your prompt.  A window will pop with no obvious webcam.  Click the little webcam looking icon in the lower left, and that will activate the cam.  You should see youself in a tiny window.

...............................

xawtv -- Scary Things happen when this program is run.  Specifically, the entire screen blacks out, the webcam light blinks ominously and panic ensues.  None of the keyboard commands appear to do anything.  Ctrl-C will eventually kill the program, but it will not restore the GUI.  Switching to one of the ttys and back to the GUI will fix it (if that doesn't make sense don't worry.  just don't try this program with this computer.)

...............................

skype -- I hope it works.

-------------------------------

III. Sound -- (edited)

the magical incantation is :

$ sudo cp -p /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.bak
$ sudo gedit /etc/modprobe.d/alsa-base

and add the following as the last line :

options snd-hda-intel index=0 model=toshiba position_fix=1

and then restart.

(other methods of restarting ALSA which occurred to me did not fix the sound.  further, other ways of formulating the line to add do not fix the sound, in my experience.)

I cannot explain any of this at all.  Thanks to Favux and gali98.

The above line summarizes their help into a single line.

-------------------------------

IV. Touchpad

For more completeness, see gali98's guide and the Linux Wacom Project Documentation.  I think the following should work on Jan 22, 2009 (the explicit transcript is long and involves various false starts) :

= I. Get everything up to date =

$ sudo aptitude update
$ sudo aptitude upgrade
(restart if necessary)

= II. Install supporting programs =

$ sudo aptitude install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev linux-headers-generic wacom-tools xserver-xorg-input-wacom tee

(SHORTCUT -- after this step, it may be possible to skip to part V. below.  I do not know if the current Ubuntu wacom packages are sufficiently up to date to avoid custom building them.)

$ sudo aptitude purge wacom-tools xserver-xorg-input-wacom

(why are we adding and removing these wacom packages?  Answer : installing them adds some other packages the wacom packages depend on to be available.  We are going to build our own wacom packages, so we remove the Ubuntu provided versions and keep the packages they depend on.)

= III. Download the most current version of linuxwacom (as of Jan 22, 2009) =

$ cd ~
$ wget [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.2-2.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.2-2.tar.bz2)
$ tar -xvf linuxwacom-0.8.2-2.tar.bz2 
$ cd linuxwacom-0.8.2-2/

(you can go to [http://linuxwacom.sourceforge.net/index.php/dl](http://linuxwacom.sourceforge.net/index.php/dl) to figure out the most current version.)

= IV. Configure and build the wacom driver =

$ ./configure --enable-wacom --prefix=/usr | tee wacomConfigOut.txt

(what is tee?  tee is a program that will save the output of another program to a text file.  it makes it easier to send output to forums!)

$ make | tee wacomMakeOut.txt
$ sudo make install  | tee wacomInstallOut.txt
$ sudo cp ./src/2.6.27/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

<restart your computer>

I had some issues with getting all the pieces installed somehow, so go ahead and do this one more time :

$ cd ~/linuxwacom-0.8.2-2/
$ sudo make install
$ sudo cp ./src/2.6.27/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

<restart>

to confirm the install :

$ which wacomcpl

should return

/usr/bin/wacomcpl

= V. Confirm that the wacom driver module is in place =

$ sudo modprobe -vr wacom
output looks like :
rmmod /lib/modules/2.6.27-9-generic/kernel/drivers/input/tablet/wacom.ko
# deactivate wacom module (answer to "is the wacom module being inserted at start up?")

$ sudo modprobe -v wacom
output looks like :
insmod /lib/modules/2.6.27-9-generic/kernel/drivers/input/tablet/wacom.ko 
# re-activated wacom module

*** If you do this later without restarting the x-windows, the wacom will appear to stop working!!!

(the "v" is for verbose; the output of this program tends to be terse even with this option)

$ dmesg | grep Wacom

This should output something like :

# the initial load by the kernel
[   17.106872] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb6/6-2/6-2:1.0/input/input10
[   17.334899] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb6/6-2/6-2:1.1/input/input11
[   17.396873] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
# the modprobe load from the above command
[ 2777.771041] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb6/6-2/6-2:1.0/input/input13
[ 2777.848869] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb6/6-2/6-2:1.1/input/input14
[ 2777.876633] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver

Note the part about PCI in the message from the kernel found with dmesg | grep Wacom; the information it provides will help point us to the right devices for the xorg.conf.

= VI. Configuring the xorg.conf file =

IF YOU ARE USING EXACTLY MY MACHINE (tx2635us) and you are brave, just use the xorg.conf file below and restart your x server.
OTHERWISE, see below for ways to figure out whether the tablet is installed, and whether you can read it.

The folowing /etc/X11/xorg.conf file works on this specific machine.  It will probably not work unless you have this exact machine, but it will provide some helpful hints for other models.  Keep in mind that this Wacom tablet is a perenially connected USB device and not a serial device.

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "touch"
  Option        "Device"        "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-"
  Option        "Type"          "touch"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen "Default Screen"
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
	InputDevice    "touch"     "SendCoreEvents"    # Only a few TabletPCs support this type
EndSection

---------------------

= Identifying the Wacom Tablet by Hand =

The following steps assume that you installed the driver successfully with the steps above.

The easiest way I can think of to identify the right device to set the wacom components to is by checking the contents of /proc/bus/input/devices
by e.g.
$ less /proc/bus/input/devices

To search for case sensitive text in less, hit the "esc" key, then type, e.g.
:/Wacom
and hit enter.

My output looks like this :

I: Bus=0003 Vendor=056a Product=0093 Version=0403
N: Name="Wacom ISDv4 93"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:14.5/usb6/6-2/6-2:1.0/input/input10
U: Uniq=
H: Handlers=mouse1 event10 
B: EV=b
B: KEY=3c03 0 0 0 0 0 0 0 0 0 0
B: ABS=100 100001b

I: Bus=0003 Vendor=056a Product=0093 Version=0403
N: Name="Wacom ISDv4 93"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:14.5/usb6/6-2/6-2:1.1/input/input11
U: Uniq=
H: Handlers=mouse2 event11 
B: EV=b
B: KEY=3c03 0 0 0 0 0 0 0 0 0 0
B: ABS=100 100001b

Notice that the lines with "S: Sysfs=" are identical to the lines reported by the kernel on startup.  Your machine may have different details.

Now, try a :
$ ls -l /dev/input/by-path/

My output is :

total 0
lrwxrwxrwx 1 root root  9 2009-01-23 11:48 pci-0000:00:13.2-usb-0:2:1.0-event- -> ../event8
lrwxrwxrwx 1 root root 10 2009-01-23 12:34 pci-0000:00:14.5-usb-0:2:1.0-event-mouse -> ../event10
lrwxrwxrwx 1 root root  9 2009-01-23 12:34 pci-0000:00:14.5-usb-0:2:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 2009-01-23 12:34 pci-0000:00:14.5-usb-0:2:1.1- -> ../mouse2
lrwxrwxrwx 1 root root 10 2009-01-23 12:34 pci-0000:00:14.5-usb-0:2:1.1-event- -> ../event11
lrwxrwxrwx 1 root root  9 2009-01-23 11:48 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root 10 2009-01-23 11:48 platform-i8042-serio-1-event-mouse -> ../event12
lrwxrwxrwx 1 root root  9 2009-01-23 11:48 platform-i8042-serio-1-mouse -> ../mouse3
lrwxrwxrwx 1 root root  9 2009-01-23 11:48 platform-pcspkr-event-spkr -> ../event9

Match the "S: Sysfs=" part that says "input" to the device above.

For my computer, I have two Wacom devices.  So I will match as follows :


Wacom Stylus Tablet :

S: Sysfs=/devices/pci0000:00/0000:00:14.5/usb6/6-2/6-2:1.1/input/input10

lrwxrwxrwx 1 root root 10 2009-01-23 12:34 pci-0000:00:14.5-usb-0:2:1.0-event-mouse -> ../event10

The path to my stylus/eraser device is :

/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse


Wacom Touch Tablet :

S: Sysfs=/devices/pci0000:00/0000:00:14.5/usb6/6-2/6-2:1.1/input/input11

lrwxrwxrwx 1 root root 10 2009-01-23 12:34 pci-0000:00:14.5-usb-0:2:1.1-event- -> ../event11

The path to my touch device is :

/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-



== Testing that the paths above actually go to the tablet ==

This can be done without having a configured xorg.conf.

Stylus Tablet :

Execute the command (in my case, change the device to match your machine)
$ sudo xxd /dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse

and touch the screen with the stylus or eraser.  Large amounts of output should come streaming onto the terminal with lots of incomprehensible characters.

e.g. :

0003ed0: 0a07 7a49 4fd4 0e00 0300 0000 c944 0000  ..zIO........D..
0003ee0: 0a07 7a49 58d4 0e00 0300 0100 dd22 0000  ..zIX........"..
0003ef0: 0a07 7a49 5bd4 0e00 0000 0000 0000 0000  ..zI[...........
0003f00: 0a07 7a49 8cf3 0e00 0300 0000 e644 0000  ..zI.........D..
0003f10: 0a07 7a49 94f3 0e00 0300 0100 9422 0000  ..zI........."..
0003f20: 0a07 7a49 96f3 0e00 0000 0000 0000 0000  ..zI............
0003f30: 0a07 7a49 cb12 0f00 0300 0000 0a45 0000  ..zI.........E..
0003f40: 0a07 7a49 d212 0f00 0300 0100 5322 0000  ..zI........S"..
0003f50: 0a07 7a49 d412 0f00 0000 0000 0000 0000  ..zI............
0003f60: 0a07 7a49 2532 0f00 0300 0000 2145 0000  ..zI%2......!E..
0003f70: 0a07 7a49 3832 0f00 0300 0100 0c22 0000  ..zI82......."..
0003f80: 0a07 7a49 3c32 0f00 0000 0000 0000 0000  ..zI<2..........
0003f90: 0b07 7a49 602e 0000 0100 4001 0000 0000  ..zI`.....@.....
0003fa0: 0b07 7a49 6a2e 0000 0300 2800 0a00 0000  ..zIj.....(.....
0003fb0: 0b07 7a49 6c2e 0000 0000 0000 0000 0000  ..zIl...........





Touch Tablet :

Execute the command (in my case, change the device to match your machine)
$ sudo xxd /dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-

and touch the screen.  Large amounts of output should come streaming onto your terminal with lots of incomprehensible characters.

e.g. :

0000f00: ee05 7a49 441d 0500 0300 0000 fa09 0000  ..zID...........
0000f10: ee05 7a49 4c1d 0500 0300 0100 2e09 0000  ..zIL...........
0000f20: ee05 7a49 4f1d 0500 0000 0000 0000 0000  ..zIO...........
0000f30: ee05 7a49 6e3c 0500 0300 0000 080a 0000  ..zIn<..........
0000f40: ee05 7a49 773c 0500 0300 0100 7609 0000  ..zIw<......v...
0000f50: ee05 7a49 7a3c 0500 0000 0000 0000 0000  ..zIz<..........
0000f60: ee05 7a49 ba5b 0500 0300 0000 150a 0000  ..zI.[..........
0000f70: ee05 7a49 c45b 0500 0300 0100 bf09 0000  ..zI.[..........
0000f80: ee05 7a49 c85b 0500 0000 0000 0000 0000  ..zI.[..........
0000f90: ee05 7a49 d717 0600 0100 4d01 0000 0000  ..zI......M.....
0000fa0: ee05 7a49 e317 0600 0000 0000 0000 0000  ..zI............
0000fb0: ee05 7a49 ee36 0600 0100 4a01 0000 0000  ..zI.6....J.....
0000fc0: ee05 7a49 f836 0600 0000 0000 0000 0000  ..zI.6..........





== Configuring X by hand ==

This applies directly to the tx2635, and maybe generally to USB tablets.  I do not know whether it will work on other tablets.

See my xorg.conf above, and replace the lines with the device paths discovered in the section about "Testing that the paths...".

Close your programs and restart x with a ctrl-alt-backspace key combination.

Hopefully, you can now use the stylus OR your finger to move the mouse around.


== Calibrating the wacom tablet ==

Execute the command :

$ wacomcpl

If the wacom devices are successfully installed, detected and installed for X-Windows, they will appear in a column on the left.  Follow the GUI prompts to calibrate the device.

I cannot get my finger touch pointer precise enough to use the program menus.


== Testing pressure sensitivity with GIMP ==

Start GIMP by going to 
Applications -> Graphics -> GIMP Image Editor

From the main window menu, click
File -> New
and just use the defaults to create a new file.

Now, enable the sensitivity to touch by opening the preferences from the menu :
Edit -> Preferences
choose :
Input Devices
and click the button :
Configure extended input devices

Select through the devices labeled "sylus", "eraser" and "touch" and set them from "disabled" to "screen".

Save the settings.

Now, select a pressure sensitive tool like the airbrush from the pallette (or press "a") and try to paint some lines with different pressures.  You should see nice gradations depending on how much pressure you apply.  Hooray!

If not, try to adjust the pressure settings with wacomcpl and the GIMP preferences.

---

### Post by oznozz on 2009-01-26
This is rather long.  Hopefully, it is helpful to people.  I have tried to provide some output and information that might help anyone unfamiliar with the particular bits of Ubuntu Linux that this addresses figure out what is happening.

Fair Warning : I'm not very often able to respond to anything and may not actually ever update this.

---

### Post by oznozz on 2009-01-28
I upgraded to the 2.6.27 kernel this morning.  So far, my tablet has not started working.  whenever I figure out how to make it work, I'll post a link or instructions.

---

### Post by oznozz on 2009-01-28
This is a hack solution.  It will probably break your computer.  Things 'work' but not 'correctly'.

$ sudo aptitude update
$ sudo aptitude install wacom-tools xserver-xorg-input-wacom
$ cd linuxwacom-0.8.2-2/
$ sudo make install
<restart>

Now, the stylus works OK as a mouse, instead of not working at all.  (if not, try re-copying the wacom.ko ).

Problems : Touch is completely non-functional. I didn't remove the wacom packages, so I might have drivers fighting or something.  None of the devices output anything through xxd, which seems a bit wrong to me.

I don't have time to come up with a better solution at the moment.

---

### Post by Favux on 2009-01-28
Hi oznozz,

The kernel driver you compiled (wacom.ko) is kernel specific.  Every time you update the kernel you break it.  You need to recompile it up to and including the step where you copy it to the appropriate directory.

You shouldn't have to recalibrate through wacomcpl, your current .xinitrc should be fine.

And you're right.  According to the LWP the wacom tools should be the same version as the driver, otherwise you risk breaking X.

---

### Post by oznozz on 2009-01-29
Correction : I upgraded from the 2.6.27-9 kernel to the 2.6.27-11 kernel.  I'm not sure how that changes the game, but I noticed that the build for linuxwacomproject is specific only to the 3rd designator of the kernel (here, the .27 part, not the -9 or -11 part.)

I hate this kind of problem.  It's the "intermittent" kind.

As in, my tablet is functional sometimes.  Not always the touch, not always the stylus, sometimes both, and other times not either one.

when I booted this morning, the touch was working.  then the headers updated, and things stopped working.  I tried rebuilding everything and restarting a couple times, but to no avail.

Notes for people : I noticed that installing or purging the wacom-tools and xserver-xorg-input-wacom causes the hald to restart.  Perhaps there is a way to "hotplug" the USB tablet by restarting hald or hald/X.

Favux, wacomcpl -- I was just using wacomcpl to see whether or not the tablet was being detected.  It's strange.  The kernel module is loaded, but at least half the time, the tablet is not being handled correctly, and sometimes X doesn't even acknowledge its existence.  So far, I like Linux and serial tablets (I wore out an HP TC1100) and I dislike USB tablets.

I also tried to convince media player to stop flickering videos like a dying fluorescent tube.  Someone on suggested running gstreamer-properties and setting the video output to X Window System, which seems to work.  However, do it under your account and not as sudo/root.  I don't have any gripes about the performance of this solution at the moment.  Keep in mind that this particular machine has an ATI video card.

---

### Post by oznozz on 2009-01-31
Update on the 2.6.27-9 to 2.6.27-11 upgrade and the behavior of the wacom tablet :

My conclusion from the last couple days is that sometimes the tablet is not initialized when the computer starts up.

I don't know if the tablet drivers actually *must* be recompiled.

Should the tablet not work, do the following :

# restart the hal demon, which I believe is equivalent to hotplugging your USB devices
$ sudo /etc/init.d/hal restart
# resart the X server
ctrl-alt-backspace

This has been the most reliable way to recover touch and stylus functionality yet.

If anyone very clever wants to figure out a test to discover the status of the tablet and then restart hal as appropriate in the xsession45 script (that's what it is in KNOPPIX, I'm not sure exactly how X starts in Ubuntu), that might be very helpful.

---

### Post by oznozz on 2009-02-04
A note for people using Mixxx users : Turning off Compiz effects in System -> Preferences -> Appearances and selecting None prevents the scrolling waveform display from flickering like crazy.  This might work for video in general, but I haven't tried it yet.  I guess this because the effect was almost identical to the problems I saw in Media Player.

A note for Windows users installing side-by-side : I usually use the windows disk utilities to resize my disks because if MS screws up, it's their fault.  I have noticed that Vista severely hogs the disk unless the equivalent of Restore Points are turned off.
Microsoft says to :
=====quote======
"1. 	

Open System by clicking the Start button Picture of the Start button, clicking Control Panel, clicking System and Maintenance, and then clicking System.
2. 	

In the left pane, click System Protection. Administrator permission required If you are prompted for an administrator password or confirmation, type the password or provide confirmation.
3. 	

To turn on System Protection for a hard disk, select the check box next to the disk, and then click OK.
– or –
To turn off System Protection for a hard disk, clear the check box next to the disk, and then click OK."
from 
[http://windowshelp.microsoft.com/Windows/en-us/help/f0688925-5abe-4caf-b49a-018f8cfcaf4d1033.mspx#E3](http://windowshelp.microsoft.com/Windows/en-us/help/f0688925-5abe-4caf-b49a-018f8cfcaf4d1033.mspx#E3)
=====end quote======


Further info about the tablet not connecting on startup : 
I read about a problem somewhere where gdm sometimes doesn't let hal get started all the way.  I followed some instructions somewhere in the Ubuntu docs or forums to re-order the boot priorities of hal and gdm (the gnome manager).  The steps were :
sudo update-rc.d -f gdm remove
sudo update-rc.d gdm defaults 25
It doesn't work all the time, but the tablet is more reliably available.

I'm trying to work on a little bash code to paste into the X startup scripts somewhere which will test whether the tablet devices are working, but I haven't figured it out yet.


For ras98, my /home/<user>/.xinitrc has all these settings for the tablet sensitivity.  It's not tweaked but it does work pretty well :
xsetwacom set stylus Suppress "2"
xsetwacom set stylus RawSample "4"
xsetwacom set stylus ClickForce "6"
xsetwacom set stylus PressCurve "0 0 100 100"
xsetwacom set eraser bottomy "16525"
xsetwacom set eraser bottomx "26332"
xsetwacom set eraser topy "-93"
xsetwacom set eraser topx "354"
xsetwacom set stylus bottomy "16525"
xsetwacom set stylus bottomx "26332"
xsetwacom set stylus topy "-93"
xsetwacom set stylus topx "354"
xsetwacom set touch bottomy "4061"
xsetwacom set touch bottomx "4090"
xsetwacom set touch topy "0"
xsetwacom set touch topx "56"
xsetwacom set eraser Button1 "Button 1"
xsetwacom set stylus TPCButton "on"
xsetwacom set stylus Button3 "Button 3"
xsetwacom set stylus Button2 "Button 2"
xsetwacom set stylus Button1 "Button 1"

In GIMP : I noticed that trying to change the sensitivity to pressure doesn't work as I would have expected, so I'm using these settings in GIMP, and adjusting the touch sensitivity with wacomcpl.

GIMP is located in :
Applications -> Graphics -> GIMP Image Editor

Settings in GIMP are located in :
<Main Menu> Edit -> Preferences 
click "Configure extended input devices"

all my tablet devices (stylus, eraser, touch) are set like this, using stylus as an example :

device : stylus
mode : screen
axes -- X : 1
axes -- Y : 2
axes -- Pressure : 3
axes -- X tilt : 4
axes -- Y tilt : 5
axes -- Wheel : 6
keys : all set to "(disabled)"

I think the numbers refer to some subdevice, but I don't know.  I believe that because (1) only one of the options for any device can be set to any number and (2) setting the numbers to anything but the above results in bizarre behaviors.

---

