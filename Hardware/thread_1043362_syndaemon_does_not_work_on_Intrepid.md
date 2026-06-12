---
title: "syndaemon does not work on Intrepid"
date: 2009-01-18
forum: Hardware
---

### Post by sgla1 on 2009-01-18
Hey all,

Syndaemon will not start on Intrepid installed on a thinkpad t61p.  I get the following error:
```
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  148 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  10
  Current serial number in output stream:  10

~$ synclient -l
Can't access shared memory area. SHMConfig disabled?

```


I have configured **/etc/hal/fdi/policy/shmconfig.fdi** per the instructions in the community docs here: 
[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig]("https://help.ubuntu.com/communitySynapticsTouchpad#shmconfig") 
and per /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi.

Here's my shmconfig.fdi file:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.touchpad">
  <match key="info.product" contains="Synaptics TouchPad">
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>
```


Here's the output of xinput list:
$ xinput list
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
"TPPS/2 IBM TrackPoint"	id=3	[XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"	id=4	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=6	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=7	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255

Please let me know if I can provide any further information.  Thanks.

Oh yeah, forgot to mention that I am using Intrepid final on amd64 and xserver-xorg-input-synaptics 0.15.2-0ubuntu7.  Hehe.

---

### Post by sgla1 on 2009-01-18
Solved -- this is a well-known bug in Intrepid amd64 -- see
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/282735]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/282735") for a package which fixes this bug.

---

### Post by sgla1 on 2009-01-18
> **sgla1 said:**
> Solved -- this is a well-known bug in Intrepid amd64 -- see
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/282735]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/282735") for a package which fixes this bug.

The fixed package has moved to [http://launchpadlibrarian.net/18664539/xserver-xorg-input-synaptics_0.15.2-0ubuntu7~wgrant3_amd64.deb]("http://launchpadlibrarian.net/18664539/xserver-xorg-input-synaptics_0.15.2-0ubuntu7~wgrant3_amd64.deb")

---

