---
title: "[SOLVED] Sony Vaio CR series Bluetooth problem"
date: 2008-09-03
forum: Hardware
---

### Post by AN@S on 2008-09-03
Hello, 
I have a problem with with my new Sony Vaio VGN-CR520 with the built-in bluetooth support. I have the blue icon at the top panel, but when I click on Browse Devices my phone is not recognized. Also when I try:

```
hcitool scan
Scanning ...
Inquiry failed: Connection timed out
```

I did a lot of googling but couldn't find a way to get it to work.

:confused:

---

### Post by IntuitiveNipple on 2008-09-03
What Bluetooth device does that Vaio have? Copy the results of these commands so we can see:
```

lsusb

 lshal | awk 'BEGIN{dev=""} $0 ~ /^udi =/ { if(dev != "" && origin != "") { } dev=$0; } $0 ~ /bluetooth_hci\.originating_device/ {origin=$0} END { split(origin, parts, " "); sys = sprintf("lshal -u %s", parts[3]); system(sys)}'

```
That last command looks (and is) complicated, but what it does is first identify any bluetooth interfaces, find the USB device that hosts them, and then reports the information for that USB device. It should show something that begins similar to this:
```

udi = '/org/freedesktop/Hal/devices/usb_device_44e_300d_01f4233a_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'hci_usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_44e_300d_01f4233a'  (string)
  info.product = 'USB Wireless Interface'  (string)

```

---

### Post by AN@S on 2008-09-04
Hi,

```
lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 05ca:1839 Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0458:0066 KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 044e:3012 Alps Electric Co., Ltd 
Bus 001 Device 005: ID 044e:3013 Alps Electric Co., Ltd 
Bus 001 Device 004: ID 044e:3010 Alps Electric Co., Ltd 
Bus 001 Device 003: ID 044e:3011 Alps Electric Co., Ltd 
Bus 001 Device 001: ID 0000:0000 
``` 

The second command:

```

udi = '/org/freedesktop/Hal/devices/usb_device_44e_3010_001E3DA3374C_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'hci_usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_44e_3010_001E3DA3374C'  (string)
  info.product = 'USB Wireless Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_44e_3010_001E3DA3374C_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 224  (0xe0)  (int)
  usb.device_protocol = 1  (0x1)  (int)
  usb.device_revision_bcd = 86  (0x56)  (int)
  usb.device_subclass = 1  (0x1)  (int)
  usb.interface.class = 224  (0xe0)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 1  (0x1)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 4  (0x4)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 4  (0x4)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Wireless Interface'  (string)
  usb.product_id = 12304  (0x3010)  (int)
  usb.serial = '001E3DA3374C'  (string)
  usb.speed = 12.0 (12) (double)
  usb.speed_bcd = 4608  (0x1200)  (int)
  usb.vendor = 'Alps Electric Co., Ltd'  (string)
  usb.vendor_id = 1102  (0x44e)  (int)
  usb.version = 2.0 (2) (double)
  usb.version_bcd = 512  (0x200)  (int)
```

---

### Post by IntuitiveNipple on 2008-09-04
I think the solution I used with another similar model will solve this. Try the instructions in [my comment to "Bluetooth problem in sony-vivo"](http://ubuntuforums.org/showpost.php?p=5706379&postcount=3) and let us know how it goes.

---

### Post by AN@S on 2008-09-04
WoooW thanks ... this works :guitar:

---

### Post by IntuitiveNipple on 2008-09-04
That's great :) Now I might recommend you investigate "[Blueman](http://blueman.tuxfamily.org/)", a Bluetooth  device manager that will blow your socks off! I've got the most recent release packaged in my PPA (see the link in the signature) if you want to try it.

Please mark the this thread as Solved.

---

### Post by tasomaniac on 2008-12-23
I have Sony Vaio CR510E laptop. It has Alps Bluetooh, I guess. My bluetooth also doesn't work in Ubuntu. I did what you said but it still didnt work. I also installed Blueman 0.6,

---

### Post by tasomaniac on 2009-01-02
I found this in a Gentoo linux forum and it works like a charm. :))

```
/usr/sbin/hciconfig hci0 reset
```

This thing you wrote doesn't work for me. I also add this in the startup.

---

### Post by maikito on 2009-01-18
i have a vgn-cr41s, and this last solution worked perfectly well on mine :D

thnkx!  :guitar:

---

### Post by oooh on 2009-01-19
Worked fine on me (hardy heron 8.04 and sony vaio fz21m)

Problem completelly solved on the following steps:

Install all packets one can find about Bluez and Obex in the Synaptic.
Modify the config file for bluetooth: /etc/bluetooth/hci.conf, modifying two lines:
security auto;
passkey "0000";
Restart the device doing: sudo /usr/sbin/hciconfig hci0 reset
Added the line "hciconfig hci0 reset" to the /etc/rc.local, so that it is restarted with ubuntu at startup
Restart
Now you can access it doing: hcitool scan so you can see devices around, or hciconfig -a, which gives you all information about your bluetooth adapter

---

### Post by panki on 2009-04-11
Works with Sony VGN-FZ440E on Jaunty.

---

### Post by müdit on 2009-08-11
where do u type these codes. imean in wich software or watever?

---

