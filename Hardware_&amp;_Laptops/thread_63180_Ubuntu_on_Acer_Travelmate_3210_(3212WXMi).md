---
title: "Ubuntu on Acer Travelmate 3210 (3212WXMi)"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by yaggo on 2005-09-07
I wrote about my experiences on installing Ubuntu Hoary on Acer Travelmate 3210 series laptop. There's also Linux compatibility chart. Currently the machine works pretty well with Linux, excluding Intel SpeedStep, which can't load due to broken ACPI data. Basic ACPI frequence scaling works, though.

[http://iki.fi/holster/linux_on_travelmate_3210](http://iki.fi/holster/linux_on_travelmate_3210)

If you are thinking about getting similar laptop or already have one, please check out that page and share you information.

---

### Post by cbudden on 2005-09-07
[QUOTE=yaggo]I wrote about my experiences on installing Ubuntu Hoary on Acer Travelmate 3210 series laptop. There's also Linux compatibility chart. Currently the machine works pretty well with Linux, excluding Intel SpeedStep, which can't load due to broken ACPI data. Basic ACPI frequence scaling works, though.

[http://iki.fi/holster/linux_on_travelmate_3210](http://iki.fi/holster/linux_on_travelmate_3210)

If you are thinking about getting similar laptop or already have one, please check out that page and share you information.[/QUOTE]
 Regarding your hotkeys.  My Acer 4500 hotkeys needed configuring in System -> prefs -. keyboard shortcuts.  Then i set the browser button to launch browser.

---

### Post by yaggo on 2005-09-08
> Regarding your hotkeys. My Acer 4500 hotkeys needed configuring in System -> prefs -. keyboard shortcuts. Then i set the browser button to launch browser. 

The 3210 is a bit different case. Since hotkeys doesn't produce any scancodes (except the dollar/euro keys), you need special driver to enable them. (hkacer, which doesn't support this model.)

---

### Post by daij on 2005-09-16
I have the same laptop so I thought I should add a few comments.

**CARD READER**
The card reader is not a built-in USB-device, it's a Ene Technology controller with a PCI-interface, and no Linux driver for this device exists, yet, so we can just forget this device.  :(

**BLUETOOTH**
Bluetooth works very well indeed (this is a USB-device), and I can send files to/from the laptop to my phone, as well as connect via GPRS (EDGE).

**WLAN**
Sometimes during boot, the following messages appear:
```

kernel: ipw2200: Fatal error
kernel: ipw2200: Start IPW Error Log Dump:
kernel: ipw2200: Status: 0x00000100, Config: 00000142
kernel: ipw2200: Start IPW Event Log Dump:

```
The card works though, and this message seems to have stopped appearing after upgrading to breezy.

**CPU**
The centrino-speedstep module in Hoary doesn't support dothan processors, the one in breezy does, but I haven't noticed any change in behaviour...

**HOTKEYS**
Except for the four "special" hotkeys and FN-F1..F3, all "hotkeys" (sound volume, mute, etc) seems to be working, at least in breezy, without acerhk-driver.

BTW: How do you control the mailled? I've tried loading the acerhk module with force_series=250 and echoing 1 to /proc/driver/acerhk/led, without any luck...

--
daij

---

