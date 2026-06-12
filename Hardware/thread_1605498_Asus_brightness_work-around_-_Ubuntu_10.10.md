---
title: "Asus brightness work-around - Ubuntu 10.10"
date: 2010-10-25
forum: Hardware
---

### Post by Shazbot89 on 2010-10-25
I have had problems with my Asus K60IJ Fn brightness (and applet) control. I have had this issue since 10.4 and sure many others have too. Finally found a work around that worked (many others did not).

This is confirmed for 10.10 on my Asus notebook.

Hope it will help you:

Source: [http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT#Screen_Brightness]("http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT#Screen_Brightness")

Work around:

> To activate the screen brightness keys first backup asus-brn-down.sh
```
sudo cp /etc/acpi/asus-brn-down.sh /etc/acpi/asus-brn-down.sh.backup
```
Then open asus-brn-down.sh with Gedit.
```
sudo gedit /etc/acpi/asus-brn-down.sh

```
Erase everything and paste the following inside.
```
#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0 
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_BRIGHTNESSDOWN

# added per http://forum.notebookreview.com/showpost.php?p=5665108&postcount=1235
#brightness=`echo $3 | sed 's/0000002//'`
#setpci -s 00:02.0 F4.B=${brightness}f

# added per mailing-list post
brightness=$((0x`setpci -s 00:02.0 F4.B`-16));
if [ $brightness -lt 0 ] ; then
   brightness=1;
fi
setpci -s 00:02.0 F4.B=`printf '%x' $brightness`;
```
Save and close.
Now backup asus-brn-up.sh
```
sudo cp /etc/acpi/asus-brn-up.sh /etc/acpi/asus-brn-up.sh.backup

```
Open asus-brn-up.sh with Gedit.
```
sudo gedit /etc/acpi/asus-brn-up.sh

```
Erase everything and paste the following inside.
```
#!/bin/sh
test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/key-constants

# DeviceConfig

if [ "$model" != "701" ] ; then
	# On an Eee PC (ASUSTeK model 701) the keys in the range handled by this
	# script have entirely different meanings. They are handled in separate
	# scripts.
	acpi_fakekey $KEY_BRIGHTNESSUP
fi

# added per http://forum.notebookreview.com/showpost.php?p=5665108&postcount=1235
#brightness=`echo $3 | sed 's/0000001//'`
#setpci -s 00:02.0 F4.B=${brightness}f

# added per mailing list post
# in /etc/asus_brn_up.sh
brightness=$((0x`setpci -s 00:02.0 F4.B`+16));
if [ $brightness -gt $((0xff)) ] ; then
  brightness=$((0xff));
fi
setpci -s 00:02.0 F4.B=`printf '%x' $brightness`;
```
Save and close.
Now you need to modify grub:
```
sudo gedit /etc/default/grub
```
Change your "GRUB_CMDLINE_LINUX_DEFAULT=" to the following:
```
GRUB_CMDLINE_LINUX_DEFAULT="i915.powersave=0 acpi_backlight=vendor vga=792 quiet splash""i915.powersave=0 acpi_backlight=vendor vga=792 quiet splash"
```
Now update your grub.cfg file:
```
sudo update-grub

```

Reboot to activate the screen brightness keys.

---

### Post by _pitch on 2011-01-06
Tnx!
That was exactly the help I was looking for.
:D

---

### Post by lamanabie on 2011-09-16
I am using Ubuntu 11.04. This script works on my ASUS UL30V perfeclty, but i have problems after suspend or hibernation ... Value of backlight is on maximum. How can I do that backlight value will be same before and after suspend/hibernation. Thanks.

---

### Post by lamanabie on 2011-09-16
> **lamanabie said:**
> I am using Ubuntu 11.04. This script works on my ASUS UL30V perfeclty, but i have problems after suspend or hibernation ... Value of backlight is on maximum. How can I do that backlight value will be same before and after suspend/hibernation. Thanks.

SOLVED by 
[https://bbs.archlinux.org/viewtopic.php?id=119014](https://bbs.archlinux.org/viewtopic.php?id=119014)
[https://wiki.archlinux.org/index.php/Pm-utils#Creating_your_own_hooks](https://wiki.archlinux.org/index.php/Pm-utils#Creating_your_own_hooks)

Anyway thanks ^^:guitar:

---

### Post by RascalAW on 2011-10-02
Awesome Workaround. worked with my Asus UL80..... but the backlight is off at half of the way of the backlight "status bar", can you explain me wich changes i have to do that the backlight is dimmed less per click???

---

### Post by Toz on 2011-10-02
The scripts are incrementing and decrementing the brightness by hexidecimal value 16:
```
brightness=$((0x`setpci -s 00:02.0 F4.B`[COLOR="Red"]-16[/COLOR]));

and

brightness=$((0x`setpci -s 00:02.0 F4.B`[COLOR="Red"]+16[/COLOR]));
```

You could try increasing/decreasing that value in half. Half of hexidecimal 16 is B. Therefore:
```
brightness=$((0x`setpci -s 00:02.0 F4.B`[COLOR="Red"]-B[/COLOR]));

and

brightness=$((0x`setpci -s 00:02.0 F4.B`[COLOR="Red"]+B[/COLOR]));
```

---

### Post by Shazbot89 on 2011-10-18
Going to have to try Toz's recommendation! Thank you Toz.
Will try and report back on results.

---

