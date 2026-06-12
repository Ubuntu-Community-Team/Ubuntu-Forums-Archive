---
title: "Asus zenbook 3 (ux390) + i915 driver firmware + usb-c dock"
date: 2016-11-07
forum: Hardware
---

### Post by donbowman on 2016-11-07
I have an Asus zenbook 3 (ux390). It has the kaby lake i7-7500U processor and graphics.

I have two, possibly related, issues I'm looking for advice on.

First, I have a dell wd15 dock. When plugged in, the external monitor is detected (brand, monitor). But it won't enable the display. When I enable the display remains dark. But, if i plug in a vga-usbc dongle, or an hdmi-usbc dongle, both work correctly. So its something about this dock. I tried the VGA, the DisplayPort, the HDMI on the dock, all the same.

Second, I see "[drm] GuC firmware load skipped" in dmesg as I boot. I'm not sure if this should/should not be loaded.

I have switched this to use 'modesetting' driver on KDE rather than xf86 intel ddx, and its otherwise working quite well.

Any pointers?

---

### Post by donbowman on 2016-11-08
It appears from [https://01.org/linuxgraphics/intel-linux-graphics-firmwares](https://01.org/linuxgraphics/intel-linux-graphics-firmwares) that the firmware is correct: the dmc 1.0.1 loads, the 'GuC' skips as its kabylake and not skylake.

Leaving me with the issue of 'why does the external monitor not turn on'

---

### Post by shurikx on 2016-11-08
Are you sure Zenbook 3 supports DisplayPort output? It does not support Thunderbolt 3 that "drive" DisplayPorts. 

It seems the USB-C is a big mess: 
[http://blog.fosketts.net/2016/10/29/total-nightmare-usb-c-thunderbolt-3/](http://blog.fosketts.net/2016/10/29/total-nightmare-usb-c-thunderbolt-3/)

---

### Post by donbowman on 2016-11-09
i have tried usb-c -> hdmi, usb-c -> vga, usb-c -> displayport, all work on individual dongles using 'alt-mode'.
w/ the dock, the monitor is detected, model is correct, resolution is correct. It just doesn't turn the screen on when I enable it w/ xrandr or kde display app.
this is not a thunderbolt dock (that is the dell tb15).

the zenbook 3 (ux390ua) is spec'd to do thunderbolt 3 tho.

---

### Post by svast on 2016-11-09
I suspect the wd15 to be the cause of your troubles, not the laptop.

The DELL docking stations do not work well: the TB15 is a nightmare, and most wd15 owners are not happy with it.
That is what prevented me away from purchasing such device  when I got my "dell XPS13 9350" (which came with USB-C thunderbolt 3 plug).

My question is: on which kind of Linux computer did you manage to make the wd15 work ?

---

### Post by Ossoleil on 2016-11-10
I have the Kensington SD4600P dock with the Zenbook ux390ua and the display port works more or less. The i915 definitely has some bugs even in the latest kernels so it doesn't come up reliably on boot or plug/unplug.

The HDMI port is reliable but that limits me to 4k@30fps which feels very sluggish.

Btw, my ux390ua only has usb3.1 and not thunderbolt3.

---

### Post by donbowman on 2016-11-11
Some others have managed to get the wd15 dock working.
e.g. [https://www.reddit.com/r/archlinux/comments/49pctt/xps_13_9350_connected_to_monitors_through_dell/ ]("https://www.reddit.com/r/archlinux/comments/49pctt/xps_13_9350_connected_to_monitors_through_dell/")
Looking @ [https://github.com/01org/thunderbolt-software-daemon/issues/2](https://github.com/01org/thunderbolt-software-daemon/issues/2) there are some specific things I can try I guess. I'm on 4.9RC so i hope(?) these patches are in, but i'll check.

---

### Post by donbowman on 2017-01-10
So an update. There was new firmware released for this dock in December by Dell. Once installed the video ports work properly.

The Ethernet (r8152) is still not reliable. The USB device will show up after the dock is powercycled, but not necessarily after the laptop is removed and reinserted. lsusb -t is missing that one device (the others are present)

[FONT=courier new]$ lsusb -t[/FONT]
[FONT=courier new]/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M[/FONT]
[FONT=courier new]    |__ Port 1: Dev 4, If 0, Class=Hub, Driver=hub/7p, 5000M[/FONT]
[COLOR=#ff0000][FONT=courier new]        |__ Port 2: Dev 5, If 0, Class=Vendor Specific Class, Driver=r8152, 5000M[/FONT][/COLOR]
[FONT=courier new]/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M[/FONT]
[FONT=courier new]    |__ Port 1: Dev 18, If 0, Class=Hub, Driver=hub/7p, 480M[/FONT]
[FONT=courier new]        |__ Port 7: Dev 22, If 0, Class=Audio, Driver=snd-usb-audio, 12M[/FONT]
[FONT=courier new]        |__ Port 7: Dev 22, If 1, Class=Audio, Driver=snd-usb-audio, 12M[/FONT]
[FONT=courier new]        |__ Port 5: Dev 20, If 3, Class=Audio, Driver=snd-usb-audio, 480M[/FONT]
[FONT=courier new]        |__ Port 5: Dev 20, If 1, Class=Audio, Driver=snd-usb-audio, 480M[/FONT]
[FONT=courier new]        |__ Port 5: Dev 20, If 2, Class=Audio, Driver=snd-usb-audio, 480M[/FONT]
[FONT=courier new]        |__ Port 5: Dev 20, If 0, Class=Audio, Driver=snd-usb-audio, 480M[/FONT]
[FONT=courier new]        |__ Port 6: Dev 21, If 0, Class=Hub, Driver=hub/2p, 480M[/FONT]
[FONT=courier new]    |__ Port 5: Dev 3, If 1, Class=Video, Driver=uvcvideo, 480M[/FONT]
[FONT=courier new]    |__ Port 5: Dev 3, If 0, Class=Video, Driver=uvcvideo, 480M[/FONT]
[FONT=courier new]    |__ Port 8: Dev 5, If 1, Class=Wireless, Driver=btusb, 12M[/FONT]
[FONT=courier new]    |__ Port 8: Dev 5, If 0, Class=Wireless, Driver=btusb, 12M[/FONT]
[FONT=courier new]    |__ Port 9: Dev 7, If 0, Class=Vendor Specific Class, Driver=, 12M[/FONT]

---

