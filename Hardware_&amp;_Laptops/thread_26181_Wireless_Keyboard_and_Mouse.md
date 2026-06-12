---
title: "Wireless Keyboard and Mouse"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by karthik085 on 2005-04-12
I have Logitech Wireless Keyboard and Mouse. My laptop is a dual-boot one (Windows/Ubuntu). Windows, Bios recognizes the keyboard. I can even use the keyboard to select which OS I want to start. But, Ubuntu does not recognizes it.

These are the ways I tried to make it work:
1. Modified /etc/X11/xorg.conf file. Changed xkbrules and xkbmode lto xfree86 and 
logicdit(Logitech Cordless Desktop iTouch). In my xorg.lst, there was no model number that supported the same. Hence, I referred to xfree86.
2. I tried seeing if there was a option in my BIOS setting, that let BIOS handle the keyboard support instead of OS. My BIOS never had settings like that at boot-time. In Device Manager under BIOS, it says bios.usb_legacy_is_supported.

However, none of them worked. If you have suggestions, please let me know.

---

