---
title: "SynapticsTouchpad Issue"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by cool_penguin on 2007-07-05
Hi Guys,

Firstly i would like to thank the UBUNTU team and all you guys for making Ubuntu such a grand success. I recently switched over to Ubuntu after having a hard time with with windows and after being rather unhappy with Xandros. Ubuntu works great and i can feel the stability. I have one small issue though.

I have an Acer Travelmate 2310 series which comes with a Synaptics touchpad. I would like to activate functions like tap to click, tap to drag and drop, tap to scroll, etc. I was looking up various posts on this form and all point out to editing the Synaptics touchpad section in the xorg.conf file. However when i open the xorg.conf file, i just see Input device as "Configured Mouse". I read the entire file carefully and there is not a single word like Synaptics or touchpad.

Even towards the end of the file (where everything in listed), i see configured mouse.

When i check for Hardware information (Preferences --> Hardware Info), i see it been detected as Synaptics touch pad.

Can anybody help me with this. I would like to configure my touchpad, but since i do not see any info regarding the same on the xorg.conf file, i am unable to do stuff and run applications like qsynaptics.

Thanks a lot in advance.

Keep up the great work guys.

Cheers,
Harry

---

### Post by geraldm on 2007-07-05
It is possible that a touchpad does not have or need a separate
driver.  I have one, a PS/2 device.  It is configured as a mouse.
The hardware on it is designed to appear as a mouse.
The xorg log shows it uses /usr/lib/xorg/modules/input/mouse_drv.so

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  Option "CorePointer"
  Option "Device" "/dev/input/mice"  # the only one.  use mice anyway.
  Option "Protocol" "ExplorerPS/2"
  Option "Emulate3Buttons" "true"
EndSection

Be sure the "ServerLayout" section has a line like
  InputDevice "Configured Mouse" "SendCoreEvents"
My xorg.conf muddles this with a wacom device, and
because I use /dev/input/mice the "SendCoreEvents"
only appears on the wacom device, but everything works
nonetheless.
 
If you want to use a different driver, synaptics, qsynaptics, the man page in that
package should provide configuration information.  I think it
should be possible to just use the mouse driver, but that is
your choice.

Gerald

---

