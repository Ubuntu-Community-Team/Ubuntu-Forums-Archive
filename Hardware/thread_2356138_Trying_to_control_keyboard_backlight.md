---
title: "Trying to control keyboard backlight"
date: 2017-03-20
forum: Hardware
---

### Post by maneesha2 on 2017-03-20
[SIZE=2]I am trying to control the keyboard backlight on a Samsung Notebook 7 spin 15.6" FHD Touch NP740U5L-Y02US - i7-6500U - 12GB - 1TB ([https://www.amazon.com/dp/B01I4H1NNS/](https://www.amazon.com/dp/B01I4H1NNS/)) set up dual boot Windows 10 and Ubuntu 16.04.
I've posted all the details of what I've tried to do here ([http://askubuntu.com/questions/893473/manage-keyboard-backlight-on-dual-boot-system](http://askubuntu.com/questions/893473/manage-keyboard-backlight-on-dual-boot-system)) and have not gotten any responses.  Here's the current content of that post, for anyone who doesn't feel like clicking through:


---

[COLOR=#111111]Function Key + F9 is supposed to control keyboard backlight, but it does not do anything. The keyboard backlight is always on. I know that Ubuntu *can* control the backlight because when I shine a flashlight directly on the sensor, the backglight turns off. However when I remove the flashlight the backlight goes on again.
[/COLOR]
[COLOR=#111111]How can I manually control the backlight (either by the function key or other way)?[/COLOR]
[COLOR=#111111]
EDIT: I have looked a[/COLOR]t my /sys/class folder and in there I see a folder called backlight[COLOR=#111111] which has settings for the screen brightness, and a folder called leds which has settings indicator lights for things like caps lock. I thought the keyboard light settings might be in the leds folder but I don't see that there.[/COLOR]
[COLOR=#111111]Like I said, I know Ubuntu *can* control my keyboard light via the light sensor but I need to control it manually.[/COLOR]
[COLOR=#111111]
EDIT2: I have also tried xset led cycling through numbers 1-32. I have also tried editing the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line in /etc/default/grub all with no success.[/COLOR]
[COLOR=#111111]
EDIT3: I have tried installing the samsung tools package ([https://answers.launchpad.net/samsung-tools/+question/289901](https://answers.launchpad.net/samsung-tools/+question/289901)) but using that I get the message Backlight cannot be disabled[/COLOR]
[COLOR=#111111]
EDIT4: asus-keyboard-backlight.sh exists in /etc/acpi and the script includes reference to KEYS_DIR=/sys/class/leds/asus\:\:kbd_backlight but that directory does not exist.[/COLOR]
[COLOR=#111111]
EDIT5: If I run acpi_listen and hit Fn-F9 (that's supposed to be mapped to keyboard light) nothing happens. If I shine a light on the sensor, the keyboard light turns off but there is no output while running acpi_listen[/COLOR]


---[/SIZE]

---

### Post by Frogs Hair on 2017-03-21
> [SIZE=2][COLOR=#111111]I know that Ubuntu *can*  control the backlight because when I shine a flashlight directly on the  sensor, the backglight turns off. However when I remove the flashlight  the backlight goes on again.[/COLOR][/SIZE] The sensor working may have to do with the keyboard being powered up rather than the operating system. It is likely that the key-bindings pertain to a windows operating system and driver. Most key functions on my laptop don't apply when I boot into Ubuntu.

---

### Post by maneesha2 on 2017-03-21
> **Frogs Hair said:**
> The sensor working may have to do with the keyboard being powered up rather than the operating system. It is likely that the key-bindings pertain to a windows operating system and driver. Most key functions on my laptop don't apply when I boot into Ubuntu.

Thanks - I figured it had to do with Windows key bindings. I'm trying to figure out how I can map the keys in Ubuntu... it doesn't even have to be the same keys.  It really kills my battery to have the lights always on -- I'm really frustrated I can't find a way to turn the lights off.  I just want to mimic whatever is happening when I shine a light on the sensor.

---

