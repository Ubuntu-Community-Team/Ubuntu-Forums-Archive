---
title: "Unable to set SHMConfig to true in 8.10"
date: 2009-03-08
forum: Hardware
---

### Post by vincencollins on 2009-03-08
I recently upgraded to ibex and I am trying to get my touchpad working,  in that effort I have been trying to get gsynaptics initialize and get SHMConfig set to true in 8.10

I have tried about everything and nothing has worked so far.  Here is what I have tried.

I have tried to add a /etc/hal/fdi/policy/shmconfig.fdi file like the instructions indicate here - [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

I have tried to edit the /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi like the instructions indicate here - [http://www.samlesher.com/ubuntu/enable-shmconfig-for-synaptics-touchpad-on-ubuntu-intrepid-ibex-810](http://www.samlesher.com/ubuntu/enable-shmconfig-for-synaptics-touchpad-on-ubuntu-intrepid-ibex-810)

Below is the module section of the xorg.conf, everything else relevant to the touchpad has been commented out with the following comment "# commented out by update-manager, HAL is now used"

> Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
	Load		"synaptics"
EndSection

Also the option in the mouse menu for touchpad does not show up either.

I also had a session setup to run syndaemon -d -i 1 to disable the touchpad while I was typing and that isn't working either.  I get the following message - "Can't access shared memory area. SHMConfig disabled?"

Any information and advice would be appreciated.  Thanks.

---

### Post by bayerman on 2009-03-28
same problem here on my gx700!

xinput -list gives the following (only mouse-relevant parts):

```
"Virtual core pointer"  id=1    [XPointer]
        Num_buttons is 32
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is 0
                Max_value is -1
                Resolution is 0
        Axis 1 :
                Min_value is 0
                Max_value is -1
                Resolution is 0
"Mouse0"        id=3    [XExtensionPointer]
        Num_buttons is 9
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
"Macintosh mouse button emulation"      id=4    [XExtensionPointer]
        Num_buttons is 32
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
"ImPS/2 Logitech Wheel Mouse"   id=5    [XExtensionPointer]
        Num_buttons is 32
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

so there is no "Synaptics" or "ALPs" found. i tried pretty much the same things as you did vincencollins, did you succeed in the meantime?

kind regards

---

### Post by vincencollins on 2009-03-29
No I am still having this issue and it is very annoying.  If I make any progress I will update this thread.

Here is my xinput -list output.

```
administrator@sager-laptop:~$ xinput -list
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Macintosh mouse button emulation"	id=2	[XExtensionPointer]
	Num_buttons is 32
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
"ImPS/2 Logitech Wheel Mouse"	id=3	[XExtensionPointer]
	Num_buttons is 32
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
"USB Mouse"	id=7	[XExtensionPointer]
	Num_buttons is 32
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
"USB Mouse"	id=5	[XExtensionPointer]
	Num_buttons is 32
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

### Post by 1clue on 2009-04-08
I'm slightly ahead of you guys, but I have taken a step not mentioned in the above documentation:  I have installed the synaptics drivers and associated software, including anything at all relating to my window manager (gnome).  My xinput list command shows the following:

```
"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Macintosh mouse button emulation"	id=2	[XExtensionPointer]
	Num_buttons is 32
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
"AT Translated Set 2 keyboard"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Cirque Corporation USB GlidePoint"	id=4	[XExtensionPointer]
	Num_buttons is 32
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
"HID 04b3:310b"	id=5	[XExtensionPointer]
	Num_buttons is 32
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

When I boot, the touch pad works fine with its default settings.  Some of the special features of the pad work, including the scroll section which is incredibly better than a mouse wheel.

However, the control panel still won't launch, and it gives the SHMConfig error.  I have added a separate entry in the **/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi** file using the "Cirque Corporation USB GlidePoint" key, and in fact added the SHMConfig line to every group in the file.  No dice.

I've tried **synclient -l**, and it says no shared memory.  I tried **sudo hal-set-property --udi  '/org/freedesktop/Hal/devices/usb_device_488_23_noserial_if0_logicaldev_input' --key input.x11_options.SHMConfig --bool true** and managed to get it to take the property, but again trying **synclient -l** I get the same error.

I have tried editing the xorg.conf file directly, I have tried the Ubuntu wiki entry of adding SHMConfig to the driver directly, and I have tried it by specifically addressing the issue at the input device.

I think there is a bug here.  Either that, or maybe the touchpad control panel doesn't look in the same place for the memory setup?

---

### Post by schlort on 2009-04-24
To enable SHMConfig on Intrepid and Jaunty, the following is correct:

Use your preferred text editor (as root) to edit /etc/hal/fdi/policy/shmconfig.fdi
(i.e. sudo nano /etc/hal/fdi/policy/shmconfig.fdi )
It should contain --
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">true</merge>
  </match>
 </device>
</deviceinfo>

```


I use amd64 and there is a bug which causes syndaemon to never start.  The latest attempt on Jaunty failed with the error:
> X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  12
  Current serial number in output stream:  12

To remedy this, install the fixed synaptics driver from William Grant's PPA repo.  

For Intrepid (8.10):
```
echo -e "\n## Syndaemon 64-bit Fix PPA (wgrant)\ndeb http://ppa.launchpad.net/wgrant/ubuntu intrepid main" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 294bb98049fed1dd96e4915c2a7ceb1d8a626b42
sudo aptitude update
sudo aptitude install xserver-xorg-input-synaptics=0.15.2-0ubuntu7~wgrant3
```

For Jaunty (9.04):
```
echo -e "\n## Syndaemon 64-bit Fix PPA (wgrant)\ndeb http://ppa.launchpad.net/wgrant/ubuntu jaunty main" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 294bb98049fed1dd96e4915c2a7ceb1d8a626b42
sudo aptitude update
sudo aptitude install xserver-xorg-input-synaptics=1.1.0-0ppa2~wgrant3
```

---

### Post by Bobber76 on 2009-05-20
> **schlort said:**
> To enable SHMConfig on Intrepid and Jaunty, the following is correct:

Use your preferred text editor (as root) to edit /etc/hal/fdi/policy/shmconfig.fdi
(i.e. sudo nano /etc/hal/fdi/policy/shmconfig.fdi )
It should contain --
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">true</merge>
  </match>
 </device>
</deviceinfo>

```

This is NOT working... 8.10 sees my synaptics touchpad as a logitech scrollmouse... I just want 2 finger scroll again, as in jaunty, but i can't... This drives me crazy. I've googled all day, but nothing helps.

---

