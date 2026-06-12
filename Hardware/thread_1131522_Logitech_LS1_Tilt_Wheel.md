---
title: "Logitech LS1 Tilt Wheel"
date: 2009-04-20
forum: Hardware
---

### Post by MoonBlossom on 2009-04-20
Hi,

I'm trying to configure my Logitech LS1 mouse to use the tilt wheel buttons. The problem I'm having is "xev | grep button" is not detecting the buttons. I made this Hal profile after reading the Ubuntu Wiki:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.mouse">
	<merge key="input.x11_driver" type="string">evdev</merge>
	<!-- Logitech tweaks -->
	<match key="@input.originating_device:usb.vendor_id" int="0x46d">
	  <match key="@input.originating_device:usb.product_id" int="0xc062">
	      <merge key="input.x11_options.Buttons" type="string">7</merge>
	      <merge key="input.x11_options.ZAxisMapping" type="integer">4 5 6 7</merge>
	  </match>
	</match>
    </match>
  </device>
</deviceinfo>
```

I get the same results, no tilt buttons :(

Btnx was able to detect my mouse buttons but the application no longer works on newer Ubuntu versions.

Please help,

Thank you :popcorn:

---

### Post by MoonBlossom on 2009-04-30
Somebody knows? :confused:

---

