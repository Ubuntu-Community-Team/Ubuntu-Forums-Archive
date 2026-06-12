---
title: "Resolution problems while using a DVI to VGA converter"
date: 2018-12-21
forum: Hardware
---

### Post by cosmin.r11 on 2018-12-21
It's an old pc with a geforce 9000 series gpu with a DVI output, the monitor input is VGA, it's also dual booted w/ w7
The video resolution does't fit the 1680x1050 display so after the usual cvt 1680 1050 and xrandr addmode and newmode commands i get the BadMatch error
After a bit of googling the error happens because of the converter and it's conformed by nVidia's driver which can't aquire the edid information
Is there a way to actually get the PC to run in the correct resolution ?
I thought about getting the edid config using windows and pasting it in ubuntu but the programs i found can't seem to work 
//Ubuntu mate 18.04 lts with the latest nVidia driver for linux

---

### Post by Autodave on 2018-12-21
You may want to try a different VGA cable.  Cheaper ones don't have the extra wire in them to report the resolution to the PC.

---

### Post by CatKiller on 2018-12-21
If the xrandr route isn't working for you, you could try putting the HorizSync and VertRefresh ranges in a file in xorg.conf.d. That was the method before xrandr and should still work.

---

### Post by cosmin.r11 on 2018-12-21
I found the values in the display manual and found some example xorg.conf online and put it in a .conf in usr/share/X11/xorg.conf.d


Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L222WS"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection



not sure what to do form now tho

---

### Post by CatKiller on 2018-12-21
> **cosmin.r11 said:**
> not sure what to do form now tho

If it works, restarting X by rebooting (or logging out, probably) should allow X to use those ranges to generate new valid modes that you can pick from.

After you've done that, /var/log/Xorg.0.log should record how it's fared in doing that.

---

### Post by cosmin.r11 on 2018-12-21
Well, there are no new options, here's[ the log]("https://pastebin.com/DUasEDdP") .

---

### Post by CatKiller on 2018-12-21
Using **code** tags is easier than an external link.

You adjust seem to be trying to load the nouveau, vesa, modesetting, and fbdev modules, which *should* have been blacklisted by the Nvidia driver installation.

There is no indication in the log that X has picked up the HorizSync and VertRefresh values you added. You may need to check the formatting and the names you've given to the devices.

The log shows that it's very confused by the EDID it's getting. It says that it isn't getting an EDID from CRT-1, which is the one that it thinks is connected, so it sets the resolution to 1024×768 as the default. Then it says that it's picking a different resolution from *somewhere*.
```
[ 57.537] (II) NVIDIA(0): Setting mode "DVI-I-1: 1600x900 @1600x900 +0+0 {ViewPortIn=1600x900, ViewPortOut=1600x900+0+0}"
```
You've not said which resolution it's actually using.

If an xorg.conf exists, you'll have to edit that rather than just putting snippets in xorg.conf.d.

---

### Post by cosmin.r11 on 2018-12-21
Apparently the xorg.conf Monitor data was different from the xorg.conf.d file 
Just copied the values and it's working 
:)

---

### Post by CatKiller on 2018-12-21
> **cosmin.r11 said:**
> Apparently the xorg.conf Monitor data was different from the xorg.conf.d file 
Just copied the values and it's working 
:)

Yay! Glad you got it fixed!

---

### Post by zzhang2019 on 2019-01-30
@[B]cosmin.r11 (or anyone looking at this thread):

I am new to Ubuntu, so could you give the exact details of "[/B][COLOR=#000000]*Apparently the xorg.conf Monitor data was different from the xorg.conf.d file *[/COLOR]
[COLOR=#000000][I]Just copied the values"?
What steps do I need to do?

Thanks![/I][/COLOR]

---

### Post by wildmanne39 on 2019-01-30
Hello and welcome to the forum zzhang2019, please start your own thread instead of posting in someone else's especially a solved thread, the volunteers are not likely to look at a solved thread for someone having issues.

You can link to this thread if you think it will help solve your issue.
Thanks

---

