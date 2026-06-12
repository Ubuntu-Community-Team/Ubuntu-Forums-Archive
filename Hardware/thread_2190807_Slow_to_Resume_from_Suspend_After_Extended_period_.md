---
title: "Slow to Resume from Suspend After Extended period of sleep"
date: 2013-11-29
forum: Hardware
---

### Post by kschiff on 2013-11-29
Am running Gnome Ubuntu 13.04 on a Thinkpad X230 with the "VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)" graphics card. I have 16 GB of RAM and an SSD drive. I do NOT have a swap partition.

If I suspect my system, it immediately goes to sleep. If I resume within a few minutes, or perhaps as long as 1/2 hour later (open the lid) it will briefly display the last active screen, but then bring up the lock screen, and then back to password/login screen. This works quickly with no issue. If I let the system sleep for an hour or more, resuming will once again bring up the last active screen, but it will appear frozen. While it is in this state, I can see the hard drive light blinking, but keyboard or mouse movement have no effect. If I wait a few minutes, the system will eventually make it back to the lock screen, and I can enter my password and be active in my previous session.

Not sure the best way to troubleshoot this... With the SSD, I have mostly avoided suspend because cold boot times are very quick; however, it would be useful if "suspend" was a more reliable option.

Any assistance is appreciated.

---

### Post by tgalati4 on 2013-11-29
Do you have the file /etc/default/acpi-support?  If so, take a look through it and change one switch at a time.  Take notes.  But first, check the BIOS power management for any display-related settings.  It could be as simple as an energy-saver setting that turns off the video hardware after an hour.  Set to "never" and see if that fixes it.

---

### Post by kschiff on 2013-11-30
I do have that file, but before I mucked with it I checked BIOS settings... I turned off anything I had that was not specific to my running hardware, but also "Wake on LAN." I will report back, but I think that may have done it. I put the machine to sleep at bedtime and it woke quickly this morning...

---

### Post by RadiantPhoenix on 2014-05-15
I think I have a similar problem in Ubuntu 12.04 x64 on my Thinkpad W500, and I have some System Monitor output to show:

Normal behavior: [ATTACH=CONFIG]253181[/ATTACH] (actual screenshot)
Bad behavior: [ATTACH=CONFIG]253182[/ATTACH] (faked because the system is running too slowly to screenshot)
Note the lack of memory cache, the falling memory usage, and the high IOWait. (Sometimes some memory cache happens, but it swiftly disappears)

This happens after sleep "sometimes". I'm not actually sure if it's only after extended sleep, but the OP's symptoms seem to match mine.

The way I deal with the problem is to go to the CLI with CTRL+ALT+F1, kill my high-memory-usage programs (Firefox, Thunderbird, and sometimes Nautilus and Freemind), then CTRL+ALT+F7 back to the GUI, and it will get back to full speed quickly.

I don't feel comfortable fiddling around with the BIOS without specific instructions and an understanding of what's going wrong.

EDIT: Something I'm not sure was clear is that killing Firefox and Thunderbird and then restarting them is *faster* than waiting for the system to fix itself "naturally".

EDIT 2: This apparently is not limited to happening in Sleep, because it just happened while the computer was running:
[list=1][*] Memory usage was at about 50% (2GB), Memory cache filled the rest of the bar
[*] Memory cache disappeared
[*] IOWait
[*] Computer suddenly became slow
[*] Memory usage was slowly declining.[/list]

Had to kill Firefox and Thunderbird, but closed Rhythmbox and Transmission "normally"

---

