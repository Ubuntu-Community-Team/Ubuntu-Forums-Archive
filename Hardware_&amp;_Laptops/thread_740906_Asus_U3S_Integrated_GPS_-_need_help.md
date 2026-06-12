---
title: "Asus U3S Integrated GPS - need help"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by n3utrino on 2008-03-31
Hi everyone.

I have an asus u3s with an integrated gps chip. But im a little lost i cannot get it working.
And i do not even know wich device i have to look for. Usb? pci?
All i found out is one suspicious usb device which looks like this.

```
udi = '/org/freedesktop/Hal/devices/usb_device_471_82d_noserial'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'  (string)
  info.product = 'Unknown (0x082d)'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_471_82d_noserial'  (string)
  info.vendor = 'Philips'  (string)
  linux.device_file = '/dev/bus/usb/007/003'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb7/7-6'  (string)
  usb_device.bus_number = 7  (0x7)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 255  (0xff)  (int)
  usb_device.device_protocol = 255  (0xff)  (int)
  usb_device.device_revision_bcd = 3  (0x3)  (int)
  usb_device.device_subclass = 255  (0xff)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 3  (0x3)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb7/7-6'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product_id = 2093  (0x82d)  (int)
  usb_device.speed = 480.0 (480) (double)
  usb_device.speed_bcd = 294912  (0x48000)  (int)
  usb_device.vendor = 'Philips'  (string)
  usb_device.vendor_id = 1137  (0x471)  (int)
  usb_device.version = 2.0 (2) (double)
  usb_device.version_bcd = 512  (0x200)  (int)


```


Anyone any suggestions?

cheerio n3utrino

---

### Post by n3utrino on 2008-03-31
i tried to connect gpsd to /dev/bus/usb/007/003
and it returns no error but seems not to work.

can anyone confirm that the Philips Device above is actually the gps?

greez n3utrino

---

### Post by n3utrino on 2008-03-31
I checked [http://www.linux-usb.org/](http://www.linux-usb.org/) and the device id 082d is not listed under
Philips so still not sure.

So id wrote an email to Philips, maybe they know more.... i doubt it ;-)

---

### Post by n3utrino on 2008-04-01
i came across some posts about a Company called NXP that belongs to philips and apparently is the manufacturer of the gps. so the above listed device might be the right one.... i am searching further

---

### Post by n3utrino on 2008-04-04
I received an answer from NXP.

> 
 - Meines Wissens ist der Chip von Maxim, die "Spot GPS Software" von
NXP Software:
 [http://www.maxim-ic.com/products/wireless/gps/max2741.cfm?CMP=490](http://www.maxim-ic.com/products/wireless/gps/max2741.cfm?CMP=490)
 [http://www.mwrf.com/Articles/ArticleID/14303/14303.html](http://www.mwrf.com/Articles/ArticleID/14303/14303.html)
 [http://datasheets.maxim-ic.com/en/ds/MAX2741.pdf](http://datasheets.maxim-ic.com/en/ds/MAX2741.pdf)

 - Es ist keine (freie) Linux-Version dieser Software erhältlich.
 - Der Treiber für Windows macht eine USB zu Seriell Wandlung für die
Kommunikation mit dem Maxim Receiver
 - Die Spot Software erledigt vollständig die Verrechnung der Rohdaten
des Maxim Receivers
 - Es wäre also nötig, eine komplette Software zu schreiben die so
etwas machen kann.

 Mit freundlichem Gruß

 NXP Support

It seems like someone has to do some coding....

---

### Post by satauros on 2008-07-02
whoa nevermind

---

