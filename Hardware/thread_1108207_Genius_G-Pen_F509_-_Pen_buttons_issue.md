---
title: "Genius G-Pen F509 - Pen buttons issue"
date: 2009-03-27
forum: Hardware
---

### Post by oberonking on 2009-03-27
Hi, I Follow this [Tutorial]("http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html") and now i can use mi tablet. 
unless the pen buttons don't work well, there's only 1 button map.
If I use xinput "n" 1 3 2 or any combination only change the first value and the other take the same value.

If I edit The xorg.conf like sayd on many howtos... the X don't work anymore... why xorg.conf since Hardy can't edit anymore without X crash?? and where's the InputDevice things??

One more thing: the lsusb exit don't gives me any name for this device:

```
mato@R2-D2:~$ lsusb 
Bus 001 Device 003: ID 172f:0038                                   <<-- [COLOR="Red"]this is my tablet O.o[/COLOR]   
Bus 001 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mato@R2-D2:~$
```

I attach Xorg.0.log and lshal exit

Any Idea???

This issue aren't killing me, but I wish that all of buttons work fine.

PS: Sorry about my english, I'm out of practice :(

---

### Post by oberonking on 2009-03-27
Bump

---

### Post by oberonking on 2009-03-28
Bump again

---

### Post by oberonking on 2009-10-12
bump.... any ideas???
please help me!!!!

---

### Post by Favux on 2009-10-12
Hi oberonking,

I think you are using Jaunty (9.04).  Is this right?

The idea in going from xorg.conf to HAL/.fdi is that it gets you usb hot plugging.

Why don't you try this ppa (or the deb.s in it)?  I think the wizardpen.fdi is included:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)  Maybe that will help with the buttons.

Let's see what:
```
xinput --list
```
is calling your tablet and devices.

---

### Post by oberonking on 2009-10-12
Here's my xinput --list exit

```
mato@R2-D2:~$ xinput --list
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
"Genius Optical Mouse"	id=5	[XExtensionPointer]
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
"stylus"	id=4	[XExtensionPointer]
	Num_buttons is 6
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1280
		Resolution is 1000
	Axis 1 :
		Min_value is 0
		Max_value is 1024
		Resolution is 1000
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1000
mato@R2-D2:~$
```

It's the "stylus".. because Blender's pressure.

Here's the button map that I put.. but all the buttons take the valour of the tip.

```
mato@R2-D2:~$ xinput get-button-map "stylus"
1 3 2 4 5 0
```

---

### Post by Favux on 2009-10-12
Hi oberonking,

Did you try the driver in the ppa?

---

### Post by oberonking on 2009-10-12
I install it, but now don't work anymore... 
Have to use "/etc/hal/fdi/policy/99-x11-wizardpen.fdi" like always?

---

### Post by Favux on 2009-10-12
Hi oberonking,

Yes I think that's where the .fdi goes and it's name.  Reboot a couple of times and also check the contents of the .fdi.  It shouldn't work and then stop working.

Try in a terminal:
```
grep -i name /proc/bus/input/devices
```
Let see if we can get a name.  I want to be sure it's a wizardpen tablet.

Also see this link on setting up:  [http://www.jpbouza.com.ar/ESP2/tutoriales/gnulinux/genius-tablet/id/en](http://www.jpbouza.com.ar/ESP2/tutoriales/gnulinux/genius-tablet/id/en)

---

### Post by oberonking on 2009-10-12
```
N: Name="Power Button (FF)"
N: Name="Power Button (CM)"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Genius Optical Mouse"
N: Name="PC Speaker"
[COLOR="Red"]**N: Name="         WALTOP             Tablet    "**[/COLOR]
```

The red one is the tablet.... strange isn't it? 

and this is where apear in lshal:

```
udi = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_0b_0'  (string)
  info.product = '         Tablet'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial'  (string)
  info.vendor = '         WALTOP'  (string)
  linux.device_file = '/dev/bus/usb/002/003'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 257  (0x101)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 3  (0x3)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = '         Tablet'  (string)
  usb_device.product_id = 56  (0x38)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = '         WALTOP'  (string)
  usb_device.vendor_id = 5935  (0x172f)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 257  (0x101)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 3  (0x3)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 56  (0x38)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = '         WALTOP'  (string)
  usb.vendor_id = 5935  (0x172f)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial_if0_logicaldev_input'
  access_control.file = '/dev/input/event5'  (string)
  access_control.type = 'mouse'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'input', 'input.mouse', 'input.tablet', 'access_control'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial_if0'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event5'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial_if0'  (string)
  input.product = '         WALTOP             Tablet'  (string)
  input.x11_driver = 'wizardpen'  (string)
  input.x11_options.BottomX = '17706'  (string)
  input.x11_options.BottomY = '10668'  (string)
  input.x11_options.MaxX = '17706'  (string)
  input.x11_options.MaxY = '10668'  (string)
  input.x11_options.SendCoreEvents = 'true'  (string)
  input.x11_options.TopX = '29'  (string)
  input.x11_options.TopY = '83'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input5/event5'  (string)
```

thanks for your help, i'm going crazy with it

---

### Post by Favux on 2009-10-12
Hi oberonking,

I looked at your lshal and discovered you have a Waltop tablet, not a wizardpen.
```
usb.vendor = '         WALTOP'  (string)
  usb.vendor_id = 5935  (0x172f)  (int)
```
So you're may be getting a conflict between the Waltop subsection of the 10-wacom.fdi and the wizardpen.fdi.

For how to set up your Waltop tablet please see:  [http://ubuntuforums.org/showthread.php?t=1261407&highlight=waltop](http://ubuntuforums.org/showthread.php?t=1261407&highlight=waltop)  The .fdi I modified for the Waltop in Jaunty is in post #8.  Please ask if you have any questions.

The wacom packages you want to install through Synaptic Package Manager are wacom-tools & xserver-xorg-input-wacom.

Edit:  Just saw your last post.  Looks like you found it was a Waltop too!

---

### Post by oberonking on 2009-10-12
Nice... thanks..
But, the buttons have the same issue... all are set like LMB.....

```
mato@R2-D2:~$ xsetwacom list
stylus           stylus    
pad              pad       
cursor           cursor    
eraser           eraser  
```

pressure works fine un Gimp, but no in blender.

---

### Post by Favux on 2009-10-12
Hi oberonking,

Yes, we couldn't get the stylus buttons to work right as you can see if you read through the thread.  I don't know why.  It would be nice to get them to work.

I think, maybe, I saw something that might apply.  Using xbindkeys?  I don't know if I can find it again.

Pressure should work in Blender if both "xsetwacom list" and "xinput --list" are calling the stylus 'stylus'.  I don't know why it wouldn't.

Does your stylus have an eraser?

---

### Post by oberonking on 2009-10-13
like I see, both takes "stylus"

```
mato@R2-D2:~$ xsetwacom list
stylus           stylus    
mato@R2-D2:~$ xsetwacom list
stylus           stylus    
mato@R2-D2:~$ xinput --list
.................
.................
"stylus"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 17920
		Resolution is 1016
	Axis 1 :
		Min_value is 0
		Max_value is 10752
		Resolution is 1016
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
mato@R2-D2:~$ 
```

eraser??? don't know... :confused:

I saw some rare things.... in Firefox, gedit, etc... both buttons works like MMB but, in Gimp.. Blender and desktop works like LMB.

EDIT: it's works like both buttons.. LMB + MMB

---

### Post by Favux on 2009-10-13
Hi oberonking,

Those outputs look correct and the xinput one is showing that the .fdi works and the tablet is being recognized as a tablet.

The eraser is on the back of the stylus like a regular eraser.  It retracts into the stylus like a special button.  It lets you use pressure to smudge.  Also does your tablet have a tablet mouse (cursor) or buttons on the tablet (pad)?

Did you set up wacomcpl yet?  See "Section 3: Calibrating your Tablet" here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Maybe that'll help you map your stylus buttons.  Although it didn't help the other Waltop tablet.

---

### Post by oberonking on 2009-10-13
no, the tablet don't have any button... 

I saw some rare things.... the buttons (not the tip) works like both buttons.. LMB + MMB......

---

### Post by Favux on 2009-10-13
Hi oberonking,

I don't know why the buttons act together.  Maybe they send a signal the linuxwacom drivers can't tell apart?

If I have an idea I'll let you know.

---

### Post by Favux on 2009-10-13
Hi oberonking,

If you are able to do technical stuff you might want to look at xidump.  Like:
```
xidump -l -v stylus
```
and then run it like:
```
xidump stylus
```
Use ctrl-C to exit.
I have only one stylus button 2 mapped to 3 and get:
```
 Buttons:                      3-UP  
```
when I use it.

From:  [http://linuxwacom.sourceforge.net/index.php/howto/xidump](http://linuxwacom.sourceforge.net/index.php/howto/xidump)

With
```
xidump -u raw stylus
```
I get
```
 Button: 3 UP
```
with the stylus button and with the stylus tip
```
 Button: 1 UP
```
Both expected, since the stylus tip is Button1 by default.

---

### Post by oberonking on 2009-10-13
Nice.....
If I change "Side Swithch Mode" to "Side Switch + tip" instead of "side Switch Only" in "wacomcpl" Buttons Works both like MMB..... And the Tip work too.

Now... why don't have pressure on Blender?, who knows.

Thanks Man... If you, someday come to Argentina... I'll Pay you some beers.

---

### Post by Favux on 2009-10-13
Hi oberonking,

You're welcome.  I'll take you up on the beers!

Progress!

Does Blender require configuring extended input devices like Gimp?

---

### Post by oberonking on 2009-10-13
> **Favux said:**
> Does Blender require configuring extended input devices like Gimp?

Nope... the only thing that Blender needs is that tablet name be "stylus"

So, why don't works? it's a mistery.

---

### Post by Favux on 2009-10-13
Hi oberonking,

It is a mystery.  Tudor117 said on the other thread:
> Blender now has pressure sensitivity which is even better!

Maybe you could try telling Synaptic Package Manager to reinstall Blender and reboot?

---

### Post by Favux on 2009-10-13
Hi oberonking,

I noticed in wacom_wac.c (one of the parts of the linuxwacom source code) that there seem to be device ID's for Graphire and Intuos styluses.  That may be why only one button works.  The linuxwacom code that is picking up your stylus (wherever it is) is identifying it as a stylus with one button?

---

### Post by oberonking on 2009-10-13
Hi Favux

I do some more (a lots of it) attempts to make work the pressure in Blender..... nothing work.
Gimp and other works fine......
I'm thinking to burn my tablet.....

	
I sent an email to the linuxwacom developer to explain my problems.
Still awaiting a reply.

If you have a clue... i'd be so happy to hear it.

---

### Post by Favux on 2009-10-13
Hi oberonking,

I was going to suggest you post on the Blender forum too.  But when I followed one of my links there I saw you just did!  :)

Did you try reinstalling Blender?  Did you remove the wizardpen.fdi and then reboot?

---

### Post by oberonking on 2009-10-14
Yes... I deleted all trace of wizardpen.
Blender, I use the precompiled one... but I install the repos one and nothing happens. 
I'm thinking to reinstall the System, maybe this way Blender start to work.

---

### Post by oberonking on 2009-10-14
Well.... I reinstalled the System and nothing happens.

Don't know what is wrong... If the tablet are take like "stylus" Blender must work perfectly, but in my case don't.

---

### Post by oberonking on 2009-10-15
I can't believe it!!!!!!!
At last can make it work, pressure in all applications.... 

So the "/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi" look like this:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
	<match key="info.product" contains="WALTOP">
		<merge key="input.x11_driver" type="string">wacom</merge>
		<merge key="input.x11_options.Type" type="string">stylus</merge>
		<merge key="info.product" type="string">stylus</merge>
		<merge key="input.x11_options.BottomY" type="string">10686</merge>
		<merge key="input.x11_options.BottomX" type="string">17679</merge>
		<merge key="input.x11_options.TopY" type="string">21</merge>
		<merge key="input.x11_options.TopX" type="string">21</merge>
	</match>
    </match>
  </device>
</deviceinfo>
```

Be careful with BottomY/X and TopY/X.... that you find in wacomcpl >> Tracking.

The linuxWacom I installed following this Tutorial: [http://ubuntuforums.org/showthread.php?t=1038949&page=11]("http://ubuntuforums.org/showthread.php?t=1038949&page=11") Post #104

Remember that my Tablet it's a Genius G-Pen F509. If any have the same Tablet and the same problem...... Hope that you have the same luck that I

Favux: Thank you so much!!!!!!

---

### Post by Favux on 2009-10-15
Hi oberonking,

Outstanding!!  You did it.  Nice work.  Blender with pressure!

You're welcome.

---

### Post by oberonking on 2009-10-15
I talk to soon.... 
Yes, pressure on Blender Work.. but only the first time that I open it after reboot. 
If I close the program and some time after start it again the pressure are lost.

That's so so so strange....... Why???

I'm write of this issue on the Blender's bug tracker.

---

### Post by cb951303 on 2009-12-11
does this tablet use Wacom or Wizardpen hardware?
does it work 100% when you configure it appropriately?

thanks

---

### Post by oberonking on 2009-12-11
> **cb951303 said:**
> does this tablet use Wacom or Wizardpen hardware?
does it work 100% when you configure it appropriately?

thanks

I try with both... wizardpen and wacom
with wizarpen the tablet work in a 10%
with wacom a 60%

i not be able to make it work 100%

---

### Post by Favux on 2009-12-11
Hi cb951303,

The tablet uses Waltop hardware.

Like oberonking says you can use the linuxwacom drivers in Karmic if you hack the wcmUSB.c and compile them.  That gives you some function.  You can also use the WizardPen drivers.

We're trying to compile the Waltop linux driver and making some progress.

---

### Post by mantha on 2010-02-05
Im triying to use my G-Pen F509 in Karmic Koala and it don't works:
I can use the pointer while I'm pressing one of the buttons, but if I don't press the tablet don't go...

I think that it's ussing the wacom driver of the Kernel.

What can i do?

I have searched a lot in the Internet and the only solution i have found is downgrade to another Ubuntu distro and this one is not viable for me...

---

### Post by oberonking on 2010-03-29
Hi Favux.... are you still there?

Well... the thing is, I'm trying Lucid in other PC and like I ear that not use hal anymore try to plug and make work my tablet.....
There isn't way to make it work... 
Any Idea to make it work without Hal???

Thanks

---

