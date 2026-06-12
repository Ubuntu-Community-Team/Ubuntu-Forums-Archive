---
title: "Can't change my brightness"
date: 2016-06-14
forum: Hardware
---

### Post by Grace_Topham on 2016-06-14
[FONT=Arial]Dell Inspiron 14 3452[/FONT]
[FONT=Arial]Lubuntu 16.0.4[/FONT]

[FONT=Arial]I’m unable to change my brightness using my keyboard keys - tried everything including [/FONT][FONT=Arial]xbacklight[/FONT][FONT=Arial]. Is there a way I can install a new keyboard driver?[/FONT]

---

### Post by Enkouyami on 2016-06-14
The keyboard driver isn't the problem.

---

### Post by Grace_Topham on 2016-06-15
Any idea of what it is, then?

---

### Post by Enkouyami on 2016-06-16
> **Grace_Topham said:**
> Any idea of what it is, then?
Some settings relating to brightness that Ubuntu didn't correctly set.

Try *[this]("https://askubuntu.com/a/573866")* (Fix #1):
 
[LIST=1]
[*]Open a terminal (Ctrl + Alt + T) and the following command below to know what video card is used for the backlight/brightness:
  ```
ls /sys/class/backlight/
```
  If your graphics card is Intel, you can proceed with *fix #1* below. 
[*]Run the command below to create the following configuration file, if it does not exist:
```
if [ ! -e /usr/share/X11/xorg.conf.d/20-intel.conf ]; then sudo touch /usr/share/X11/xorg.conf.d/20-intel.conf; else echo "That file exist, so continue to edit it with a text editor"; fi
```
  Now we need to edit this file; you can use any editor be it a terminal one or graphical. 
[*]Open the with 
  ```
sudo xdg-open '/usr/share/X11/xorg.conf.d/20-intel.conf'
``` and add the following lines to this file:
```
Section "Device"
    Identifier  "card0"
    Driver      "intel"
    Option      "Backlight"  "intel_backlight"        
    BusID       "PCI:0:2:0"
EndSection

```
Save it and close the editor. 
[*]Log out and log in back. The brightness control should be working through function keys now. 
[/LIST]
[B]

 and if it doesn't solve the problem, try *[that]("https://askubuntu.com/a/228835")* (Fix 2):[/B]
change the /etc/default/grub file as follows:

[LIST=1]
[*]Open a terminal (Ctrl + Alt + T) and run ```
sudo xdg-open '/etc/default/grub'
``` 
[*]Find the line: > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and modify it to one of the following: 
[*]> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

[B]or
[/B]
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux
acpi_backlight=vendor" **(try this if the first one doesn't work)** 
[*]Save and close your editor. 
[*]Then run the command ```
sudo update-grub
``` 
[*]Reboot your pc. 
[/LIST]

---

