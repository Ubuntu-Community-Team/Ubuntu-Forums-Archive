---
title: "Getting stuff to work on a tablet"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by thebrownhaze on 2007-08-09
I have an HP TC110 tablet which I have installed Ubuntu on to.  It required a little messing around to get the bits working, so I thought I would post what I did here in case its of any use to anyone else.

Firstly, the installation.  I don&#8217;t have a CD drive for this machine, so I installed Ubuntu using [WUBI]("http://wubi-installer.org/"), the windows installer that installs Ubuntu in to some sort of a virtual disk, thereby not affecting the format of your disk, or  changing windows at all.  Its very easy to use, but be warned, the suspend and hibernate features will not work using this. 

Ubuntu installed fine and most stuff worked straight away, including the wireless network card and the radio stylus.  Some stuff didn&#8217;t work, here is a run-through of what didn&#8217;t work and how I fixed it.

**problem**: While the stylus would move the pointer around the screen and I could use the &#8220;right mouse button&#8221; (i.e. clicking on stuff), the &#8220;left mouse button&#8221; (i.e. the little sift key on the side of the pen), did not produce the correct effect (i.e. making menus appear)

**solution**:To resolve this I entered the command:

[FONT="Courier New"]sudo xsetwacom set stylus Button3 "button 3"[/FONT]

note: This may only apply to the button mappings on the pen for an HP TC1100, you may need to play around with the button configs to get it right for your tablet. 

**Problem:** The soft keys (the ones that you touch with the stylus to use), including the button used to change the orientation of the screen form landscape to portrait. 

**Solution:** Firstly I worked out the command to rotate the screen from landscape to portrait:

[FONT="Courier New"]xrandr -o left[/FONT]

and then portrait to landscape:

[FONT="Courier New"]xrandr -o normal[/FONT]

When you change the orientation of the screen, you have to tell the stylus to change its orientation too, otherwise, when you move the pen left, your pointer will go up.  This can be done with the following commands:

landscape to portrait:

[FONT="Courier New"]xsetwacom set "stylus" Rotate 2[/FONT]

portrait to landscape:

[FONT="Courier New"]xsetwacom set "stylus" Rotate 0[/FONT]

I then crated to litte shell scripts that looked like this:

Title = Portrait.scp:
[FONT="Courier New"]xrandr -o left
xsetwacom set "stylus" Rotate 2[/FONT]

Title = landscape.scp
[FONT="Courier New"]xrandr -o normal
xsetwacom set "stylus" Rotate 0[/FONT]

Once these files where created and the permissions set so they could be run, I mapped them to the &#8220;tab&#8221; and &#8220;q menu&#8221; buttons&#8217; on the side of the tablet.  I did this with the &#8220;keyboard shortcuts&#8221; applet from the system > preferences menu.

**Problem:** The onscreen keyboard button no longer works.

**Solution:** its not perfect, but I use the &#8220;on-board&#8221; on screen keyboard, get it like this:

[FONT="Courier New"]Sudo apt-get install onboard[/FONT]

This does have on major flaw, if you want to do anything that requires root access, the root password box takes over the whole screen, I have not found a way to enter the password in to this box with an onscreen keyboard, as yet.  If you have , please let me know.  Also, I don&#8217;t have any spare buttons to map this to, so it has to be brought up from the applications menu, or from its icon on the application tray.

**Problem:** you have to unlock your default key ring to use wireless networking.  The is because it encrypts your WEP or WPA password (which is good) but you don&#8217;t what to have to type this in each time you reboot.  

**Solution: **Below is an article that shows you how to get around this, assuming that your login password is the same as your key ring password.  I haven&#8217;t go this working either, but I would be interested to hear if you have.

[http://ubuntuforums.org/showthread.php?t=192281](http://ubuntuforums.org/showthread.php?t=192281)

I love using Ubuntu on my tablet, its nice to know that you can causally surf in relative safety, and my other half loves to play majong tiles with the stylus.

I am far from Linux expert, but if you have had problems with your tablet, I hope this is of some use.

---

### Post by robnz on 2007-09-30
Hi there, which screen driver are you using? I can't get my tc1100 to rotate. xrandr reports no rotations possible.
Rob

UPDATE: Disregard my question. The solution was to add the following line to the nvidia device section in /etc/X11/xorg.conf
```
Option "RandRRotation" "true"
```

---

### Post by robnz on 2007-10-01
Here's a single script to toggle between portrait and landscape modes.
```
#!/bin/sh
# Script created to toggle screen orientation on a Compaq TC1100 tablet
# Adapted by Rob Stockley from code found at
# http://www.koders.com/noncode/fidF6152D1225924664BF30DC6977DCD1E697FACD61.aspx
if [ -n "$(xrandr | grep rotation | grep left)" ]
then
xrandr -o normal
xsetwacom set "stylus" Rotate 0
else
xrandr -o left
xsetwacom set "stylus" Rotate 2
fi
```
Note that for this to work you'll need the following sections in /etc/X11/xorg.conf
```
...
Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/input/wacom"
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  option "Button2" "3" # Maps button on side of pen to RMB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/input/wacom"
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  option "Button2" "3" # Maps button on side of pen to RMB
EndSection
```
And in the ServerLayout section you need these lines
```
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
```
BTW I'm still struggling to get the three pen buttons, left of the screen working.

---

### Post by bezkarl on 2007-10-01
Hi- I have followed all the above instructions, but my problem is the stylus isn't recognised and hasn't been since I installed Ubuntu 7. It's interesting to see the device automatically recognised by another user.
I'm pretty inexperienced in the use of any Linux OS's- is there anything I should be checking to see if the device is functional?
Many thanks

---

### Post by robnz on 2007-10-01
Make sure you have the following packages installed
```
wacom-tools
xserver-xorg-input-wacom
nvidia-glx
nvidia-kernel-common
```
You don't need the Nvidia drivers to make the stylus work but they are required to rotate the screen. If you have these then post the output of the following command
```
$ grep -i wacom /var/log/Xorg.0.log
```
You should get something like this
```
rob@rob-laptop:~$ grep -i wacom /var/log/Xorg.0.log
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
(II) Wacom driver level: 47-0.7.7-7 $
(**) stylus device is /dev/input/wacom
(**) WACOM: suppress value is 2
(**) cursor device is /dev/input/wacom
(**) WACOM: suppress value is 2
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/wacom"
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom General ISDV4 tablet speed=9600 maxX=21240 maxY=15980 maxZ=255 resX=2540 resY=2540 suppress=2 tilt=disabled
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=21240 bottom Y=15980
(==) Wacom device "cursor" top X=0 top Y=0 bottom X=21240 bottom Y=15980
rob@rob-laptop:~$
```

---

### Post by bezkarl on 2007-10-02
Thank you for your reply robnz. All packages are installed, but the Xorg.0.log shows this:-

(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
(II) Wacom driver level: 47-0.7.7-7 $
(**) stylus device is /dev/input/wacom
(**) WACOM: suppress value is 2
(**) cursor device is /dev/input/wacom
(**) WACOM: suppress value is 2
(**) eraser device is /dev/input/wacom
(**) WACOM: suppress value is 2
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
Error opening /dev/input/wacom : Success

It appears to be a problem opening the serial ports- any thoughts?
Many thanks.

---

### Post by robnz on 2007-10-02
Make sure that /dev/input/wacom exists and that it points to the correct serial port.
```
rob@rob-laptop:~$ ls -l /dev/input/wacom
lrwxrwxrwx 1 root root 10 2007-10-03 06:53 /dev/input/wacom -> /dev/ttyS0
```
If that looks okay then try reading data directly from the serial port. Run the xxd command then try using the stylus. You should get something like this. Use ctrl-c to end.
```
rob@rob-laptop:~$ xxd /dev/ttyS0
0000000: a00c 0208 4e00 7000 00a0 0c01 084e 0050  ....N.p......N.P
0000010: 0000 a00c 0208 4e00 5000 00a0 0c03 084e  ......N.P......N
0000020: 0028 0000 a00c 0508 4e00 2800 00a0 0c07  .(......N.(.....
0000030: 084e 0048 0000 a00c 0a08 4e00 4800 00a0  .N.H......N.H...
...
...and lots more...
...
```
Don't be surprised if the console appears to hang after you hit ctrl-c. Just keep using the stylus and eventually the buffer will clear.
No need to post the output just let us know if you got some output.

---

### Post by bezkarl on 2007-10-02
Thank you again- will give your suggestions a go asap.

---

### Post by bezkarl on 2007-10-03
ls -l /dev/input/wacom did not tell me the serial port 
(**-rw-r--r-- l root root 2 2007-10-03 09:02 /dev/input/wacom**), and the xxd command did provide output although not the same as above- I'm beginning to suspect the hardware is dodgy?

---

### Post by robnz on 2007-10-03
I'm guessing that you got the output on /dev/ttyS0 and not /dev/input/wacom. If that is the case then edit /etc/X11/xorg.conf and update the stylus and cursor inputdevice sections to reflect the device that responded using xxd. While you're there you can comment out the eraser section as the tc1100 pen doesn't have one.

When you've done that restart the xserver (ctrl-alt-backspace) and try the pen.

---

### Post by bezkarl on 2007-10-03
My Xorg.conf is pointing to /dev/input/wacom but when I commented out my eraser and restarted the xserver the GDM failed to load. I believe the stylus is on /dev/ttyS0, but editing Xorg.conf to this effect does not make it work. I think I will call it a day!

---

### Post by robnz on 2007-10-03
My fault about the gdm lockup. I should have mentioned that you also need to comment out the eraser line in the ServerLayout section of xorg.conf. Either comment them out or leave them alone for now. 

Once you have your xorg.conf pointing to /dev/ttyS0 you can use the following command to see if the xserver is getting anything from the stylus.
```
rob@rob-laptop:~$ xidump stylus
```
You'll get something like this.
```
InputDevice: stylus
Valuators: Absolute   ID: Undefined  Serial Number: Undefined

             x-axis    y-axis   pressure   x-tilt    y-tilt     wheel
     data:
      min:  +00000    +00000    +00000    -00064    -00064    +00000
      max:  +21240    +15980    +00255    +00063    +00063    +01023
      res:  +02540    +02540    +00001    +00001    +00001    +00001


Proximity:
    Focus:
  Buttons:
     Keys:

```
Move the stylus around and some of the numbers should change. ctrl-c to close.

So far you've established that the stylus is on /dev/ttyS0 and that the kernel is passing on data from it. xidump will tell you whether the xserver is receiving that data.

---

### Post by bezkarl on 2007-10-15
No joy I'm afraid- xidump reports that the stylus is not recognised. 
I think the hardware must be broken as I've spent hours trying to get it work. 
I'm also having issues with upgrading the nVidia driver- the gdm fails to load using the restricted driver.
Any further help would be appreciated.
Thanks

---

### Post by robnz on 2007-10-15
Remake the changes to xorg.conf using /dev/ttyS0 and restart X. Expect GDM to lock up. When that happens press ctrl-alt-F1, login to the console and make a copy of the log and config using this command. 
```
$ cat /etc/X11/xorg.conf /var/log/Xorg.0.log | gzip > ~/x-setup.gz
```
Email me (rob dot stockley at mowgli dot net dot nz) the file x-setup.gz located in your home directory and I'll try to figure out what's going on. You can check the contents of what you're sending me using this command.
```
$ zcat x-setup.gz | less
```

---

### Post by bezkarl on 2007-10-17
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=469554&amp;highlight=tc1100](http://ubuntuforums.org/showthread.php?t=469554&amp;highlight=tc1100) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Managed to finally install the restricted Nvidia driver and avoid the gdm lockups, thanks to this forum, but in attempting to enable to screen to rotate the gdm fails to start and cannot undo changes causing this effect.
Therefore I'm starting again with a clean slate.
Thanks for the all the help.

---

