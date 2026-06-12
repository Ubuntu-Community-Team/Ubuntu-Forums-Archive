---
title: "Brightness sliders missing in gnome-power-manager preferences"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by rgwzlfw on 2006-08-27
I have a Compaq V2000 laptop, running fully updated dapper.

When I enter the gnome-power-manager preferences screen, I cannot see the Brightness sliders on either the AC or Battery option screens, as described in the gnome help pages, and on [this page.]("http://www.gnome.org/projects/gnome-power-manager/gpp.html") All other options work fine. The keyboard shortcuts for changing the panel brightness work fine, however, so I am confident that my hardware supports changing the brightness.

I have tried reinstalling gnome-power-manager, HAL, dbus, and libnotify from packages, but not from source.

Does anyone have a solution? I can dim the panel manually but it is very irritating to do so as I use the laptop on the move a lot and am constantly plugging it in and unplugging it. Also it would be nice to have the screen dim nicely after a few minutes of idling, like on my mac...

Sorry if this topic has been covered before; I have searched extensively and have not found any relevant information.

---

### Post by ysse on 2006-08-27
I honestly did not know that there were sliders like that!

But like most things Gnome, settings that aren't visible by default can be changed in gconf-editor. Press Alt-F2 and enter ```
gconf-editor
``` to start it. Navigate to apps/gnome-power-manager, and in the right pane you will find the keys "ac_brightness" and "battery_brightness". They have valid values from 0 to 100.

But whether they actually will do anything for you I don't know. On my system (Fujitsu-Siemens Amilo Si 1520) nothing happens when I change those key values. I have the ordinary keyboard shortcuts working (BIOS?), and the panel brightness changes when I switch between AC and battery power. Maybe that function overrides the gnome-power-manager settings?

Sorry I can't be more specific.

---

### Post by rgwzlfw on 2006-08-27
I noticed those keys you mention before I posted, but changing them didn't do anything, and settings such as "dim_on_idle" are on by default, but do not appear to have any effect. I think tomorrow I will try compiling and installing the latest HAL and gnome-power-manager.

---

### Post by rgwzlfw on 2006-08-28
Compiling the latest HAL and g-p-m from source didn't change anything. New options were available in the new g-p-m, but nothing relating to brightness. The documentation suggests that read-only gcontrol keys might be the problem, but all the relevant keys are writable. Perhaps my hardware just doesn't support this functionality. Pity.

---

### Post by hughsient on 2006-10-27
> **rgwzlfw said:**
> Perhaps my hardware just doesn't support this functionality. Pity.

Yup, sounds like you have hardwired brightness support. Can you change the brightness using software in Windows? I'm guessing not. One way to check linux software support is to do "lshal | grep brightness".

Richard Hughes.

---

### Post by GoPool on 2007-10-16
I am also having this problem. I remember being able to set the display brightness level in the gnome power manager window, but now it is missing. I probably thought that it was never there and I was just dreaming, until I found an image online that shows Gnome power manager using the brightness slider. I cannot see the slider on my Acer Ferrari 3400 running Feisty, or my IBM T40 running Gusty RC. I can set these values in config editor --->apps-->gdm, but it is easier and more efficient to set display setting in gnome power manager. Does anyone out there know how to fix this problem?


[IMG]http://people.freedesktop.org/~david/g-p-m-prefer-power-savings.png[/IMG]

UPDATE:
I fixed in my Thinkpad by doing the following.
1. In the file 
```
/etc/modprobe.d/thinkpad_acpi.modprobe
``` change 
```
options thinkpad_acpi hotkey=enable,0xffff8f experimental=1
``` to 
```
options thinkpad_acpi hotkey=enable,0xffff experimental=1 fan_control=1
```

2. In the file 
```
/etc/modules
``` add this line ```
thinkpad_acpi hotkey=enable,0xffff experimental=1 fan_control=1
```

After these changes, the brightness applet should work, there is also a display on the screen whenever the brightness level is changed, and you should also be able to see the brightness sliders in gnome-power-manager that works.

---

### Post by craigtyson on 2007-12-05
GoPool

Cheers This works on my IBM X31

Exelent

---

