---
title: "Mouse Speed"
date: 2008-11-10
forum: Hardware
---

### Post by Yashiro on 2008-11-10
Just posting to de-mystify the settings in the [COLOR="Sienna"]Gnome Mouse Settings Applet[/COLOR].

Mice speed, accuracy and acceleration are all handled quite poorly in X.
For people coming from Windows this can be a bit confusing.

Traditionally, mice are controlled by the command. 
[COLOR="Green"]xset m <acceleration> <threshold>[/COLOR]
*Acceleration can accept fractional values of the format 67/100, 3/2, 5/9 etc.*

[COLOR="DimGray"]The acceleration parameter is a multiplier that is applied to the mouse cursor motion. 
If the acceleration parameter is set to ``4'', the mouse cursor moves across the screen four times faster than you move the mouse.

Setting a high acceleration is convenient for quickly moving the mouse cursor large distances on your screen. However, it can be awkward when you want to position the mouse precisely. 
The pointer can move too quickly and it becomes difficult to focus the mouse cursor on a small area on your screen. To overcome this problem, you can set the threshold parameter. 

The threshold controls the number of pixels the mouse cursor must move before the cursor motion accelerates.

For example, suppose you set an acceleration value of ``6'' and a threshold value of ``8''. 
The mouse is configured so that if you move the mouse cursor more than 8 pixels, the cursor can then move 6 times as fast on the screen as you actually move the physical mouse.[/COLOR]


To see your current xset mouse settings type [COLOR="Green"]xset -q | grep accel[/COLOR] in a terminal.

Now, in terms of the [COLOR="Sienna"]Gnome Mouse Settings Applet[/COLOR]:
A value set using a terminal command of "xset m 1 1" is equivalent to -

Acceleration Slider At half way. (This is 10/10, which is of course 1)
[====*====]

Sensitivity Slider Unmoved. (1)
[]

---

### Post by keith11 on 2008-11-29
Thank you for that informative post. I am still struggling to find a combination of the acceleration value, which I prefer somewhere between 4.5 to 5, and the threshold value. I don't know what the value for the threshold should be for that acceleration value so that the mouse cursor does not move in installments - when the mouse cursor moves, it moves with small stops in between, although it is not very apparent. I have Vista too on the same machine and I was wondering how I can get that kind of smoothness of the mouse cursor. Thanks.

Keith.

---

### Post by Yashiro on 2009-01-29
The following tips apply to the Logitech MX518 (c01e). Some/most should work on newer mice, but take care.
Some tips are obsolete depending on your build, but I include them for completeness.

_Setting the DPI_

Install **lomoco**. Add the following line to **/etc/rc.local**
> lomoco --pid=c01e -m --no-sms[I][SIZE="1"]lomoco deviceid dpi nocruisecontrol
lomoco --help to see other dpi settings.[/SIZE][/I]

This will set your mouse to 1200dpi and stop the cruise control buttons from acting on their own. 
Part of a general strategy to enable all the buttons on Hardy (with xmodmap and btnx)


_In your **xorg.conf**_

Set the Resolution in the Device section.
> Section "InputDevice"
	Identifier  "MX518 Optical Mouse"
	Driver      "evdev"
	Option	    "Name" "Logitech USB-PS/2 Optical Mouse"
	Option	    "AllowMouseOpenFail" "true"
	Option	    "VertScrollDelta" "12"
	**Option      "Resolution"    "1200"**
	Option	    "Emulate3Buttons" "false"
EndSection


_Modify USB polling rate. (2 methods)_

Add usbhid.mousepoll=1 to the kernel parameters for 1000Mhz polling.

> title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=ba636202-3275-45ed-b485-da35aa659c61  ro quiet splash vga=794 **usbhid.mousepoll=1**
initrd		/boot/initrd.img-2.6.24-23-generic

Change the value contained in **/sys/module/usbhid/parameters/mousepoll**
to 1.

In **/etc/rc.local**
> echo 1 > /sys/module/usbhid/parameters/mousepoll

Or try
> sudo -i
echo 1 > /sys/module/usbhid/parameters/mousepoll

---

### Post by electrogeist on 2009-01-29
You can have a more progressive transition into the acceleration using options like:
[LIST]
[*] xset m 11/8 0
[*] xset m 5/3 0
[/LIST]

To do this the <threshold> needs to be set to 0
> If the ‘threshold’ parameter is provided and 0, the ‘accelera&#8208;
tion’ parameter will be used in the exponent of a more natural
and continous formula, giving precise control for slow motion
but big reach for fast motion, and a progresive transition for
motions in between. Recommended ‘acceleration’ value in this case
is 3/2 to 2, but not limited to that range. 

Also see Endolith's post in this thread:
[INDENT]Re: Mimicking "Windows" Mouse Sensitivity
[http://ubuntuforums.org/showpost.php?p=6494978&postcount=4](http://ubuntuforums.org/showpost.php?p=6494978&postcount=4) [/INDENT]
And the man page for xset, about 2/3 of way down:
[INDENT][http://manpages.ubuntu.com/manpages/intrepid/en/man1/xset.1.html](http://manpages.ubuntu.com/manpages/intrepid/en/man1/xset.1.html)[/INDENT]

---

### Post by Yashiro on 2009-01-29
You can, yes. If you actually used acceleration in Windows then you'd probably feel more comfortable with some in Linux.
This does introduce the Linux weirdness into the behaviour though. Macs are similar in this regard.

Linearity without acceleration is what I prefer. Hence no artificial acceleration and just lots of mouse updates.

---

### Post by electrogeist on 2009-01-29
I am still on the fence as far as preference... maybe too many options ;)

---

