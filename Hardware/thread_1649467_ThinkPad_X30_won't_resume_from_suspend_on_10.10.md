---
title: "ThinkPad X30 won't resume from suspend on 10.10"
date: 2010-12-20
forum: Hardware
---

### Post by dtemp132 on 2010-12-20
I want ya'll to know that I've sunk an entire day into this, and I'm not posting at the first sign of trouble ;)

Running 10.10 with kernel 2.6.35-23 on a Thinkpad X30. The machine seems to work fine in all other respects, except it won't resume from sleep. Specifically, the computer seems to wake up but the screen does not turn back on. I've been searching for solutions all day and have tried a number of things, most found here: [http://ubuntuforums.org/showthread.php?t=1596545](http://ubuntuforums.org/showthread.php?t=1596545)

o) Tried pressing the FN key and F3/F4/F7/F12/Home/End
o) Tried pressing Ctrl+Alt and the F keys and backspace
o) Installed the package "hibernate"
o) Created /etc/X11/xorg.conf according to these instructions [[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html]](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html]) and added the "ForceEnablePipeA" according to this page [[http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume#Solution_for_ThinkPads_with_Intel_I830_Chipset]](http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume#Solution_for_ThinkPads_with_Intel_I830_Chipset])
o) I also created the file /etc/acpi/actions/sleep.sh and made it executable according to the last link above. I made the file have the same contents as the grey box. Not sure if I followed this suggestion correctly as this file didn't exist (there wasn't event the actions folder), but there is a /etc/acpi/sleep.sh that I didn't know how to exit properly to follow this suggestion (just append the lines at the end?)
o) Created /etc/pm/config.d/unload_module (file didn't exist) with just the line:
SUSPEND_MODULES="xhci"
o) In /etc/defaults/grub, changed GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX=”acpi_sleep=nonvs" and ran "sudo update-grub" and rebooted
o) I HAVEN'T been able to try booting into different kernels because I can't get my grub menu to come up, although I suspect this is an unrelated problem. This wouldn't be a solution anyway because I am giving this computer to someone who doesn't even know what kernels are and maintenance should be easy.

The screen isn't just "black", I can confirm the LCD backlight isn't on. I can tell the lock screen is working even though it isn't displayed, as I get a characteristic "thunk" from my speakers when I press the right arrow key.

The graphics chip is the Intel 830. The wireless card is an Intel WM3A2200BG with Dell branding. The machine works fine with WinXP.

---

### Post by Zanderist on 2011-03-01
> **dtemp132 said:**
> I want ya'll to know that I've sunk an entire day into this, and I'm not posting at the first sign of trouble ;)

Running 10.10 with kernel 2.6.35-23 on a Thinkpad X30. The machine seems to work fine in all other respects, except it won't resume from sleep. Specifically, the computer seems to wake up but the screen does not turn back on. I've been searching for solutions all day and have tried a number of things, most found here: [http://ubuntuforums.org/showthread.php?t=1596545](http://ubuntuforums.org/showthread.php?t=1596545)

o) Tried pressing the FN key and F3/F4/F7/F12/Home/End
o) Tried pressing Ctrl+Alt and the F keys and backspace
o) Installed the package "hibernate"
o) Created /etc/X11/xorg.conf according to these instructions [[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html]](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html]) and added the "ForceEnablePipeA" according to this page [[http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume#Solution_for_ThinkPads_with_Intel_I830_Chipset]](http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume#Solution_for_ThinkPads_with_Intel_I830_Chipset])
o) I also created the file /etc/acpi/actions/sleep.sh and made it executable according to the last link above. I made the file have the same contents as the grey box. Not sure if I followed this suggestion correctly as this file didn't exist (there wasn't event the actions folder), but there is a /etc/acpi/sleep.sh that I didn't know how to exit properly to follow this suggestion (just append the lines at the end?)
o) Created /etc/pm/config.d/unload_module (file didn't exist) with just the line:
SUSPEND_MODULES="xhci"
o) In /etc/defaults/grub, changed GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX=”acpi_sleep=nonvs" and ran "sudo update-grub" and rebooted
o) I HAVEN'T been able to try booting into different kernels because I can't get my grub menu to come up, although I suspect this is an unrelated problem. This wouldn't be a solution anyway because I am giving this computer to someone who doesn't even know what kernels are and maintenance should be easy.

The screen isn't just "black", I can confirm the LCD backlight isn't on. I can tell the lock screen is working even though it isn't displayed, as I get a characteristic "thunk" from my speakers when I press the right arrow key.

The graphics chip is the Intel 830. The wireless card is an Intel WM3A2200BG with Dell branding. The machine works fine with WinXP.

The same thing has been happening to me on my HP Pavilion dv6, only question I have is have you activated the video card driver?

I found when I deactivated it the problem would go away.

---

