---
title: "Configuring Lenovo X61 Tablet for Lucid"
date: 2010-08-02
forum: Hardware
---

### Post by MES5464 on 2010-08-02
I want to start out by saying that Ubuntu 9.10 was perfect for my Lenovo X61 Tablet. Everything worked.

I have upgraded to 10.04 and I am having trouble configuring the stylus. The Wacom tablet (behind the screen) is detected and the stylus works, except all clicks (pen point, side button, eraser) as seen as right clicks.

I have reviewed the [Wacom]("https://help.ubuntu.com/community/Wacom") help and attempted to change my 10-wacom.conf file without any success. Currently my file looks like this:

```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
#	Option "KeepShape" "on"
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
#	Option "Button1" "1"
	Option "Button2" "3"
#	Option "Button3" "3"
EndSection
```

I tried moving the button options into the second and third section of the file without any success. I also used method 2 in the help but that didn't have an effect. The only device name it would accept was "Serial Wacom Tablet" but no behavior changed with the stylus.

I have the feeling that I am not far from getting this write, I just need some fresh eyes to help me see what I am doing wrong.

Any help would be appreciated.

---

### Post by Favux on 2010-08-02
Hi Marion,

You want to add the option to the serial snippet like so:
```
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
	Option "Button2" "3"
EndSection

```
Currently there is a limitation on 10-wacom.conf where you can only configure the main device (stylus), and not sub-devices like eraser and touch.  So it's probably better to set up a xsetwacom startup script specific for your tablet pc.

To do that we want to look at the output of 'xinput --list'.  How many stylus buttons?  It has an eraser, correct?  Does your X61 have touch?

---

### Post by MES5464 on 2010-08-02
This is the result of the xinput command:

```

marion@moroni:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Wireless Notebook Presenter Mouse 8000	id=9	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                     	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]


```

My stylus has the point (tip), a side button, and the eraser button (opposite end from tip). The screen only responds to the stylus, not a finger.

---

### Post by Favux on 2010-08-02
Hi MES5464,

Here's a first pass at what it would look like.  It's adapted from a HP TX2000 which is usb, but I think all the settings apply to a serial tablet pc too.

To set it up to auto-start, download the attached file, and rename it .xsetwacom.sh (or whatever you want) and place it in your home directory. Remember it will be a hidden file. To enable the xsetwacom commands in the .xsetwacom.sh file to apply to Xserver through a reboot you enter in a terminal:
```
chmod +x ~/.xsetwacom.sh

```
or you could right click on the file and in Properties, in the Permission tab, check Execute as program. Then go to System->Preferences->Startup Applications and click on add and for the command write "sh /home/yourusername/.xsetwacom.sh" (without the quotes). You can also change your settings on the fly using the xsetwacom parameters in a terminal. They only apply during the current session.

Once the script is executable you can double click on it to apply it's settings or reboot to check the auto-start set up.

I left the coordinates in in case you want/need to set them.  Yours would be different.  You can get the ballpark ones from Xorg.0.log in /var/log when the wacom drivers initialize your digitizer.

---

### Post by MES5464 on 2010-08-03
Favux, the file worked perfectly. Thank you. How do I tweak this so the right click doesn't fire until I tap the screen? Right now, if the stylus is hovering over the screen and I click the side button, the right click event fires. I thought the TPCButton would do that but I must be wrong.

---

### Post by Favux on 2010-08-03
Good!

You're right.  With TPCButton "on" it's suppose to be tip + side switch.  If "off" then you get hover mode or side switch only.  So it's not clear to me what is wrong.  Did you remove your other attempts at setting it?  The xsetwacom command should control but it wouldn't hurt.

---

