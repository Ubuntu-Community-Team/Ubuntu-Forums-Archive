---
title: "Laptop Brightness Hotkeys not working (HAL) [Averatec 4600]"
date: 2008-09-01
forum: Hardware
---

### Post by gse on 2008-09-01
Hi all. 

I have a problem with laptop brightness adjustment. 

In detail: I have a new Averatec 4600 (GA: Intel GMX3100) running Ubuntu 8.04 (hal 0.5.11, hal-info 20080601). 

The laptop starts usually with lowest brightness (0) and does not memorize a change. 

The brightness can manually be changed via  

```
sudo echo -n 7 > /sys/devices/virtual/backlight/acpi_video0/brightness
```
or 
```
sudo echo -n 100 > /proc/acpi/video/GFX0/DD02/brightness
```
 but will be reset after each Xserver restart.

The respectable keys Fn-F7 and Fn-F8 for brighntess-up and -down are _not_ working. 
The command ```
/usr/bin/lshal -m
``` does not show anything when Fn-F7 or Fn-F8 is pressed. 

The command 
```
sudo /usr/lib/hal/scripts/hal-system-lcd-set-brightness
```
throws the error ".: 10: hal-functions: not found" where line 10 is ". hal-functions".
Interestingly, other comparable scripts in the same directory do not throw this error.

The above-mentionned scripts are used for brightness adjustment (according to lshal):

```
udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.capabilities = {'laptop_panel'} (string list)
  info.category = 'laptop_panel'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.LaptopPanel'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic Backlight Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'  (string)
  laptop_panel.access_method = 'general'  (string)
  laptop_panel.brightness_in_hardware = false  (bool)
  laptop_panel.num_levels = 8  (0x8)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'backlight'  (string)
  linux.sysfs_path = '/sys/devices/virtual/backlight/acpi_video0'  (string)
  org.freedesktop.Hal.Device.LaptopPanel.method_argnames = {'brightness_value', ''} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_execpaths = {'hal-system-lcd-set-brightness', 'hal-system-lcd-get-brightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_names = {'SetBrightness', 'GetBrightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_signatures = {'i', ''} (string list)

```

Has anyone an idea what to do or where to start? 
Thank you very much in advance for your help and time!

Kind Regards,
Greg

---

### Post by nicedude on 2008-09-01
The brightness keys are usually controlled by the BIOS I think and mine work in any OS, although my special keys ( email, web etc ) do not as they were ment to be controlled by a windows application. As for a solution since you have a command that changes it to a setting you can use is to make a simple script of the command and place it in you startup scripts folder so it is executed on each bootup.

---

### Post by gse on 2008-09-01
Nicedude, thank you very much for your hint. Your proposal is the quick and dirty hack I will apply if a more sustainable approach is not findable. In the first line I search for a fix of the cause, not only of the symptom. In the end this will ideally be reported upstream such that other users profit.

Nevertheless, thank you very much for your advice.

Kind Regards,
Greg

---

### Post by garytr23 on 2008-11-10
I have a thinkpad sl300, and I'm trying to track down the way this brightness thingy works with gnome-power-manager and hal.. as mine and everyone else's brightness controls are really messed up.  Have you found any resources for this? 

My brightness keys work, but on all these thinkpad models they are reversed for some reason.  I can set brightness with them clumsily, but not all settings are available.  Eventually i want to fix the volume buttons that don't do anything, too, as I don't want to wait a year for someone else to do it.

"echo 85 | sudo tee /proc/acpi/video/VGA/LCDD/brightness" does the trick..

and 

"gary@gary-laptop:~$ cat /proc/acpi/video/VGA/LCDD/brightness 
levels:  100 90 85 80 75 70 65 60 55 50 45 40 35 30 25 20
current: 85"

If i disable gnome-power-manager, I get only 2 very dim settings in correct order that i can do with my buttons... also strange.

---

