---
title: "QSynaptics won't work"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by dcalvani on 2007-06-12
hello

I've been trying to fix the touchpad/mouse problem (erratic+freezes when I'm on AC power) I've got on my Fujitsu-Siemens Lifebook S-6120 by downloading QSynaptics. 

This is the message I got on my Terminal when (after downloading) I type "qsnaptics":

XXXXX@Adab:~$ qsynaptics
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
users home is /home/XXXXX
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?

The QSynaptics windows appears at the same time. At the bottom of it I read two messages: "please install the synaptics touchpad driver" and "please enable X shared memory config in XF86Config". 

Please help! Thank you.

---

### Post by hardyn on 2007-06-12
some edits are required in your xorg.conf file... 

[http://ubuntu1501.blogspot.com/2007/04/configure-synaptic-touchpad-settngs.html](http://ubuntu1501.blogspot.com/2007/04/configure-synaptic-touchpad-settngs.html)

is a pretty good tutorial.

I found the action of the Qsynaptics to be somewhat irratic, i have opted not to use it, but use:

syndaemon -i1 -d -t

instead. i like it better.  the edits to the xorg. file are identical.  the above syntax may be added to the startup programs.

cheers.

---

### Post by Chrissss on 2007-06-14
Like you, i've got a FSC Lifebook S-6120. You need special boot options to get SHMConfig working. So open /boot/grub/menu.lst in a editor

# sudo gedit /boot/grub/menu.lst

an add inside the defoptions line the options i8042.reset i8042.nomux. It should look like this

```
...
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash i8042.reset i8042.nomux
...
```

After that execute

# sudo update-grub

To add those options to the kernel entries. After that edit /etc/X11/xorg.conf

# sudo gedit /etc/X11/xorg.conf

an replace the Section "InputDevice" with

```
...
Section "InputDevice"
        Driver "synaptics"
        Identifier "Synaptics TouchPad"
        Option "Device" "/dev/psaux"
        Option "SendCoreEvents" "true"
        Option "Protocol" "auto-dev"
        Option "LeftEdge" "130"
        Option "RightEdge" "840"
        Option "TopEdge" "130"
        Option "BottomEdge" "640"
        Option "FingerLow" "7"
        Option "FingerHigh" "8"
        Option "MaxTapTime" "180"
        Option "MaxTapMove" "110"
        Option "EmulateMidButtonTime" "75"
        Option "VertScrollDelta" "20"
        Option "HorizScrollDelta" "20"
        Option "MinSpeed" "0.60"
        Option "MaxSpeed" "1.10"
        Option "AccelFactor" "0.030"
        Option "EdgeMotionMinSpeed" "200"
        Option "EdgeMotionMaxSpeed" "200"
        Option "UpDownScrolling" "1"
        Option "CircularScrolling" "1"
        Option "CircScrollDelta" "0.1"
        Option "CircScrollTrigger" "2"
        Option "SHMConfig" "on"
        Option "Emulate3Buttons" "on"
EndSection
...
```
That's all :)

Christoph

---

### Post by dcalvani on 2007-06-14
Thanks tons Chrissss!!!

Now Qsynaptics works...except that - no matter what I try - whenever my Lifebook is on AC power, it's impossible to use the touchpad. The mouse either freezes or gets quite jumpy and erratic, and it makes it impossible to work. 

Do you have any idea on what I could do? Thank you again. 

> **Chrissss said:**
> Like you, i've got a FSC Lifebook S-6120. You need special boot options to get SHMConfig working. So open /boot/grub/menu.lst in a editor

# sudo gedit /boot/grub/menu.lst

an add inside the defoptions line the options i8042.reset i8042.nomux. It should look like this

```
...
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash i8042.reset i8042.nomux
...
```

After that execute

# sudo update-grub

To add those options to the kernel entries. After that edit /etc/X11/xorg.conf

# sudo gedit /etc/X11/xorg.conf

an replace the Section "InputDevice" with

```
...
Section "InputDevice"
        Driver "synaptics"
        Identifier "Synaptics TouchPad"
        Option "Device" "/dev/psaux"
        Option "SendCoreEvents" "true"
        Option "Protocol" "auto-dev"
        Option "LeftEdge" "130"
        Option "RightEdge" "840"
        Option "TopEdge" "130"
        Option "BottomEdge" "640"
        Option "FingerLow" "7"
        Option "FingerHigh" "8"
        Option "MaxTapTime" "180"
        Option "MaxTapMove" "110"
        Option "EmulateMidButtonTime" "75"
        Option "VertScrollDelta" "20"
        Option "HorizScrollDelta" "20"
        Option "MinSpeed" "0.60"
        Option "MaxSpeed" "1.10"
        Option "AccelFactor" "0.030"
        Option "EdgeMotionMinSpeed" "200"
        Option "EdgeMotionMaxSpeed" "200"
        Option "UpDownScrolling" "1"
        Option "CircularScrolling" "1"
        Option "CircScrollDelta" "0.1"
        Option "CircScrollTrigger" "2"
        Option "SHMConfig" "on"
        Option "Emulate3Buttons" "on"
EndSection
...
```
That's all :)

Christoph

---

### Post by dcalvani on 2007-06-14
Thank you so much hardyn!
Now, when I type syndaemon on my Terminal, I get a string Enabled Disabled...". I'm not sure the two things are connected, but the touchpad seems to work slightly better (but just slightly really) when syndaemon is running. You're saying the syntax syndaemon -i1 -d -t can be added to the start-up programs. How do you do that?


> **hardyn said:**
> some edits are required in your xorg.conf file... 

[http://ubuntu1501.blogspot.com/2007/04/configure-synaptic-touchpad-settngs.html](http://ubuntu1501.blogspot.com/2007/04/configure-synaptic-touchpad-settngs.html)

is a pretty good tutorial.

I found the action of the Qsynaptics to be somewhat irratic, i have opted not to use it, but use:

syndaemon -i1 -d -t

instead. i like it better.  the edits to the xorg. file are identical.  the above syntax may be added to the startup programs.

cheers.

---

### Post by Paul.Spectre on 2007-12-11
Chrisss
I too have a 6120 and tried the additional nomux and reset options but the touchpad is still not detected and SHMConfig is not being set. This is driving me nuts?
Do you have any other ideas?

---

