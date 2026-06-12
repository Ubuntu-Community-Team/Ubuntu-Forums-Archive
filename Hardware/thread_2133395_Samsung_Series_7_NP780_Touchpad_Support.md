---
title: "Samsung Series 7 NP780 Touchpad Support"
date: 2013-04-08
forum: Hardware
---

### Post by peppedaman on 2013-04-08
Hello,

So far I've been having a problem with my Elantech multitouch trackpad in Linux. Basically all i get is right click left click and tap, along with movement abilities. The problem seems to be rooted in improper detection of the elantech as a touchpad, likely b/c its a new revision or whatnot. Using psmouse-elantech-v6 does nothing to solve the problem, though its changes the identifier shown in xinput and also reports "version 9" elantech touchpad. I've even tried psmouse-alps and psmouse-alps-dst (see dmesg for why), no effect on anything. All below info is from default psmouse, for reference. Synclient reports the same no matter what. dmesg is the same except it detects version 9 elantech as i said. Xorg.0.log is also identical. xinput reports "PS/2 Elantech TF Click-Pad" instead of the usual "PS/2 Elantech Touchpad". Of note is that working elantech trackpads of the past in forums i scouted through shows up as "ETPS/2 Elantech Touchpad". I think this might be a simple fix in the end, just improper detection, I hope. For reference, I've tried kernel 3.5 on Ubuntu 12.10 and kernel 3.8.0-17 on Ubuntu 13.04 thus far, with all combinations of psmouse. Here's my debug of default psmouse:

synclient -l
```
Couldn't find synaptics properties. No synaptics driver loaded?
``` //note that even if attempting to force synaptics it will reject the touchpad as unknown

dmesg (snipped)
```

[   19.796863] psmouse serio1: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[   19.989545] psmouse serio1: elantech: unknown hardware version, aborting...
[   20.175551] input: PS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input4

```

/var/log/Xorg.0.log (snipped)
```

[    30.009] (**) PS/2 Elantech Touchpad: Applying InputClass "evdev pointer ca
tchall"
[    30.009] (II) Using input driver 'evdev' for 'PS/2 Elantech Touchpad'
[    30.009] (**) PS/2 Elantech Touchpad: always reports core events
[    30.009] (**) evdev: PS/2 Elantech Touchpad: Device: "/dev/input/event4"
[    30.009] (--) evdev: PS/2 Elantech Touchpad: Vendor 0x2 Product 0x1
[    30.009] (--) evdev: PS/2 Elantech Touchpad: Found 3 mouse buttons
[    30.009] (--) evdev: PS/2 Elantech Touchpad: Found relative axes
[    30.009] (--) evdev: PS/2 Elantech Touchpad: Found x and y relative axes
[    30.009] (II) evdev: PS/2 Elantech Touchpad: Configuring as mouse
[    30.009] (**) evdev: PS/2 Elantech Touchpad: YAxisMapping: buttons 4 and 5
[    30.009] (**) evdev: PS/2 Elantech Touchpad: EmulateWheelButton: 4, Emulate
WheelInertia: 10, EmulateWheelTimeout: 200
[    30.009] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[    30.009] (II) XINPUT: Adding extended input device "PS/2 Elantech Touchpad" (type: MOUSE, id 13)
[    30.009] (II) evdev: PS/2 Elantech Touchpad: initialized for relative axes.
[    30.009] (**) PS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    30.009] (**) PS/2 Elantech Touchpad: (accel) acceleration profile 0
[    30.009] (**) PS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    30.009] (**) PS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    30.010] (II) config/udev: Adding input device PS/2 Elantech Touchpad (/dev/input/mouse0)
[    30.010] (II) No input driver specified, ignoring this device.
[    30.010] (II) This device may have been added with another device file.


```

xinput | grep Elan
```

PS/2 Elantech Touchpad                      id=13    [slave  pointer  (2)]

```

my 10-evdev.conf
```

 GNU nano 2.2.6                                              File: /usr/share/X11/xorg.conf.d/10-evdev.conf                                                                                                   


#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.


Section "InputClass"
       Identifier "evdev pointer catchall"
       MatchIsPointer "on"
       MatchDevicePath "/dev/input/event*"
       Driver "evdev"
EndSection


Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection


Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection


Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection


Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

```

my 50-synaptics.conf
```

# Example xorg.conf.d snippet that assigns the touchpad driver
# to all touchpads. See xorg.conf.d(5) for more information on
# InputClass.
# DO NOT EDIT THIS FILE, your distribution will likely overwrite
# it when updating. Copy (and rename) this file into
# /etc/X11/xorg.conf.d first.
# Additional options may be added in the form of
#   Option "OptionName" "value"
#
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html
      MatchDevicePath "/dev/input/event*"
EndSection


Section "InputClass"
        Identifier "touchpad ignore duplicates"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/mouse*"
        Option "Ignore" "on"
EndSection


# This option enables the bottom right corner to be a right button on
# non-synaptics clickpads.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
EndSection


# This option disables software buttons on Apple touchpads.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Disable clickpad buttons on Apple touchpads"
        MatchProduct "Apple|bcm5974"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"
EndSection

```


Hope things go well with this. The computer is rather new and already the support is great otherwise. It's going to be a popular laptop I imagine so if this can be patched early it'll save alot of people the headache I've been going through. Feel free to ask any questions and request any testing. 
:)

---

### Post by Jadenity on 2013-04-19
I have the exact same problem with exactly the same outputs. Is there a bug report for this exact problem yet?

---

### Post by trjnhrse44 on 2013-05-01
Their is indeed a bug open for this problem. Unfortunately, it doesnt seem to be a priority.  This is really something that should be solved upstream anyway.
[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442
[/URL]
In the mean time I can tell you that forcing the driver to recognize the hardware as applicable to driver version 4, does not help.  The driver as written includes cases for recognizing 6 types of hardware.  This hardware reports as version 7, but also seems to require a new version of the driver to be written. (hardware v6 used driver v4, but v7 does not like the v4 driver)  When forcing version 4, I get all kinds of protocol communication errors.  I am in the process of writing a modified driver, but have to admit, this type of hardware hacking is new to me.  ( I am primarily a python coder, and this is all in C and focused on bitwise operations. )  I have a VERY buggy, yet working version currently, and I will post code here, when usable.

---

### Post by peppedaman on 2013-05-05
> **trjnhrse44 said:**
> Their is indeed a bug open for this problem. Unfortunately, it doesnt seem to be a priority.  This is really something that should be solved upstream anyway.
[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442
[/URL]
In the mean time I can tell you that forcing the driver to recognize the hardware as applicable to driver version 4, does not help.  The driver as written includes cases for recognizing 6 types of hardware.  This hardware reports as version 7, but also seems to require a new version of the driver to be written. (hardware v6 used driver v4, but v7 does not like the v4 driver)  When forcing version 4, I get all kinds of protocol communication errors.  I am in the process of writing a modified driver, but have to admit, this type of hardware hacking is new to me.  ( I am primarily a python coder, and this is all in C and focused on bitwise operations. )  I have a VERY buggy, yet working version currently, and I will post code here, when usable.

Hey,

Thank you for your response and for your efforts! I'm sure your efforts will not go in vain. I tried figuring out how to reverse engineer the protocol, but didn't get very far as there isn't much information out there on the subject. If there is anything I can do to help, let me know. I can code at a basic level in C and I do have an understanding of things such as bitwise operations. I can also test things out if you need a tester. Thanks again!

Oh yea, and I actually figured out it would be better to flag it upstream after making this thread, I made that issue ticket :P

---

### Post by fenshu on 2013-05-05
I ve series 7 NP740 and it's the same ... it dont show the elantech name... at all... in fact

xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                            id=10    [slave  pointer  (2)]
[COLOR=#b22222]&#9116;   &#8627; PS/2 Generic Mouse                          id=12    [slave  pointer  (2)][/COLOR]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; WebCam SC-10HDP12631N                       id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
reso@reso:~$

---

### Post by peppedaman on 2013-05-05
> **fenshu said:**
> I ve series 7 NP740 and it's the same ... it dont show the elantech name... at all... in fact

xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                            id=10    [slave  pointer  (2)]
[COLOR=#b22222]&#9116;   &#8627; PS/2 Generic Mouse                          id=12    [slave  pointer  (2)][/COLOR]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; WebCam SC-10HDP12631N                       id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
reso@reso:~$

Are you at least on kernel 3.2? IIRC there was a commit related to elantech touchpads back then. In any case I'd update to the latest kernel if you havent already.

---

### Post by gregoire on 2013-05-07
I have the same problem. I have added a comment on the bug report... Hope that there will be a fix soon.

---

### Post by dlane on 2013-05-09
I'm experiencing the same problem, also getting the generic
"PS/2 Generic Mouse id=11 [slave pointer (2)]" 
from xinput. This is on a Gigabyte U2442V laptop. dmesg says I've got a 
"PS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input25"

I'm running kernel 3.5.0-28-generic (on Linux Mint)...

---

### Post by murmlos on 2013-05-11
Hello, im having the same problem as OP with my Samsung 900x3e. Im guessing its the same touchpad.

Im on kernel 3.9.0 and it hasn't been fixed... Oh and im using Arch Linux!

---

### Post by hennilu on 2013-05-12
Exactly the same problem here as OP and murmlos. I have the same computer as murmlos (samsung 900x3e).
I've tried with ubuntu 12.04, 12.10 and 13.04 without success (default kernels on every version from 3.5.x through to 3.8.x)

---

### Post by lgrangeia on 2013-05-16
> **trjnhrse44 said:**
> Their is indeed a bug open for this problem. Unfortunately, it doesnt seem to be a priority.  This is really something that should be solved upstream anyway.
[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442
[/URL]
In the mean time I can tell you that forcing the driver to recognize the hardware as applicable to driver version 4, does not help.  The driver as written includes cases for recognizing 6 types of hardware.  This hardware reports as version 7, but also seems to require a new version of the driver to be written. (hardware v6 used driver v4, but v7 does not like the v4 driver)  When forcing version 4, I get all kinds of protocol communication errors.  I am in the process of writing a modified driver, but have to admit, this type of hardware hacking is new to me.  ( I am primarily a python coder, and this is all in C and focused on bitwise operations. )  I have a VERY buggy, yet working version currently, and I will post code here, when usable.

Hi,

Can you please send me your patch/code? I'll be happy to help, as I have some experience in kernel coding, and a samsung NP730U3E that suffers from the same problem.

If its ok, please post your patch here or send it to luis.grangeia at gmail.

Thanks,

LG

---

### Post by trjnhrse44 on 2013-05-16
I am at work now, and have no access to the laptop I am writing the patch on.  I will post it later today/tomorrow as soon as I get a chance.  Thanks for the help!

---

### Post by yngvewb on 2013-05-17
I have the same problem on Samsung Series 9 on Ubuntu 13.04. Reports as PS/2 Elantech Touchpad  and no multitouch. I also would really like to test your new driver :-)

---

### Post by trjnhrse44 on 2013-05-17
> **yngvewb said:**
> I have the same problem on Samsung Series 9 on Ubuntu 13.04. Reports as PS/2 Elantech Touchpad  and no multitouch. I also would really like to test your new driver :-)

Alas, I went to the pub last night and so didn't get to this yet.  I will deliver though, have no fear!

---

### Post by yngvewb on 2013-05-18
Hehehe, I would happily buy you a beer if I get the touchpad to do to finger scrolling :-)

---

### Post by madko on 2013-05-26
Same problem here on NP740

---

### Post by beachbum2049 on 2013-05-26
Same problem as above. I've tried using the system76 elantech-v6 driver and this tutorial:

[http://ubuntuforums.org/showthread.php?t=2111236](http://ubuntuforums.org/showthread.php?t=2111236)

but the module build produced errors.

Also tried patching using a supposedly working patch from Arch AUR here:

[https://aur.archlinux.org/packages/psmouse-elantech/](https://aur.archlinux.org/packages/psmouse-elantech/)

But that didn't help.

Edit:
The patch from AUR allowed the module to compile, and the pointer works without no multi-touch, so no change there. But, my xinput shows this now:

> &#9121; Virtual core pointer                        id=2    [master pointer  (3)]&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                            id=10    [slave  pointer  (2)]
&#9116;   &#8627; **PS/2 Elantech ETF1059 Click-Pad             **id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; WebCam SC-10HDP12631N                       id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]


---

### Post by pepl on 2013-06-04
> **trjnhrse44 said:**
> I am at work now, and have no access to the laptop I am writing the patch on.  I will post it later today/tomorrow as soon as I get a chance.  Thanks for the help!

Hi [**[COLOR=#000000]trjnhrse44[/COLOR]**]("http://ubuntuforums.org/member.php?u=91075"),

Any news on the patch? I would be happy to help/test.

Cheers,
Michael

---

### Post by yngvewb on 2013-06-06
Me too

---

### Post by audiocircut on 2013-06-08
Im also having this problem and am interested in testing any patches :). I am on a samsung Series 7 ultra NP740U3E.

---

### Post by clayboy on 2013-06-09
also available to test any patches that come thru the pipeline... wanna get my new sexy beast up and fully running =)

---

### Post by kendatsuba on 2013-06-14
Hello everybody, please refer to:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442)

for a possibly working patch.

Best regards,
Matteo

---

### Post by pepl on 2013-06-15
> **kendatsuba said:**
> Hello everybody, please refer to:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442)

for a possibly working patch.

Best regards,
Matteo

Worked for my Samsung Series 7 NP730! Thx a lot Matteo!!!

Madko++ wrapped up the patch for DKMS - [http://ubuntuforums.org/showthread.php?t=2111236&p=12692065#post12692065](http://ubuntuforums.org/showthread.php?t=2111236&p=12692065#post12692065)

---

