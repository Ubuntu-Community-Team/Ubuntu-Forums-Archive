---
title: "IOGEAR Mobile Digital Scribe G-PEN working w/ no buttons"
date: 2009-02-22
forum: Hardware
---

### Post by vbman11 on 2009-02-22
Hi all
I used this guide ([http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html)) along with the community docs to get my G Pen(see title) working up to the point with no buttons, I'm not even able to click on anything. Is there anyone that has this pen or any other pen that can help. I have tried Xinput commands and also tried xev to see if there was any output... nothing. Please Help!

---

### Post by kamronrpi on 2009-05-24
glad to hear another IOGEAR GPEN user.
[FONT=monospace]I hope I can catch up to you and then help you get the buttons to work.[/FONT]
I installed the deb from [http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html)
My device does not show up in:[B] [FONT=monospace]grep -i name /proc/bus/input/devices  
[/FONT][/B]I just get this list:
N: Name="Power Button (FF)"
N: Name="Lid Switch"
N: Name="Sleep Button (CM)"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="PC Speaker"
N: Name="Video Bus"
N: Name="ThinkPad Extra Buttons"
N: Name="SynPS/2 Synaptics TouchPad"
N: Name="TPPS/2 IBM TrackPoint"
But I do get this for the [FONT=monospace] lshal | less command:
udi = '/org/freedesktop/Hal/devices/usb_device_e20_100_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'  (string)
  info.product = 'NoteTaker FW Ver 2.05'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_e20_100_noserial'  (string)
  info.vendor = 'Pegasus Technologies Ltd.'  (string)
  linux.device_file = '/dev/bus/usb/003/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2'  (string)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 517  (0x205)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'NoteTaker FW Ver 2.05'  (string)
  usb_device.product_id = 256  (0x100)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'Pegasus Technologies Ltd.'  (string)
  usb_device.vendor_id = 3616  (0xe20)  (int)
  usb_device.version = 1.1 (1.1) (double)

[/FONT]I am a little confused what the device name should be for use in this line:
 <match key="info.product" contains="[COLOR=red]NAME OF YOUR TABLE OBTAINED FROM PREVIOUS STEP[/COLOR]">
When I put in [FONT=monospace]NoteTaker FW Ver 2.05 in the above line, no mouse control works or xournal either.  Then I tried the same thing for USB HID Interface, b/c I thought that may be the correct device.  No luck with that either.
[/FONT][FONT=monospace]I hope I can catch up to you and then help you get the buttons to work.
Configuring did not work either when I did:

Thanks
Kam
[/FONT][FONT=monospace]
[/FONT]

---

### Post by vbman11 on 2009-05-24
I have moved on to bigger and better things(mac osX), and i can't quite remember what i put in. You could try putting in the "pegasus..." entry. Im sorry i dont remember, but i might try again to get it to work in the future(just for thrills).

Sorry

---

