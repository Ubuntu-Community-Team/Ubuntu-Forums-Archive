---
title: "help identifying keycode without xev"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by damagedspline on 2007-01-27
Hi, I'm trying to improve my laptop's "behavior" under linux by assign the extra keys to do what they are supposed to do.

for instance: the wireless activate/deactivate button. (i'm using acerhk to activate the wirelessled on a fujitsu laptop - it's working, just want to assign the key). well, the wireless activation button is not recognized under xev & i dont get any related message in dmesg.
i also tried showkey with no results.

how can i force the keycode detection (hopefully with no kernel recompilation)?

---

### Post by damagedspline on 2007-02-03
Ok, I tried recompile the kernel with ACPI_DEBUG but still no messages in dmesg when I press those unmapped keys.

I tried another approach which with I use xorg's evdev.
The acerhk driver is alo mapped as /sys/class/input/input2 & event1.

by adding the following the following to xorg:
```
Section "InputDevice"
Identifier "Acer HotKey"
Driver "evdev"
Option "CoreKeyboard"
Option "Device" "/dev/input/event9" #this should be that underlined name from 19-local.rules
EndSection
```

adding the next line to [ServerLayout]:
```
InputDevice "Acer HotKey"
```

and creating the following rule in udev /etc/udev/rules.d/19-local.rules :
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Acer hotkey driver", NAME="input/event9"
```

well, beside remapping the arrowkeys on my keyboard it had no effect... I guess acerhk only supplied the framework without suitable implementation... :(

---

### Post by damagedspline on 2007-02-06
Once again, I'm my own rescue.

I added a few lines of code to acerhk and now my wireless and fancy fan buttons are recognized as I wanted.

Who should I inform of this patch so it will be inserted into Fiesty? (it handles FSC Amilo A1xxx laptops)

---

### Post by _Stevie_ on 2008-01-14
hi damagedspline!

i got a fujitsu siemens laptop as well and wanted to ask, if enabling the acer hotkey driver will
also make work the LEDs on the laptop.

best,

stevie

---

