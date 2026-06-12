---
title: "Missing keyboard functions"
date: 2019-07-20
forum: Hardware
---

### Post by crockett98 on 2019-07-20
I've got a 2009 32bit netbook that I've been struggling to find a small and lightweight distro for. I settled with the 18.04 Ubuntu mini.iso and used the option to install LXDE/Lubuntu. It works great and only uses 130Mb of RAM.

Except, my keyboard isn't working correctly.

Here is an image of my keyboard...
[https://www.laptopkeyboard.com/wp-content/uploads/2017/08/278_1271436978_SG1_keyboard_laptop_keys.gif](https://www.laptopkeyboard.com/wp-content/uploads/2017/08/278_1271436978_SG1_keyboard_laptop_keys.gif)

The problem is the Fn key. I first noticed my volume and brightness don't work. After a bit of playing around I discovered the Numlock doesnt work for the numbers but it will work for /+-*. Fn-L seems to be page down, Fn-U and Fn-O seem to be left and right arrow... and so it goes on! 
Sleep (Fn-Esc), Monitor switch (Fn-F4), Home/End and Touchpad toggle (Fn-F10) all work fine. 

Is there an easy way to at least get the volume, brightness and Wifi toggle working? 

Thanks for any help!

EDIT: I should add that all the standard keys work, as do the shift keys. Its just the Fn keys that are dicey!

---

### Post by TheFu on 2019-07-20
My research says that Fn keys are controlled by the BIOS, not the OS.

You can re-map the desired functionality to different keys, if you like.  LXDE uses openbox and the openbox XML configuration file supports this.  In ~/.config/openbox/ is the XML file.  The name used of it can be found looking at the process table:
```
tf        3787  3771  0 Jul04 ?        00:00:26 openbox --config-file /home/tf/.config/openbox/lxde-rc.xml
```
So, on my 16.04 desktop, lxde-rc.xml is the name of the file.
```

<keybind key="W-F5"><action name="Execute"><command>xbacklight -dec 10</command></action></keybind>
<keybind key="W-F6"><action name="Execute"><command>xbacklight -inc 10</command></action></keybind>
```

"W" is the "Super" key - mine is mapped above as the capslock key.  F5 and F6 are where the Fn+F5 for dimmer and Fn+F6 for brighter.  You get the idea. You'll need to look at the XML file to find the right place to put these commands and you'll need to look up the specific commands to be used for the actions you want.

Clear as mud?  The openbox how-to has more about this stuff. Google should find it.

---

