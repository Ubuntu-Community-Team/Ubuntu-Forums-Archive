---
title: "Problems setting correct monitor resolution"
date: 2010-06-30
forum: Hardware
---

### Post by Losgann Mor on 2010-06-30
Hello,

I think this is probably a hardware problem; if not, the mods may feel free to move it as appropriate.

I've got Lucid running on an old IBM ThinkCentre, with an IBM P76 monitor. The monitor can do up to 1600x1200 resolution, although I usually set it to 1280x1024 as I find that more comfortable. However, Ubuntu defaults to 1024x768. When I go into Monitor Settings, neither 1280x1024 nor 1600x1200 are given as options; the only options available are 1380x768, 1024x768, 800x600, 848x480, and 640x480. In order to get the right resolution, I have to open a terminal and use xrandr --newmode and xrandr --addmode to manually create an entry for 1280x1024 (or 1600x1200), and then go into Monitor Settings, where it is now available to select, but it only lasts for the current session; every time I log in I have to go through this process.

Would anyone have any ideas as to why this would be happening? Is it because the hardware is several years old? Is it something to do with the graphics card (Intel 915 G) in the computer?

I'd be grateful for any suggestions. Thanks!

---

