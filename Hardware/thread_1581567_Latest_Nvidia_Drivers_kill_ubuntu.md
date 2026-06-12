---
title: "Latest Nvidia Drivers kill ubuntu"
date: 2010-09-25
forum: Hardware
---

### Post by Yautja_Cetanu on 2010-09-25
I have a sony vaio F11 and dual monitors. I have found out that I need the latest nvidia drivers to fix a problem with the graphics card I'm having with dual monitors.

I add the PPA here:
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)

then run apt-get update.

I have literally no idea what I'm doing so I don't know how to actually install things once I've added the PPA. However, what I do is go to System --> Hardware Display Drivers and then I enable the nvidia drivers and then I restart. Here is what happens:

**1. With the default driver enabled**
My laptop screen works fine but I cannot detect my external screen.

**2. With Nvidia drivers installed **
My external screen now completely works fine when I restart! However it cannot detect my laptop screen. When I unplug my external screen my laptop screen display gets borked. There are loads of wierd colours on the top and the display is split in two. (Hard to describe this but basically the left side of the screen actually appears on the right? and the bottom is cut off)

**3. With Nvidia drivers installed AFTER enabling PPA**
The resolution of the loading ubuntu screen is tiny. (This is the screen right at the beginning of booting up where it says "ubuntu" and then has 5 dots that change colour.

The coloured dots all change colour and when they have all changed colour it looks like the system totally hangs. It stays on that screen in definitely.

FWhat is going on here? Why doesn't ubuntu automatically update to latest drivers?

---

### Post by Yautja_Cetanu on 2010-09-29
anything?

Is no one else having any issues updating to the nvidia drivers and can't tell me which direction to go?

---

