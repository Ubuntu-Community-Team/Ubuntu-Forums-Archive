---
title: "Compaq Evo N800V Backlight problem"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by svennils on 2007-04-13
Hi,

After 3 years of Slackware on my Evo, i switched to Ubuntu edgy 1 month ago.
Now everything is running fine, suspend works for the first time, and the intel wlan too.
The only thing i cannot get to work, is the FN+F7/F8 keys for the lcd backlight adjustment. 
When pressing the lid close button, the backlight tones down smoothly, unlike in bios or windows or slack, where it was turned off the same second the button was pressed. So edgy has some sort of control of the brightness. When running XEV, the function keys Fn+f7/f8 do not return any value. 
Obvoiusly the bios handles them directly, and passes an acpi event to the kernel. Sleep button(fn+f3) works. Bluetooth on/off(fn+f2) also, and it doesent generate xev events either. 
The 2 threads here concerning an evo 610 mentioned a trip into gconf-editor, but adjusting the ac and battery brightness values there did nothing for me either. 
So exactly where is the kernel interfacing with the acpi bios in the brightness issue? 
The bios obviously gets the signal from the buttons, and passes it on, but there it stops. For now the laptop works fine, but on battery i'd like to turn down the brightness to conserve power. And at night, 100% is a bit bright to me.
Oh, the syslog does not report anything on those buttons either. The 3 unassigned mail, search, and info buttons below the screen are generating syslog events.
Any suggestions?

---

