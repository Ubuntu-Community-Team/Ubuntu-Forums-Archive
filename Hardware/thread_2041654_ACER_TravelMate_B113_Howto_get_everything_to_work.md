---
title: "ACER TravelMate B113: Howto get everything to work"
date: 2012-08-13
forum: Hardware
---

### Post by nexero on 2012-08-13
Hey there!
As I bought a new Acer TravelMate B113 for my girlfriend and I ran into some issues, here is what I figured out:

[SIZE="4"]Issues after a clean install:[/SIZE]
**1)** Fn-Brightness and Ubuntu internal brightness do not work
**2)** No powersaving optimizations
**3)** No proper right click support for clickpad and no proper palm detection
**4)** No external support microphone or combined headset-plugs

[SIZE="4"]Solutions:

[/SIZE][SIZE="3"]**1)**[/SIZE]  Fn-Brightness and Ubuntu internal brightness do not work:

Add ```
acpi_backlight=vendor
``` to **/etc/default/grub** in the section **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash *acpi_backlight=vendor*"** and execute ```
sudo update-grub && sudo reboot
```.

[SIZE="3"]**2)**[/SIZE] No powersaving optimizations:

Again, edit **/etc/default/grub** and add 
```
pcie_aspm=force i915.i915_enable_fbc=1 drm.vblankoffdelay=1 i915.semaphores=1 i915.lvds_downclock=1 nmi_watchdog=0 acpi_backlight=vendor
```
in the section **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash *pcie_aspm=force i915.i915_enable_fbc=1 drm.vblankoffdelay=1 i915.semaphores=1 i915.lvds_downclock=1 nmi_watchdog=0 acpi_backlight=vendor*"** and execute this: 
```
sudo update-grub && sudo reboot
```

Execute this to get ALPM to work:

```
echo SATA_ALPM_ENABLE=true | sudo tee /etc/pm/config.d/sata_alpm
```

Create **/etc/udev/rules.d/10-runtime-pm.rules** with root permission:
```
SUBSYSTEM!="pci", GOTO="power_runtime_rules_end"
ACTION!="add", GOTO="power_runtime_rules_end"

KERNEL=="????:??:??.?"
PROGRAM="/bin/sleep 0.1"

ATTR{power/control}=="*", ATTR{power/control}="auto"

LABEL="power_runtime_rules_end"
```


[SIZE="3"]**3)**[/SIZE] No proper right click support for clickpad:

Create a a new folder and a new file:
```
sudo mkdir /etc/X11/xorg.conf.d/ && sudo nano /etc/X11/xorg.conf.d/51-clickpad.conf
```
Paste this into your new file:
```
Section "InputClass
Identifier "Default clickpad buttons"
MatchDriver "synaptics"
Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"

EndSection
```

Execute this in a terminal once and never enable the setting "System Settings > Mouse & Touchpad > Touchpad > Disable touchpad while typing" again:
```
gsettings set org.gnome.settings-daemon.peripherals.touchpad disable-while-typing false
```
Add a new entry to your startup programs, on Unity desktop it can be done this way:
Run "System Settings > Startup Applications > Add" and add 
```
syndaemon -i 1.7 -d -t -K
```
You might want to edit the value **-i 1.7**, as it defines how long tapping would be disabled after stopping typing in seconds.
Needs a reboot to take effect.

[SIZE="3"]**4)**[/SIZE] No external support microphone or combined headset-plugs:

Type this into a terminal:

```
echo options snd-hda-intel model=laptop-dmic | sudo tee -a /etc/modprobe.d/alsa-base.conf
```



[SIZE="4"]**Thats it!** 
Everything else seems to works out of the box.[/SIZE]

---

### Post by nexero on 2012-08-16
Created a wiki page:

**[Acer TravelMate B113]("https://help.ubuntu.com/community/AcerTravelMateB113")**

Feel free to improve it!

---

### Post by johambros on 2013-02-27
Hello nexero
Thanks for your help this far.

I installed Xubuntu on Travelmate B113.
I can add two informations concerning Xubuntu:

1) Clickpad corners to senitive:
Solution under: [http://www.theorangenotebook.com/2012/02/call-for-testing-clickpad.html](http://www.theorangenotebook.com/2012/02/call-for-testing-clickpad.html) (only step 1 and step 2)

2) Set Display to less brightness at startup. Solution under [http://forum.ubuntuusers.de/topic/bildschirmhelligkeit-dauerhaft-einstellen/#post-3338502](http://forum.ubuntuusers.de/topic/bildschirmhelligkeit-dauerhaft-einstellen/#post-3338502) (Install tool "xbacklight")


But I encounter 2 problems I cannot solve, although I am searching for a solution since about 2 weeks now.

1) Bluetooth does not work. 
Blueman showes up in the taskbar but "adapter" and "devices" are greyed out. Installed blueZ:
lspci | grep -i bluetooth gives no result
hcitool dev gives o result
hcitool scan gives "no device"
lsusb | grep Bluetooth gives no result
lsmod | grep bluetooth gives "bluetooth   180153 10 bnep,rfcomm"

2) External Mic: I followed your advice but the result is that afterwards the internal mic input only captures white noise at a very high level.
I tried every thinkable setting in alsa and pulse. Also deleting all settings in pulse and re-installing alsa. When removing the line "options snd-hda-intel model=laptop-dmic" the internal mic works fine again.


Maybe you can help? I would be very thankful.
And sorry for my bad english :)
Johannes

---

### Post by johambros on 2013-02-28
Ok, now I found out why bluetooth didn't work for me.
It's the Fn+F3 switch. This switch does not only switch wlan but also bluetooth!

 Unfortunately the on/off-state of bluetooth is not displayed so it took several days of research for me to figure that out.
Fn+F3 toggles between the following states: wlan on, bt off / wlan on, bt on / wlan off, bt on / wlan off, bt off

Does anyone need the bluetooth-dongle I ordered? ;)

---

