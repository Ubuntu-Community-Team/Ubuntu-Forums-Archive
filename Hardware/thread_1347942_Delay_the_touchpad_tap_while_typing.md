---
title: "Delay the touchpad tap while typing"
date: 2009-12-06
forum: Hardware
---

### Post by orengolan on 2009-12-06
laptop: Dell Inspiron 11z with xubuntu 9.10
My touchpad works, but I try to delay or disable the touchpad tap while I type.
when I type: syndaemon -t
I see ```
'unable to find a synaptics device'.
```

when I type gsynaptics 
I see: ```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```

touchfreeze application is not working as well.

I had no entry for touchpad in xorg and someone told me to add 2 sections there and to add this line: Option "SHMConfig" "true".
I did it but it didn't help.
I read [here]("https://help.ubuntu.com/community/SynapticsTouchpad") that adding /etc/hal/fdi/policy/shmconfig.fdi with some xml stuff will help but it didn't do anything.
Here is the shmconfig.dfi:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
    </match>
  </device>
</deviceinfo>
```

Here is my xorg.conf (the last 2 sections are the ones I added):
```
Section "Device"
        Identifier "Configured Video Device"
EndSection

Section "Monitor"
        Identifier "Configured Monitor"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
EndSection

Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "HorizScrollDelta" "0"
        Option "SHMConfig" "true"
EndSection

Section "ServerLayout"
        Identifier "Layout0"
        InputDevice "Synaptics Touchpad" "Core Pointer"
        Screen "Default Screen"
EndSection
```

Is my xorg.conf ok?

I also see this issue mentioned on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/132627")-
[https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/132627](https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/132627)

---

### Post by QuanTime on 2009-12-06
ubuntu 9.10 x64
Same problem..  I have a Asus K70IC series mantop (mantop is a 17" or bigger laptop.. anyways..)

```

quantime@allenkey:~$ tpconfig
Could not open PS/2 Port [/dev/psaux].

```

```

quantime@allenkey:~$ syndaemon 
Unable to find a synaptics device.

```

```


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
    Load    "synaptics"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    #Driver         "mouse"
    #Option         "CorePointer"
    #Option         "Device" "/dev/input/mice"
    #Option         "Protocol" "ExplorerPS/2"
    #Option         "ZAxisMapping" "4 5"
    #Option         "Emulate3Buttons" "false"

    Driver      "synaptics"
   Option       "CorePointer"
   Option       "Device"        "/dev/psaux"
   Option       "Protocol"      "auto-dev"
   Option       "LeftEdge"      "1700"
   Option       "RightEdge"     "5300"
   Option       "TopEdge"       "1700"
   Option       "BottomEdge"    "4200"
   Option       "FingerLow"     "25"
   Option       "FingerHigh"    "30"
   Option       "MaxTapTime"    "180"
   Option       "MaxTapMove"    "220"
   Option       "VertScrollDelta" "100"
   Option       "MinSpeed"      "0.06"
   Option       "MaxSpeed"      "0.12"
   Option       "AccelFactor" "0.0010"
   Option       "SHMConfig"     "on"
EndSection

```

```

quantime@allenkey:~$ xinput list
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=2    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Sleep Button"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Asus Laptop extra buttons"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"ImPS/2 Logitech Wheel Mouse"    id=7    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 7
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"AT Translated Set 2 keyboard"    id=8    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"CNF7129"    id=9    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=10    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1


```

Thats as far as i can get now..  Whats your outputs like ?  Maybe i need to change my input device to reflect what xinput is reporting ?

---

### Post by orengolan on 2009-12-06
xinput list
```
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"ImPS/2 Logitech Wheel Mouse"	id=2	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 7
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Dell WMI hotkeys"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Integrated Webcam"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=8	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=9	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Dynex Wired Optical Mouse"	id=10	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 13
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```

---

### Post by QuanTime on 2009-12-06
i see your device at ID 9 is the same as my ID 10 device.
Maybe this is the clue ?  Not sure about it being 5 button though.

-----
EDIT
-----
lshal > list.txt 
These are the only things relating to mouse inputs.  I read somewhere it should be identified as a synaptic device..  Ideas or fixes ?

```

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  info.product = 'ImPS/2 Logitech Wheel Mouse'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'  (string)
  input.device = '/dev/input/event9'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  input.product = 'ImPS/2 Logitech Wheel Mouse'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event9'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio4/input/input9/event9'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'  (string)
  input.device = '/dev/input/event4'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/virtual/input/input4/event4'  (string)


```

---

### Post by QuanTime on 2009-12-12
bump for help. i still cant solve this.  I use gnome ubuntu.. but it seems its relevant to kbuntu too.

---

### Post by wilee-nilee on 2009-12-12
touchfreeze in synaptic will delay the touchpad and a little more.

---

### Post by QuanTime on 2009-12-12
when you say that, how do you mean touchfreeze ? i DONT have synaptic registering my touchpad.. Far as i can guess, its ps2 mouse.
In System -> Preferences -> Touchpad.

When i click it, i get 

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

Ive enabled SHMConfig and tried all sorts of solutions, but my touchpad just wont recognise for some reason.. It works, but i cant alter anything..

Ideas ?

---

### Post by wilee-nilee on 2009-12-12
touchfreeze is a program in synaptic go system-administration-synaptic package manager.

---

### Post by Zorael on 2009-12-12
Is it a real Synaptics pad, then? If not, chances are the synaptics driver won't work for you - and as you listed it's recognized as a normal PS/2 mouse.

It's technically possible to modify the synaptics driver to make it accept a different pad as a "real" Synaptics pad (as patsissions did in [this thread](http://ubuntuforums.org/showthread.php?t=1314919)), but there's *no* guarantee it will work. Much like you can't really use ATI drivers with an Nvidia card.

I'm not sure if ALPS pads work with the Synaptics driver, but at least Sentelic pads need drivers of their own.

If yours is indeed a Synaptics pad and it's just not being recognized as one, the driver will have to be updated to include its device ID. That's a legitimate bug and should be filed against the driver package xserver-xorg-input-synaptics (or directly upstream).

---

### Post by QuanTime on 2009-12-13
Its fairly obvious now that its NOT a synaptics device.. Any way to identify what it is and get some use out of it ? its starting to drive me b@tsh!t crazy...

```

quantime@allenkey:~$ touchfreeze 
SynDaemon::SynDaemon 

set daemon true 
set pad true 
using typing delay of 500 ms 
"/usr/bin/synclient" 
initial state is TouchpadOff= 0 
Segmentation fault
quantime@allenkey:~$ 


```

---

### Post by Zorael on 2009-12-14
[Googling suggests](http://www.laptopmag.com/laptops/dell-inspiron-11z.aspx) that the Inspiron 11z has an "[Elan Smart-Pad](http://www.emc.com.tw/eng/tpn_sp_fun.asp)" instead of a Synaptics touchpad. Much like with the Sentelics, they're likely cheaper so Dell chose to save a buck.

> **Q: Where can I download the Elan's driver?**
Please download it from your system manufacturer's website.

I think the only real way to get standard touchpad functionality of it is to have Elan provide linux drivers. You could either contact Dell and see if you can get more than canned responses from them, or write a mail to Elan themselves. Since it looks like they have the policy that users should get their drivers from the manufacturers, for all I know they have linux drivers laying about, and it's just up to Dell to start distributing them.

Or they could just be an up-and-coming Taiwanese company who has put priority on writing Windows software to get out onto the market faster.

---

### Post by QuanTime on 2009-12-14
Ive just learnt that my Asus 17" lappy (K70IC) has a Elantech pad also.  Ill try to get onto them with what info i now have.

Cheers for the guidance.

-----
EDIT
-----

[http://arjan.opmeer.net/elantech/](http://arjan.opmeer.net/elantech/)

just found that.. what ya think ?

---

### Post by Zorael on 2009-12-15
Well, if you indeed have an Elantech pad (dmesg | grep -i elantech), and it's not being recognized by the Synaptics driver, then perhaps you need to do as that page says and contact the maintainer to have its device ID added.

---

### Post by orengolan on 2009-12-28
According to the link that QuanTime mentioned,
I need kernel 2.6.28 or newer and  Xorg Synaptics driver 0.99.1 or newer.
it looks like I have xserver-xorg-input-synaptics 1.1.2-1ubuntu7
I am confused. do i need to install anything or do I have everything needed for my touchpad to be recognized?

Zorel, can you elaborate about "ontact the maintainer to have its device ID added"  I am not sure if it's relevant to me.

Thanks!

uname -r
```
2.6.31-16-generic
```

dpkg -l |grep syna
```
ii  gsynaptics                                 0.9.16-2                                   configuration tool for Synaptics touchpad driver of X server
ii  synaptic                                   0.62.7ubuntu6                              Graphical package manager
ii  xserver-xorg-input-synaptics               1.1.2-1ubuntu7                             Synaptics TouchPad driver for X.Org server
```

---

### Post by QuanTime on 2009-12-28
I think our hardware ID doesnt match the list that the driver has, so its not registering.  Im not sure how to fix / add it.
It was the same with the webcam and lib4vl drivers.  It just needed the hardware ID for it to work properly.

Am i wrong in saying this ?

---

### Post by orengolan on 2009-12-28
I contacted the maintainer and will update if he replies.
also,  dmesg | grep elan returns nothing.
What do u guys see when you type it?

---

### Post by QuanTime on 2009-12-29
same.. nothing.. but when i mod my ps2 mouse, it mods the touchpad.. so its just identifying wrong.

---

### Post by orengolan on 2010-01-23
I contacted dell and they told me to call the "direct number for ubuntu - 1-866-982-8688"

I called this number (it's Canonical), left a message but they didn't reply.
I'll call again next week but please call them as well!

I will try to call Elan, the manufacturer of the touchpad if Canonical keeps ignoring me.


I found another thread about this issue. Dell mini 10 (not 10V) has elantech as well:
[http://ubuntuforums.org/showthread.php?p=8713106#post8713106](http://ubuntuforums.org/showthread.php?p=8713106#post8713106)

---

### Post by QuanTime on 2010-01-23
im curious..  EEEpc touch works fine with the extra functions, and they are elantech.  Maybe the hardware ID isnt correctly being identified.  So once new models are added to the list, everything will work ?

This is what happened with my laptop webcam.  once it was added, everything worked perfectly.

Anyone know who the package maintainer for elantech is ? maybe thats an option.

---

### Post by orengolan on 2010-01-25
I submitted the bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/512192](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/512192)

Please go there and change the status to 'Confirm' so Ubuntu developers will understand that it's a hardware issue and not something specific to me.

Thanks!

---

### Post by QuanTime on 2010-01-25
done.. But the more ppl who comment on it, the more helpful it might be for the dev's

---

### Post by cynthia386 on 2010-02-17
Addressing this issue at the driver level is overly complex.  All you need to do is to provide an option to disable the mouse while typing.

---

### Post by orengolan on 2010-04-11
I just upgraded to 10.4 and it was not fixed.
here are the 2 bug reports, please go there and add a comment with your machine etc.

[https://bugs.launchpad.net/ubuntu/ha...ev/+bug/123775](https://bugs.launchpad.net/ubuntu/ha...ev/+bug/123775)

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/512192](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/512192)

I also post it on kernel-team mailing list:
[https://lists.ubuntu.com/archives/ke...il/009826.html](https://lists.ubuntu.com/archives/ke...il/009826.html)

go there and reply, tell the developers it's a real issue.

Also go to #ubuntu-kernel on irc and ask about it.

---

### Post by QuanTime on 2010-04-11
> **cynthia386 said:**
> Addressing this issue at the driver level is overly complex.  All you need to do is to provide an option to disable the mouse while typing.

Yup, all i want, but cant get it :(

---

### Post by alhead on 2010-09-29
Has anyone been able to fix this?  I just installed Ubuntu 10.04 on a new eee pc 1015PEB.  GPointingDeviceSettings thinks it's a Logitech PS2 Wheel Mouse.  I can't access any touchpad settings.

---

### Post by Quan-Time on 2010-09-29
i actually had a fix with 9.10 karmic..  Since upgrade to 10.04 lucid, its all gone.  Sort of annoying but its something im dealing with.  Ive just learnt to type slightly differently.

If there is a fix, id happily use it again.  Ive also noticed my HorizTwoFingerScroll=1 option no longer works as i dont have gsynaptics, only VertTwoFingerScroll works, which is 1 (on) by default now.

Previously i had to have those 2 commands, and 2 other options on a script @ startup and it was good to go.

---

### Post by alhead on 2010-09-29
I found a thread that helped me.
[http://ubuntuforums.org/showpost.php?p=9175201&postcount=44](http://ubuntuforums.org/showpost.php?p=9175201&postcount=44)
I followed the instructions, and now I can configure the touchpad.

---

### Post by Detroit Frog on 2010-10-01
> **alhead said:**
> I found a thread that helped me.
[http://ubuntuforums.org/showpost.php?p=9175201&postcount=44](http://ubuntuforums.org/showpost.php?p=9175201&postcount=44)
I followed the instructions, and now I can configure the touchpad.

I think we have the same machine (Asus 1015PEB with 10.04)
I followed the same instructions but at step 5 the patches fail to work. I get this:

```
patching file drivers/input/mouse/elantech.c
Hunk #1 FAILED at 666.
1 out of 1 hunk FAILED -- saving rejects to file drivers/input/mouse/elantech.c.rej

```

Any idea what could be the problem?

---

### Post by zeating on 2010-10-03
> **alhead said:**
> I found a thread that helped me.
[http://ubuntuforums.org/showpost.php?p=9175201&postcount=44](http://ubuntuforums.org/showpost.php?p=9175201&postcount=44)
I followed the instructions, and now I can configure the touchpad.

Wanted to sign up just to say thank you, been looking forever for a fix for my touchpad and this was the only thing that worked. I can now adjust settings in gpointing-device-settings and things function as they are intended to! :popcorn:

---

