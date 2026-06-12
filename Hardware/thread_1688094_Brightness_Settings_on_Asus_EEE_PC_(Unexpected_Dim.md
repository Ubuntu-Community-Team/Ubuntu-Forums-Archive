---
title: "Brightness Settings on Asus EEE PC (Unexpected Dimming on each Boot-up)"
date: 2011-02-15
forum: Hardware
---

### Post by bendispo on 2011-02-15
PC: Asus EEE PC 1018P (N550)
OS: Ubuntu 10.10

I recently purchased an Asus 1018P (the new dual core N550 version).  I believe it's running the same hardware as the dual core, non-ION 1015's.  I upgraded to the newest firmware, and I'm able to use the screen at it's brightest setting (earlier bios versions were dim).  

However, there seems to a new issue.  Whenever I shut down or restart, the brightness setting I'm currently at becomes the new maximum brightness on the next boot up. So, if I'm at 70% brightness when I shut down, the next session begins with that 70% as the new 100%.  

This only seems to occur when I'm actually in Ubuntu.  When I'm in the boot up screen or in GRUB console (I'm dual booting).  I can adjust the brightness using the keyboard hotkeys back up to maximum before it actually enters into Ubuntu.  So, it seems that the issue is that Ubuntu is taking whatever brightness the screen is set as during startup for it's maximum brightness once I'm in the OS.

If anyone has any advice, it would be greatly appreciated.

As a note, I'm using this fix for the hotkeys, as recommended in one of the 1015 threads:

GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux"

I also earlier tried using the following from the hardware wiki, but it seems to be problematic, with the brightness bubble not matching the actual brightness:

GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux acpi_backlight=vendor splash"

In any case, both the second and the first options exhibit the problem I've been describing.

Thank you all in advance! :)

---

### Post by bendispo on 2011-02-16
Bump.  No one with any advice? :)

---

### Post by a_rojilla on 2011-03-17
Same here. In my case with an older Asus 1005P.

After more than 7 years with Ubuntu, I think I'm done. It's 2011 and I'm still asked to edit xorg.conf or GRUB just to make my screen brighter. Amazing.

I had no problems with older versions of Ubuntu and that's the worst of all: I panic with every new upgrade because experience has shown me that something important that was working before will stop working. This time it has been the screen. I just wouldn't upgrade if I wasn't forced to upgrade the whole OS just to benefit from some new features. Enough.

I wish Ubuntu the best, but I'm moving away.

---

### Post by antismap on 2011-08-02
Hello, I have the same problem with an eeepc 1001px.
It's annoying because every two boots the screen gets too dark so i have to boot twice. Someone got a fix ? 
I agree with the last post. I have xubuntu 10.10 and I don't want to upgrade to the last version because I'm sure something else won't work anymore and thus the situation would get worse. 
I hope someone can help me !

---

