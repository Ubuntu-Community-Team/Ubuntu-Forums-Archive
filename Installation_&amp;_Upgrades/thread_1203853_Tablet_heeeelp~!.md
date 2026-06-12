---
title: "Tablet heeeelp~!"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by Silvenium on 2009-07-03
HUGE Linux noob here.

--------

Using Jaunty, I am trying to get my *Genius MousePen 8x6* to work. When I touch the pen to the actual pad, the light which usually says it's working will turn on. Occassionally it will 'click' wherever the mouse is--but not every time.

I have all the windows drivers, tried opening them with wine, didn't work. 

I used this tutorial (Which is for the Wizard Pen...) [[http://www.jpbouza.com.ar/ESP2/tutoriales/linux/genius-tablet/id/en]]("http://www.jpbouza.com.ar/ESP2/tutoriales/linux/genius-tablet/id/en%5D") to help, but it also didn't work.

Any help would be much appreciated. When I had 8.10, the tablet worked FINE and worked automatically.

--------

If it helps, I have some information for my tablet/the usb cable/whatever...
usb_device_1d6b_1_0000_00_0b_0'  (string)
  info.product = 'Genius MousePen 8x6 Tablet'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial'  (string)
  info.vendor = 'UC-Logic Technology Corp.'  (string)
  linux.device_file = '/dev/bus/usb/002/003'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-6'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 0  (0x0)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 3  (0x3)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-6'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Genius MousePen 8x6 Tablet'  (string)
  usb_device.product_id = 5  (0x5)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'UC-Logic Technology Corp.'  (string)
  usb_device.vendor_id = 21827  (0x5543)  (int)
  usb_device.version = 1.1 (1.1) (double)

---

### Post by Favux on 2009-07-03
Hi Silvenium,

If you haven't already check these out.

The most useful is probably:  [http://ubuntuforums.org/showthread.php?t=1151464&page=2](http://ubuntuforums.org/showthread.php?t=1151464&page=2)

And then the following wiki's:
[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
[https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet)

Good luck!

---

### Post by Mark Phelps on 2009-07-04
Just so you know, you can't install windows drivers using Wine.

---

### Post by Silvenium on 2009-07-05
> **Favux said:**
> Hi Silvenium,

If you haven't already check these out.

The most useful is probably:  [http://ubuntuforums.org/showthread.php?t=1151464&page=2](http://ubuntuforums.org/showthread.php?t=1151464&page=2)

And then the following wiki's:
[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
[https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet)

Good luck!


I used the Tablet Setup WizardPen (first Wiki)--I can 'click' with my tablet pen, I just can't move it. Any idea/thoughts?

I tried the 'Everything worked great! Except the mouse doesn't move at all!' part. What do they mean by the...
 'The whole block is shown to indicate context. The main thing to change is theOption "Name" "UC-LOGIC Tablet WP8060U"part. Set the name to whatever type you have.' 
part? Don't really understand it. I'm sure if I knew what this meant, then I would get this better...

---

### Post by Favux on 2009-07-05
Hi Silvenium,

In Jaunty you don't want to use the xorg.conf.  Remove any entries you made in it.  You want to use HAL/.fdi.

See the post #16 that BCtom just made:  [http://ubuntuforums.org/showthread.php?t=1151464&page=2](http://ubuntuforums.org/showthread.php?t=1151464&page=2)  and follow the link he gives.  See if that makes sense to you.  You could ask him for help if you have questions.  Since he just set things up the memory will be fresh.

---

### Post by Silvenium on 2009-07-05
> **Favux said:**
> Hi Silvenium,

In Jaunty you don't want to use the xorg.conf.  Remove any entries you made in it.  You want to use HAL/.fdi.

See the post #16 that BCtom just made:  [http://ubuntuforums.org/showthread.php?t=1151464&page=2](http://ubuntuforums.org/showthread.php?t=1151464&page=2)  and follow the link he gives.  See if that makes sense to you.  You could ask him for help if you have questions.  Since he just set things up the memory will be fresh.


How can you delete them, and how do you easily create .fdi files? The only way I know how to is to do some code in the terminal, and it's really annoying! ...I believe, last time it said I didn't have the right permissions (but I am the only one who uses the computer).

---

### Post by Favux on 2009-07-05
Hi Silvenium,

To change system stuff you have to be the super user so in a terminal you type:
```
sudo
```
and it asks for you password.  When your using a graphical program like Text Editor (gedit) you use gksudo so in a terminal:
```
gksudo gedit
```
but you have to tell it what file you want and the path so for xorg.conf you type (or copy and paste):
```
gksudo gedit /etc/X11/xorg.conf
```
You could then post what's in it and I can show you what to comment out or remove.

Before you do anything to xorg.conf you want to back it up so you use the copy (cp) command like so:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Notice cp isn't graphical so you use sudo.

---

### Post by Silvenium on 2009-07-07
How do you easily create .fdi files, then? Especially in the policy/hal department. I can't just go and create a new folder in it, and even when I do it the terminal way it always doesn't want to save (not the right permissions)....
Sorry for being such a hinderance. You probably like to help in your free time, just not with such noobish things.

---

### Post by Favux on 2009-07-07
Hi Silvenium,

You do the exact same thing:
```
gksudo gedit /the/path/thefilename.fdi
```
Use Places (Nautilus) to figure out the path if needed.  They probably tell you where to place (the path) the .fdi.  Use the .fdi name they tell you to use.  This will open a blank, new file with the .fdi name.  Copy and paste the .fdi contents into it.  Save and close.  Presto a new file created in the right place.

Or you can use the cp (copy) command with sudo, also just like above.

---

