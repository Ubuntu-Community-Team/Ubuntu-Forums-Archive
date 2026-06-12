---
title: "Asus Z53sc &quot;Ubuntu Jaunty&quot;; Backlight issues"
date: 2009-06-26
forum: Hardware
---

### Post by MegaDrive on 2009-06-26
Hey all,

I've been experiencing some problems with Ubuntu..
The backlight in Ubuntu is reported at "100%" but is not really at that brightness level.

Vista is at a bright 100% level and Ubuntus "maximum brightness" is about the equivalent of 75 ~ 90% brightness.

At bootup after leaving Vista, bootup into ubuntu goes totally normally until about half way through bootup into Ubuntu when the screen all of a sudden dims to a nearly unreadable level, making the login screen text nearly unreadable.

However once I log in it returns to "100% brightness" which in reality seems only about 75%, I can change the backlight levels absolutely fine but "100%" is stuck at this medium-high brightness level.

The screen dimming to 0% only happens when booting out of Vista into Ubuntu, if I reboot from Ubuntu into Ubuntu this never happens but screen brightness remains at this 75% level, no way to go to the maximum level.

I can use the brightness changing keys on my laptop and they work but again, I cannot go to true 100%


I've searched for any workaround or fix with no avail.
This problem never occured in Hardy.

Here is some information regarding my screen brightness, hopefully it helps.

```
 cat /proc/acpi/video/VGA/LCDD/brightness
levels:  0 1 2 3 4 5 6 7 8 9 10 11 12 13
current: 13

```
```

Generic Backlight Device
Property	Value
info.category	laptop_panel
info.subsystem	backlight
info.product	Generic Backlight Device
info.udi	/org/freedesktop/Hal/devices/computer_backlight
info.parent	/org/freedesktop/Hal/devices/computer
info.interfaces	org.freedesktop.Hal.Device.LaptopPanel
info.capabilities	laptop_panel
info.addons	hald-addon-generic-backlight
linux.hotplug_type	2
linux.subsystem	backlight
linux.sysfs_path	/sys/devices/virtual/backlight/acpi_video0
laptop_panel.num_levels	14
laptop_panel.brightness_in_hardware	False
laptop_panel.access_method	general 
```

I also forgot to mention that 
```
 [    1.378846] ACPI: Expecting a [Reference] package element, found type C 
```

Happens at bootup, if that is of any help.

Thanks for any help in advance,
Megadrive

---

### Post by MegaDrive on 2009-06-26
Bump.

---

### Post by MegaDrive on 2009-07-11
Bump. Anyone? D:

---

### Post by _WiLloW_ on 2009-07-15
Hello!

Try adding *'acpi_backlight=vendor'* kernel parameter to */boot/grub/menu.lst* kernel line:

```
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=* ro quiet splash **acpi_backlight=vendor** 
```
):P

---

### Post by MegaDrive on 2009-07-20
> **_WiLloW_ said:**
> Hello!

Try adding *'acpi_backlight=vendor'* kernel parameter to */boot/grub/menu.lst* kernel line:

```
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=* ro quiet splash **acpi_backlight=vendor** 
```
):P

Works perfect;
Thankyou!

---

### Post by ilario73 on 2009-08-12
It works perfectly also with my packard Bell laptop using jaunty.
Thanks mille

---

### Post by sloikas on 2009-08-19
Thx, you saved me from dark, i can see again :)

---

### Post by zzxop on 2010-02-04
> **_WiLloW_ said:**
> Hello!

Try adding *'acpi_backlight=vendor'* kernel parameter to */boot/grub/menu.lst* kernel line:

```
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=* ro quiet splash **acpi_backlight=vendor** 
```
):P

Thanks so much!!!! The brightness is the same from boot to desktop!!!,Thanks again!!!

---

### Post by amira-kitten on 2011-10-26
I know this is a really old thread but seenas I have the same problem I was hoping someone could help.

If I do the above and set the backlight to vendor the backlight works on full brightness and all problems with flickering disappear but my display will only work on 800x600.

If I use acpi_osi= then the flickering has gone, the resolution is right but the brightness is only about 50 to 60%. Although this is much more usable than having no backlight switched on at all (as it was with the original settings before I tried to fix it) I was wondering if there is a way of combining the 2 settings so the backlight works properly and the resolution stays right.

With grub set to vendor settings my monitor is recognized by KDE just as "VGA" with only the 800x600 option.

With any other grub settings I've tried the monitor is called "LVDS1" and has a choice of resolutions with 1024x600 being the appropriate setting for me.

My netbook is a Samsung N130 running 11.10

I hope you understand what I'm trying to explain here.

---

### Post by coffeecat on 2011-10-26
@amira-kitten, please start your own thread. You are running 11.10, and the thread title refers to the now unsupported 9.04 (Jaunty) which will not attract the answers you need.

Old thread - closed.

---

