---
title: "Finepoint stylus FDI help"
date: 2008-11-17
forum: Hardware
---

### Post by ace214 on 2008-11-17
I'm trying to set up my Finepoint stylus on my Gateway cx2619 using the FDI method in Intrepid, because when I use xorg.conf it makes my screen do funny things on shut down. I created a /etc/hal/fdi/policy/fpit.fdi which contains:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input">
   <match key="info.product" containts="PnP Device (FPI2004)">
    <merge key="input.x11_driver" type="string">fpit</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
    <merge key="input.x11_options.InvertY" type="string">true</merge>
    <merge key="input.x11_options.MaximumXPositon" type="integer">12550</merge>
    <merge key="input.x11_options.MaximumYPositon" type="integer">7650</merge>
    <merge key="input.x11_options.MinimumXPositon" type="integer">400</merge>
    <merge key="input.x11_options.MinimumYPositon" type="integer">400</merge>
    <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
    <merge key="input.x11_options.TrackRandR" type="string">true</merge>
   </match>
  </match>
 </device>
</deviceinfo>
```

because I used to have an xorg configuration that was:
```
Section "InputDevice"
	Identifier	"Tablet"
	Driver		"fpit"
	Option		"Device"		"/dev/ttyS0"
	Option		"InvertY"
	Option		"MaximumXPosition"	"12550"
	Option		"MaximumYPosition"	"7650"
	Option		"MinimumXPosition"	"400"
	Option		"MinimumYPosition"	"400"
	Option		"SendCoreEvents"	"True"
	Option		"TrackRandR"
EndSection
```

and my lshal reads this:
```
udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'
  info.callouts.add = {'hal-system-setserial'} (string list)
  info.capabilities = {'input', 'input.tablet', 'input.tablet.tabletPC'} (string
 list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (FPI2004)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'  (string)
  input.device.set = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.id = 'FPI2004'  (string)
  pnp.serial.baud_base = 38400  (0x9600)  (int)
  pnp.serial.irq = 4  (0x4)  (int)
  pnp.serial.port = '0x3f8'  (string)
```

Except the pen never seems to initialize or transfer to xinput. The only thing that the log says in regards to the device is a setserial line being run by hal. The tablet worked fine when I only had it running through xorg.conf. It just screwed up my shutdown process.

Thanks for any help.

---

