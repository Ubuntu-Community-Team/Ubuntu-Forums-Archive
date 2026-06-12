---
title: "Ryzen 3500u no display after login screen."
date: 2020-10-14
forum: Hardware
---

### Post by celderian on 2020-10-14
Hey there. I am having some major issue with a HP Spectre x360 Ryzen laptop. There is no display after login in. I have Kubuntu 20.04 installed and all the UI element are blank. The wallpaper is black and things like the taskbar are grey with no text. If I hit the super key, the launcher but that is also blank. I’ve dropped down to shell and ran dmesg and there’s multiple messages about gpu driver recovery.  The issue disappears if I use the nomodeset set at boot but I really need gpu acceleration.  Any pointers to a solution? Thank you.

---

### Post by mastablasta on 2020-10-15
you need a different boot option [COLOR=#000000][FONT=&quot]iommu=soft[/FONT][/COLOR]
see here how i did it:
[https://ubuntuforums.org/showthread.php?t=2446942](https://ubuntuforums.org/showthread.php?t=2446942)

it works quite well so far and we had no issues with performance for our usage.

hopefully one of the new kernels will solve it but no one tested the patch so my bug report was closed.

---

### Post by celderian on 2020-10-16
Thank you kind stranger! That definitely helped.

---

