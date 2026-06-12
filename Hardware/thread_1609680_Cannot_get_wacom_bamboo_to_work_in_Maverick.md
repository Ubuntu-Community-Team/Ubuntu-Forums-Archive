---
title: "Cannot get wacom bamboo to work in Maverick"
date: 2010-10-30
forum: Hardware
---

### Post by doctordruidphd on 2010-10-30
I've burned out googling and experimenting on this, time for some experienced help:

I have a wacom bamboo "fun" (touch and pen) tablet.

I have followed all the instructions I can find, about downloading the drivers from linuxwacomproject, and building and installing wacom.ko.

First problem: The documentation says that I should 
NOT be getting a "wacom: v1.52-pc-0.3:USB Wacom tablet driver" message for the tablet in dmesg, that this is the driver shipped with the kernel, not the one I built. I built the driver, moved wacom.ko into /lib/modules/2.6.35-23-generic/kernel/drivers/input/tablet/wacom.ko, ran sudo depmod -a, even did an update-initramfs -u.

I still get that message.

Second problem: I followed the instructions about setting up /usr/share/X11/xorg.conf.d/50-wacom.conf.
Nothing happens when I plug the pad (USB) in; I do get a message in demsg, but the pad does not work. I have to reboot, with the pad plugged in, for it to work.

I also tried making the changes in /etc/X11/sorg.conf as stated on the linuxwacomproject howto. Makes no difference.

Third problem: after installing the stuff from linuxwacomproject, wacomcpl does not work. I can see the stylus and eraser options, but selecting either one brings up an error message: "Error:W Error: 2 Bad Value (integer p..."

There is no wacom-tools package for maverick in the repositories, that I have been able to find. Several websites say to use this. OK, how?

I do not think the tablet and/or driver are working properly.  I am actually using kde, and the kde configuration too for the wacom tablet says it cannot detect a tablet.


Fourth problem: I cannot configure the buttons, stylus, etc, nor can I see anything anywhere to configure them.  I GIMP, the eraser acts just like the stylus -- it paints, does not erase, and I can't see how to confuigure its behavior.

Well, this is a mess. The tutorials all assume their advice works, and it isn't working here.

HELP!!

---

### Post by Favux on 2010-10-30
Hi doctordruidphd,

Please see the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  It works in Maverick and shows you how to configure using a xsetwacom script.  xf86-input-wacom does not include wacomcpl.

---

### Post by doctordruidphd on 2010-10-30
Thank You for your reply, but still no joy.
Something has gone wrong somewhere. The first time I ran this, I rebooted with the pad plugged in. All four options listed in 50-wacom.conf were listed, but I got the same error messages as below. I unplugged and reinserted the pad, and then only two of the devices (pad and eraser) were detected.
xwacomsetup.sh can't find any of the devices.

Thaks for any help you can give in sorting this out.

The output of dmesg after plugging the pad back in is:
------------------------------------
[  977.561274] usb 2-6: new full speed USB device using ohci_hcd and address 6
[  977.805283] input: Wacom BambooFun 2FG 4x5 Pen as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input9
[  977.845273] input: Wacom BambooFun 2FG 4x5 Finger as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.1/input/input10
-------------------------------------

Here is /usr/share/X11/xorg.conf.d/50-wacom.conf:

-------------------------------------------
Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#       MatchProduct "Wacom|WALTOP|WACOM"
        MatchProduct "Wacom|WACOM|Hanwang"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom eraser class"
        MatchProduct "Wacom"
        MatchProduct "eraser"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "eraser"
  Option        "USB"           "on"
EndSection

Section "InputClass"
        Identifier "Wacom stylus class"
        MatchProduct "Wacom"
        MatchProduct "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
EndSection

Section "InputClass"
        Identifier "Wacom pad class"
        MatchProduct "Wacom"
        MatchProduct "pad"
  Option        "Device"        "/dev/input/wacom-touch"
  Option        "Type"          "pad"
  Option        "USB"           "on"
EndSection

Section "InputClass"
        Identifier "Wacom touch class"
        MatchProduct "Wacom"
        MatchProduct "touch"
        Option  "Device"        "/dev/input/wacom-touch"
        Option  "Type"  "touch"
        Option "USB" "on"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001|N-Trig Pen"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
#       Option "Button2" "3"
EndSection
--------------------------------------------------

Here is xinput --list:
---------------------------------------
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen eraser        id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger pad        id=10   [slave  pointer  (2)]
&#9116;   &#8627; Microsoft SideWinder™ Mouse               id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Chicony Saitek Eclipse Keyboard           id=13   [slave  keyboard (3)]
    &#8627; Chicony Saitek Eclipse Keyboard           id=14   [slave  keyboard (3)]
-------------------------------------------

Here is xsetwacom list:
-------------------------------------------

Wacom_BambooFun_2FG_4x5_Pen_eraser     eraser
Wacom_BambooFun_2FG_4x5_Finger_pad     pad
----------------------------------------------

And here is the result of running the xsetwacom.sh for 50-wacom.conf:
--------------------------------------------
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '9'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '9'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '9'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '9'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '9'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '9'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '9'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '9'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '9'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '8'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '8'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '8'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '8'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '8'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '8'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '10'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '10'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '10'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '10'
------------------------------------

---

### Post by Favux on 2010-10-30
First 50-wacom.conf is different from xorg.conf.  You can't define each device in it.  It won't configure dependent devices.  So remove:
```
Section "InputClass"
Identifier "Wacom eraser class"
MatchProduct "Wacom"
MatchProduct "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "USB" "on"
EndSection

Section "InputClass"
Identifier "Wacom stylus class"
MatchProduct "Wacom"
MatchProduct "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "USB" "on"
EndSection

Section "InputClass"
Identifier "Wacom pad class"
MatchProduct "Wacom"
MatchProduct "pad"
Option "Device" "/dev/input/wacom-touch"
Option "Type" "pad"
Option "USB" "on"
EndSection

Section "InputClass"
Identifier "Wacom touch class"
MatchProduct "Wacom"
MatchProduct "touch"
Option "Device" "/dev/input/wacom-touch"
Option "Type" "touch"
Option "USB" "on"
EndSection

```
Then after a reboot repeat 'xinput --list' so we see what you have.  The xsetwacom commands you are using are incorrect.

---

### Post by doctordruidphd on 2010-10-31
Thanks for your reply. I really appreciate the help.

Did as you suggested. Here is 50-wacom.conf:
-------------------------------------
Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#       MatchProduct "Wacom|WALTOP|WACOM"
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
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
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
-----------------------------------------

Here is xinput --list:
---------------------------------------
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen eraser        id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen stylus        id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger pad        id=10   [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger touch      id=11   [slave  pointer  (2)]
&#9116;   &#8627; Microsoft SideWinder&#8482; Mouse               id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Chicony Saitek Eclipse Keyboard           id=13   [slave  keyboard (3)]
    &#8627; Chicony Saitek Eclipse Keyboard           id=14   [slave  keyboard (3)]
--------------------------------------

And xsetwacom list:

--------------------------------------
Wacom_BambooFun_2FG_4x5_Pen_eraser     eraser
Wacom_BambooFun_2FG_4x5_Pen_stylus     stylus
Wacom_BambooFun_2FG_4x5_Finger_pad     pad
Wacom_BambooFun_2FG_4x5_Finger_touch     touch
--------------------------------------

Looks like we are getting somewhere.
The xsetwacom.sh I am using is the one that comes from "Favux_Sample_Bamboo-P&T_xsetwacom-scripts.tar.gz" , and the file "Favux_wacom.conf-.xsetwacom.sh" as listed on the howto.

Edit: OK, looks like to get xsetwacom to work, I can't use id numbers, I have to use the verbose device_name. Commands are now working.

Any quick pointers how to get the eraser to erase in gimp?  I'm still lost on that one. Thanks.

---

### Post by Favux on 2010-10-31
Alright, looks like you're almost there.  You need to use the "Device names" that 'xinput --list' returns in the xsetwacom commands.  So:

stylus = "Wacom BambooFun 2FG 4x5 Pen stylus"

eraser = "Wacom BambooFun 2FG 4x5 Pen eraser"

touch = "Wacom BambooFun 2FG 4x5 Finger touch"

pad = "Wacom BambooFun 2FG 4x5 Finger pad"

So where you'd use to use stylus in an xsetwacom command you now use "Wacom BambooFun 2FG 4x5 Pen stylus" with the quotes.  So just go through the .xsetwacom.sh and make sure the "Device names" are correct.

---

### Post by Favux on 2010-10-31
> Any quick pointers how to get the eraser to erase in gimp? I'm still lost on that one.
Point the eraser end to the little eraser icon on the floating tool bar.  After it selects eraser then Save the assignment.

---

### Post by doctordruidphd on 2010-10-31
Great! Thanks very much for your help. I guess mostly some things I didn't understand from the howto.
It's working just fine now. Thanks again!

---

### Post by doctordruidphd on 2010-10-31
Looks like there are still some problems with xsetwacom.

The following command does not work:
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_stylus" PressCurve "0 0 100 100"

produces this output:
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Pen_stylus value for 'PressCurve'

I tried to get the value for PressCurve, with the following results:

greenman@Wolfenstein:~$ xsetwacom -s get "Wacom_BambooFun_2FG_4x5_Pen_stylus" PressCurve
xsetwacom set Wacom_BambooFun_2FG_4x5_Pen_stylus PressCurve "0 0 0 1"

That can't be right.

Here's another that doesn't work:

greenman@Wolfenstein:~$ xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_touch" ZoomDistance "50"  # default is 50
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Finger_touch value for 'ZoomDistance'


Also, I'm trying to set button 4 to the escape key, and can't get that right either:
xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_pad" Button4 "key escape"
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Finger_pad value for 'Button4'

I also tried "core key escape" as described on the linuxwacomproject howto, same result.

---

### Post by Favux on 2010-10-31
For escape either esc, Esc, or Escape should work.

Not sure what's going on.  There may have been a problem with xsetwacom during the install.

Don't use "core", that's been deprecated.

---

### Post by doctordruidphd on 2010-10-31
I have tried both with and without the quotes:

greenman@Wolfenstein:~$ xsetwacom -s get Wacom_BambooFun_2FG_4x5_Pen_stylus PressCurve
xsetwacom set Wacom_BambooFun_2FG_4x5_Pen_stylus PressCurve "0 0 0 1"
greenman@Wolfenstein:~$ xsetwacom -s get "Wacom_BambooFun_2FG_4x5_Pen_stylus" PressCurve
xsetwacom set Wacom_BambooFun_2FG_4x5_Pen_stylus PressCurve "0 0 0 1"

and for the escape key:

greenman@Wolfenstein:~$ xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_pad" Button4 "key Esc"
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Finger_pad value for 'Button4'
greenman@Wolfenstein:~$ xsetwacom set Wacom_BambooFun_2FG_4x5_Finger_pad Button4 "key Esc"
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Finger_pad value for 'Button4'
greenman@Wolfenstein:~$ xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_pad" Button4 "key Escape"
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Finger_pad value for 'Button4'
greenman@Wolfenstein:~$ xsetwacom set Wacom_BambooFun_2FG_4x5_Finger_pad Button4 "key Escape"
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Finger_pad value for 'Button4'

---

### Post by Favux on 2010-10-31
The default 0.10.8 xf86-input-wacom in Maverick should handle these xsetwacom commands fine.  So first go to Synaptic Package Manager and find xserver-xorg-input-wacom and tell Synaptic to reinstall it and reboot.

Are there any changes you made you haven't mentioned?

---

### Post by doctordruidphd on 2010-10-31
I tried reinstalling xerver-xorg-input-wacom. 
Same error problems, can't set the key or presscurve, same erroneous values for presscurve.

From the steps on the howto at
[http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1)
I followed these:

1. Downloaded and unpacked linuxwacom-0.8.8-10, 

./configure --enable-wacom --prefix=/usr

make

sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

It did in fact replace wacom.ko with the newly compiled one.
HOWEVER, after rebooting with the tablet plugged in, I get the following in dmesg:
[   28.580552] usbcore: registered new interface driver wacom
[   28.580555] wacom: v1.52-pc-0.3:USB Wacom tablet driver
Somewhere on the linuxwacomproject site, it says that 1.52 is the generic driver included with the kernel, not the compiled one. So I did a locate wacom.ko, removed all of the ones I sould find, and recopied the compiled one. Also did update-initramfs -u. Didn't make any difference.

Next, I setup 50-wacom.conf, which I corrected with your information.

I also tried using the procedure for installing the git-clone xf86-input-wacom, but that didn't help either.  Reinstalling xserver-xorg-input-wacom should have overwritten that anyway.

I also tried using the procedures for setting up with xorg.conf, but that didn't work either. I have since reverted back to the original xorg.conf.

One other thing I tried was installing the prebuild stuff from the linuxwacom package. The wacomcpl application gives an error message "Error: Xerror: 2 Bad Value" message if I click on the stylus or eraser options.

---

### Post by Favux on 2010-10-31
If the tablet works at all you know it's running on the compiled wacom.ko.  So don't worry about that.

Unless something got left over after you overwrote it it looks like everything is fine.

So I don't understand what's wrong.  Your tablet works OK in Windows (to rule out a hardware problem)?

We may have to clone the xf86-input-wacom git repository (step II.) and see if that fixes things.


Did you check 'xinput --list' again to make sure nothings changed?

---

### Post by doctordruidphd on 2010-10-31
Thanks for your reply. It really is driving me batty.

I don't have windows to test with; the only windows is in virtualbox, and I suspect that will open a whole new can of worms.

I will go through the git repository stuff again, and report back.

---

### Post by doctordruidphd on 2010-10-31
OK, I followed the steps in II., inclduing installing the x macros, and installing the stuff from the git repository. No luck, same error messages.

Funny thing is, the other commands, like setting Button1 "1", work without error, and **xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_touch" Gesture "on"** do work. The ones that don't work, from xsetwacom.sh, are:

greenman@Wolfenstein:~$ ./xsetwacom.sh
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Pen_stylus value for 'PressCurve'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Pen_eraser value for 'PressCurve'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Finger_touch value for 'ZoomDistance'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Finger_touch value for 'TapTime'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Finger_pad value for 'Button4'

Which. besides the key, are the ones involved in setting some numerical value. Could there be a problem with the xsetwacom program? I notice it comes from xserver-xorg-input-wacom, but reinstalling that doesn't seem to have helped.

---

### Post by Favux on 2010-10-31
I don't know what's wrong.

Show me your current 'xinput --list' output and attach your current .xsetwacom.sh to your next post.

A bug could have been just introduced to xf86-input-wacom I suppose.  But then you'd think the reinstall of the default through Synaptic would have fixed it.

---

### Post by doctordruidphd on 2010-10-31
greenman@Wolfenstein:~$ xinput --list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft SideWinder&#8482; Mouse               id=12   [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen eraser        id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen stylus        id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger pad        id=10   [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger touch      id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Chicony Saitek Eclipse Keyboard           id=13   [slave  keyboard (3)]
    &#8627; Chicony Saitek Eclipse Keyboard           id=14   [slave  keyboard (3)]

xsetwacom list:
greenman@Wolfenstein:~$ xsetwacom list
Wacom_BambooFun_2FG_4x5_Pen_eraser     eraser
Wacom_BambooFun_2FG_4x5_Pen_stylus     stylus
Wacom_BambooFun_2FG_4x5_Finger_pad     pad
Wacom_BambooFun_2FG_4x5_Finger_touch     touch


.xsetwacom.sh:

greenman@Wolfenstein:~$ cat .xsetwacom.sh
## Device names and ID numbers from 'xinput --list'.

## stylus = "Wacom_BambooFun_2FG_4x5_Pen_stylus"
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_stylus" Suppress "2"  # data trimmed, 0-100
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_stylus" RawSample "20"  # default is 4
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_stylus" ClickForce "6"  # 1-21
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_stylus" PressCurve "0 0 100 100"
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_stylus" TPCButton "on"
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_stylus" Mode "Absolute"  # or Relative
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_stylus" Button1 "1"  # left mouse click
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_stylus" Button2 "3"  # right mouse click
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_stylus" Button3 "2"  # middle mouse click

## eraser = "Wacom_BambooFun_2FG_4x5_Pen_eraser"
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_eraser" Suppress "2"  # data trimmed, 0-100
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_eraser" RawSample "20"  #default is 4
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_eraser" ClickForce "6"  # 1-21
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_eraser" PressCurve "0 0 100 100"
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_eraser" Mode "Absolute"  # or Relative
xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_eraser" Button1 "1"

## touch = "Wacom_BambooFun_2FG_4x5_Finger_touch"
xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_touch" Touch "on"
xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_touch" Gesture "on"
# 1FG dbl. tap is left click, 2FG dbl. tap is right click
xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_touch" ZoomDistance "50"  # default is 50
xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_touch" ScrollDistance "20"  # default is 20
xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_touch" TapTime "250"  # 2FG R click, default is 250 ms

## pad = "Wacom_BambooFun_2FG_4x5_Finger_pad"
xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_pad" Button1 "1" ##"key ctrl t"  # toggle touch script
xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_pad" Button2 "3" ##"key backspace"
xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_pad" Button3 "2" # # right mouse click
xsetwacom set "Wacom_BambooFun_2FG_4x5_Finger_pad" Button4 "key alt left"  # Back a page in FireFox


Results of running .xsetwacom.sh:

greenman@Wolfenstein:~$ ./.xsetwacom.sh
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Pen_stylus value for 'PressCurve'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Pen_eraser value for 'PressCurve'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Finger_touch value for 'ZoomDistance'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Finger_touch value for 'TapTime'
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom_BambooFun_2FG_4x5_Finger_pad value for 'Button4'

---

### Post by Favux on 2010-10-31
Try using the "Device names" from xinput --list without the underscores connecting them.  In other words:
```
"Wacom BambooFun 2FG 4x5 Pen stylus"
```
instead of
```
"Wacom_BambooFun_2FG_4x5_Pen_stylus"
```

---

### Post by doctordruidphd on 2010-10-31
That didn't work:

greenman@Wolfenstein:~$ xsetwacom set "Wacom BambooFun 2FG 4x5 Pen eraser" PressCurve "0 0 100 100"
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom BambooFun 2FG 4x5 Pen eraser value for 'PressCurve'

However, for the fun of it, I tried:
greenman@Wolfenstein:~$ xsetwacom set "Wacom_BambooFun_2FG_4x5_Pen_eraser" PressCurve "0 0 0 0"
Pack: Value for 'PressCurve' out of range (0 - 100)

That's a different response. So maybe there is a bug after all?

Next thing I am going to try is building this on aptosid, and maybe lucid.  Have to do some other things now, so it may be a while before I can get back.  I do really appreciate your help, and I hope we can get to the bottom of this thing. Thanks, again.

---

### Post by doctordruidphd on 2010-10-31
Mystery solved -- though the problems are not.

I loaded a backup copy of my Maverick system onto another partition. I then did -- and only did -- the compilation for wacom.ko, copied into the relevant spot, did the depmod -a, and rebooted.  Well, that worked.  Indeed, I had to remove the underscores from the device name in .xsetwacom.sh, and once I did that, it ran just fine.  The values are setting and returning for PressCurve, etc.  Still can't set button4 to the escape key, nohow, but that's probably something else.

Then I remembered what I did.  I followed the instructions on linuxwacomproject, before I ever saw your howto, which included building and installing their utilities, including their version of xsetwacom.  I didn't do that on the new system, and the new system works fine. I copied xsetwacom from the new to the old system, and it still doesn't work there.

I suspect that I did some damage somewhere by installing that stuff, and I don't know if I'll ever figure out how to remove it, as it overwrote some files on the system.  Well, the backup is only a week old, so I probably won't lose much by just whacking it.

What's that about too many chefs...

Anyway, at long last, I have a functional, and configurable bamboo.  Thanks so much for your help.

---

