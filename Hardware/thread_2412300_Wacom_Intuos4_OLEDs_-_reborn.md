---
title: "Wacom Intuos4 OLEDs - reborn"
date: 2019-02-11
forum: Hardware
---

### Post by sanette-linux on 2019-02-11
Hi,

in case people are still interested in this old subject (the thread has been closed: [https://ubuntuforums.org/showthread.php?t=1380744](https://ubuntuforums.org/showthread.php?t=1380744))
I have just completely rewritten the OLED script, for newer linux kernels.
So, yes you can put arbitrary images to your Intuos4 OLED screens!

[https://github.com/sanette/intuos4-oled](https://github.com/sanette/intuos4-oled)

* send images to individual buttons, or groups of button
* send multi-line text, with any font on your system
* automatic image processing and resizing: you can use any image size and format!
* 16 values of grays
* automatically save images on disk, for easy restoring after the tablet is disconnected/reconnected
* can handle several profiles by specifying specific datafiles
* udev rules file, so that you don't need root privileges

I'm also thinking of an api for animations, and why not, write a Tetris on the tablet ;) hehe

On a Ubuntu based distro, it should work out of the box. Just needs standard python and imagemagick.
I'd be happy to have testers on other distros.

---

