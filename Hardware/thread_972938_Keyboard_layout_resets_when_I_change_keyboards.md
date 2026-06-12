---
title: "Keyboard layout resets when I change keyboards"
date: 2008-11-06
forum: Hardware
---

### Post by Gorgapor on 2008-11-06
I'm using Intrepid on a lenovo thinkpad. I use a dvorak layout, and a separate usb keyboard when at home. However, sometimes my layout resets to qwerty on the usb keyboard, but not on the laptop keyboard. This seems to happen every time I reboot or unplug/replug the secondary keyboard.

If I go into System > Preferences > Keyboard, and add or subtract ANY layout (not just the dvorak one), or change ANY of the "Other Options...", the usb keyboard then has the correct layout.

Why is this happening? Is there a way to avoid having to manually reload my layout every time? Is there a workaround where I can run a script to reload my keyboard settings?

---

### Post by prshah on 2008-11-06
> **Gorgapor said:**
> Is there a way to avoid having to manually reload my layout every time? 

See any of these links: 

[[SOLVED] keyboard layout disappears on boot]("http://ubuntuforums.org/showthread.php?t=850040&highlight=setxkbmap")
[[SOLVED] Keyboard Layout Settings won't stick after reboot]("http://ubuntuforums.org/showthread.php?t=813567&highlight=setxkbmap")
[[SOLVED] Keyboar layout keeps resetting to US]("http://ubuntuforums.org/showthread.php?t=898384&highlight=setxkbmap")
[Keyboard preferences lost on automatic login]("http://ubuntuforums.org/showthread.php?p=5860154&highlight=setxkbmap#post5860154")

Summary: Add "setxkbmap" to your startup sessions.

---

