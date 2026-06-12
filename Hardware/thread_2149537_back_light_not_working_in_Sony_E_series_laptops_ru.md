---
title: "back light not working in Sony E series laptops running on Ubuntu 12.10"
date: 2013-05-29
forum: Hardware
---

### Post by chetancr9 on 2013-05-29
[COLOR=#000000]Hello All,[/COLOR]

[COLOR=#000000]I am running Ubuntu 12.10 on Sony E series Laptop[/COLOR]

[COLOR=#000000]Brightness Control is not working (Fn F5/F6 ) is not working[/COLOR]
[COLOR=#000000]The brightness remains same for all values (0-15)[/COLOR]

[COLOR=#000000]I tried to update from the grub it didn't work for me.[/COLOR]

[COLOR=#000000]Below is the output of commands acpi_listen with brightness + ans - function keys pressed. [/COLOR]

[COLOR=#000000]chetan@chetan-SVE15115ENB:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done[/COLOR]
[COLOR=#000000]/sys/class/backlight/acpi_video0[/COLOR]
[COLOR=#000000]0[/COLOR]
[COLOR=#000000]15[/COLOR]
[COLOR=#000000]chetan@chetan-SVE15115ENB:~$ acpi_listen[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 00000010[/COLOR]
[COLOR=#000000]video PEGP 00000081 00000000[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 0000003b[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 00000010[/COLOR]
[COLOR=#000000]video PEGP 00000081 00000000[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 0000003b[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 00000010[/COLOR]
[COLOR=#000000]video PEGP 00000081 00000000[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 0000003b[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 00000011[/COLOR]
[COLOR=#000000]video PEGP 00000081 00000000[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 0000003b[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 00000011[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 0000003b[/COLOR]
[COLOR=#000000]video PEGP 00000081 00000000[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 00000011[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 0000003b[/COLOR]
[COLOR=#000000]video PEGP 00000081 00000000[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 00000011[/COLOR]
[COLOR=#000000]video PEGP 00000081 00000000[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 0000003b[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 00000011[/COLOR]
[COLOR=#000000]video PEGP 00000081 00000000[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 0000003b[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 00000011[/COLOR]
[COLOR=#000000]video PEGP 00000081 00000000[/COLOR]
[COLOR=#000000]sonyl/hotkey SNC 00000001 0000003b[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 00000011[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 0000003b[/COLOR]
[COLOR=#000000]video PEGP 00000081 00000000[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 00000011[/COLOR]
[COLOR=#000000]video PEGP 00000081 00000000[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 0000003b[/COLOR]
[COLOR=#000000]sony/hotkey SNC 00000001 00000011[/COLOR]




[COLOR=#000000]Kindly help me to solve this problems


Thanks[/COLOR]

---

### Post by ohnonot on 2013-05-29
i think there's an acpi daemon for that, called "acpid". is it running?
is the screen blanking and switching off the backlight normally (screensaver)?
is there anything else that is not working?

---

