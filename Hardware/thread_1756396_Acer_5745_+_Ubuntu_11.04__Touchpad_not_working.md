---
title: "Acer 5745 + Ubuntu 11.04  Touchpad not working"
date: 2011-05-12
forum: Hardware
---

### Post by hseth on 2011-05-12
Hi,

I just upgraded to 11.04 on my Acer 5745. Everything was looking and working gr8 but suddenly my touchpad stopped working. My touchpad was working fine with 10.10 and even with 11.04 (for atleast a couple of days :(). I dont remember changing anything. 

So, it may be after some updates.
I have looking around in the forum for a possible solution. 
From the discussion, I gathered that the problem can be at multiple levels

[LIST=1]
[*]The kernel is not recognizing the touchpad
[*]The XOrg is not recognizing it
[*]I disabled it manually(:rolleyes:)
[*][http://ubuntuforums.org/showpost.php?p=10714735&postcount=3](http://ubuntuforums.org/showpost.php?p=10714735&postcount=3)
[/LIST]
I'll go through one by one
3. I disabled and enabled my touchpad a number of times using the Fn + F7, I get a notification on the top-right corner but the touchpad still does not work
4. Tried the solution mentioned here, but no joy

Now I checked if the hardware is being recognized or not.
When i do 
```

$ cat /proc/bus/input/devices
```I get the following output for touchpad
```

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input9
U: Uniq=
H: Handlers=mouse1 event9 
B: PROP=9
B: EV=b
B: KEY=6420 3000f 0 0 0 0
B: ABS=260800011000003
```So it seems the 1) is not the problem :)

Now to check whether XOrg recognized the touchpad
```
$ xinput list
``````

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; 1.3M WebCam                                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=14    [slave  keyboard (3)]

```Also executing
```
cat /var/log/Xorg.0.log | grep -i synaptics
```gives
```
[    20.820] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    20.820] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    20.820] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    20.820] (II) LoadModule: "synaptics"
[    20.820] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.821] (II) Module synaptics: vendor="X.Org Foundation"
[    20.821] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    20.821] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.821] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.050] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5682
[    21.050] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4692
[    21.050] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    21.050] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    21.050] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[    21.260] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    21.260] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.360] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    21.360] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    21.360] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    21.360] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[    21.360] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    21.360] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    21.360] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    21.360] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    21.510] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    21.510] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[   785.970] (--) SynPS/2 Synaptics TouchPad: touchpad found

```From what i see, I understand that the touchpad is being recognized properly, but is not responding.

Not able to think anything further :confused:

--
Himanshu Seth

---

### Post by nems on 2011-05-13
Hi!

I have same laptop model as You, and same problem as you.
If you get a soulutin from an another source please notify me.

Thank you.
nems

---

### Post by sniper18 on 2011-05-16
I have a HP Mini with the same pointer device (Synaptics SynPS/2 TouchPad and I also have the same problem / symptoms.

---

### Post by Llewlyn on 2011-05-23
Your problem might be here:

```
[    20.820] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    20.820] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
```

Have a look at this:
[https://wiki.archlinux.org/index.php/Touchpad_Synaptics](https://wiki.archlinux.org/index.php/Touchpad_Synaptics)

Troubleshooting section.

Ll.

---

### Post by eeen on 2011-08-22
Hi, I'm having a pretty much identical problem, I looked at the troubleshooting links and it was no help, I dont really understand how to put the information there to use as I am totally new to this.

My laptop is a different model but appart from that the information the original poster posted applies to me aswell, was a solution found for this?

---

### Post by phetre on 2011-08-22
Same here, on an Asus EeePC 1005HAB. My touchpad suddenly stopped working about a week ago, but only after login—it works fine at the GDM greeter. My /var/log/Xorg.0.log shows the double loading of Synaptic mentioned in the Arch wiki, so I tried to implement the solution mentioned there. Ubuntu (at least on my machine) doesn't have an /etc/X11/xorg.conf.d/ directory by default, so I created one containing the block from the Arch wiki.

(That is:

```
$ sudo mkdir /etc/X11/xorg.conf.d
$ sudo nano /etc/X11/xorg.conf.d/10-synaptics.conf
```

Then I copied and pasted this from the Arch wiki:

```
Section "InputClass"
      Identifier "touchpad catchall"
      Driver "synaptics"
      MatchIsTouchpad "on"
      MatchDevicePath "/dev/input/event*"
            Option "TapButton1" "1"
            Option "TapButton2" "2"
            Option "TapButton3" "3"
EndSection
```

Then pressed ctrl-o and [enter] to save, and ctrl-x to exit.)

It didn't work—in fact, my /var/log/Xorg.0.log seems to show the module being loaded *three* times now:

```
$ cat /var/log/Xorg.0.log | grep -i synaptics
[    64.863] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    64.863] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    64.863] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
```

Does Ubuntu need this to go somewhere else besides /etc/X11/xorg.conf.d/, or do we use a different method entirely?

---

### Post by phetre on 2011-08-25
Aha! My problem seems to have nothing to do with the kernel module; it is fixed by [flipping a GConf setting]("http://ubuntuforums.org/showpost.php?p=9315670&postcount=6").

```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

---

### Post by coffeeaddict_nl on 2012-03-20
I've been trying a multitude of solutions, all without much effect; in the end it turned out that I had disabled the touchpad using Fn+F7, hitting it (Fn+F7) again made the touchpad 'just' work :oops:

Mine is an Aspire 7560G btw

---

### Post by randyklein99 on 2012-03-20
> **coffeeaddict_nl said:**
> I've been trying a multitude of solutions, all without much effect; in the end it turned out that I had disabled the touchpad using Fn+F7, hitting it (Fn+F7) again made the touchpad 'just' work :oops:

Mine is an Aspire 7560G btw

I've been there before...

---

