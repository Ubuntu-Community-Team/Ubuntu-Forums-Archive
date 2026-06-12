---
title: "Anyone having problem connecting Sixaxis trough USB?"
date: 2013-09-24
forum: Hardware
---

### Post by Pako Pako on 2013-09-24
In another thread here about users having connection difficulties with [the Sony Sixaxis over bluetooth]("http://ubuntuforums.org/showthread.php?t=1190061"). I'm having some difficulty with it over USB (made [a thread in the Gaming section]("http://ubuntuforums.org/showthread.php?t=2176381")).
[URL="http://ubuntuforums.org/showthread.php?t=2176381"]
[/URL]It's a Sony Navigation Controller and I've tested it (over USB) on a Xubuntu (12.04) machine and an android machine, but still having issues with my 11.04 laptop (it has 1 USB 2.0 port and no bluetooth).

Using *dmesg |grep Sony*, the controller comes up as:
```
input: Sony Navigation Controller as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input5
generic-usb 0003:054C:042F.0001: input,hidraw0: USB HID v1.11 Joystick [Sony Navigation Controller] on usb-0000:00:1d.0-2/input0
input: Sony Navigation Controller as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input9
generic-usb 0003:054C:042F.0002: input,hidraw0: USB HID v1.11 Joystick [Sony Navigation Controller] on usb-0000:00:1d.0-2/input0
input: Sony Navigation Controller as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input10
generic-usb 0003:054C:042F.0003: input,hidraw0: USB HID v1.11 Joystick [Sony Navigation Controller] on usb-0000:00:1d.0-2/input0
```

Running sixpair, I get an error message that *"No controller found on USB busses."* Nothing responds in jstest-gtk, though it also sees a Sony Navigation Controller connected. Running jstest-gtk before the controller is plugged in and hitting "Refresh" afterwards does nothing; I have to restart the program. Hitting "Mapping" also causes jstest-gtk to crash when the controller is plugged in.**[B]**[/B]
Is this just a limitation of Ubuntu 11.04? (Because users with 9.x and 10.x seem to have it working.) Is it a conflict of something I downloaded?

---

### Post by kostkon on 2013-09-25
11.04 is not supported any more, so it would be good if you could upgrade your laptop to 12.04, either by doing 11.04 -> 11.10 -> 12.04 (more info about EOL upgrades [here]("https://help.ubuntu.com/community/EOLUpgrades")), or with a clean install, and then use [AntiMicro]("http://www.webupd8.org/2013/09/map-keyboardmouse-input-to-your-gamepad.html") to set up your gamepad if you want.

Hope that helps.

---

### Post by Pako Pako on 2013-09-25
> **kostkon said:**
> 11.04 is not supported any more, so it would be good if you could upgrade your laptop to 12.04, either by doing 11.04 -> 11.10 -> 12.04 (more info about EOL upgrades [here]("https://help.ubuntu.com/community/EOLUpgrades")), or with a clean install,
Ah, that's always what I hear here, but upgrading is always problematic. How will GRUB handle it? How will I export all my settings? Will my iR and dial-up modem still work? Will I be able to dig out Gnome and ditch Unity/compiz?

It would be much more efficient to figure out a way to jerry-rig it together -- or be told outright it just won't take. (Because at the moment, all "drivers" seem to require later qt packages available only in 12.04 and newer.)

---

### Post by Yellow Pasque on 2013-09-25
[https://launchpad.net/~falk-t-j/+archive/qtsixa?field.series_filter=natty](https://launchpad.net/~falk-t-j/+archive/qtsixa?field.series_filter=natty)

If you don't like to upgrade, then don't use non-LTS releases.. (or use a rolling release where you only upgrade a bit at a time, and if something breaks, it's pretty easy to pinpoint what caused it).

---

### Post by Pako Pako on 2013-10-01
> **Temüjin said:**
> [https://launchpad.net/~falk-t-j/+archive/qtsixa?field.series_filter=natty](https://launchpad.net/~falk-t-j/+archive/qtsixa?field.series_filter=natty)
I've installed QtSixA before, on both 12.04 and 11.04;  aside from the nifty GUI, the controller still isn't detected via USB. With my 11.04 laptop, it also has an additional "no bluetooth available" message (because it's true) before going to the GUI that says "no devices found."

With 12.04, I had the option of using Gimx (which won't work in 11.04 due to library deficiencies) to recognize the controller, but not all programs were friendly with it. Emulators like bSNES and Kgen worked fine, but ZSNES and DeSmuME kept sensing the accelerometer or something and wouldn't allow me to properly edit the key-mappings.

> **Temüjin said:**
> If you don't like to upgrade... use a rolling release where you only upgrade a bit at a time, and if something breaks, it's pretty easy to pinpoint what caused it.
I'm not sure this means what I think it means. I can update *portions* of 11.04 to 12.04 LTS?

---

