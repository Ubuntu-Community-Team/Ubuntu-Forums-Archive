---
title: "Surface Pro 3 Typecover trackpad not working"
date: 2016-03-24
forum: Hardware
---

### Post by keeran_mann on 2016-03-24
Hello,

I'm completely new to Linux but have installed Ubuntu 15.10 on my Surface Pro 3 on a separate partition. Everything is working apart from the trackpad on the type cover, I was wondering if anyone knew how to fix this? I've got the latest Linux kernel 4.5 installed. 

If anyone has any advice, that will be greatly appreciated!

---

### Post by RonStordahl on 2016-05-12
I also tried to do a live install using Ubuntu-16.04-desktop-amd64 and the typecover trackpad does not work.  There is no mouse pointer displayed.

As an additional test I tried a Ubuntu-16.04-server-amd64 install.  The typecover keyboard is apparently not seen.

---

### Post by medvardsen on 2016-05-13
To make mouse pointer visible I hope this can help:

You can try to install dconf-tools
open a terminal:
sudo apt-get install dconf-tools

enter
password

check if you then have a tool installed (thru the desktop) called: dconf editor

open it
go to section
org > gnome > settings-daemon > peripherals > mouse
enable locate-pointer in the checkbox

No solution for the trackpad

---

### Post by medvardsen on 2016-05-13
If you in logon window hit the settings button and choose "Gnome on Wayland" it seems to solve the trackpad issue :D

---

### Post by RonStordahl on 2016-05-16
medvardsen...how could I do what you suggest?  The keyboard is dead..there is no way to proceed.

As a matter of interest I booted Linux Mint 17.3 cinnamon no codecs 64 bit and it works just fine.  The keyboard and touchpad are active.

Perhaps the next release or update of Ubuntu will fix this.

Ron

---

### Post by razaquato on 2016-08-05
Hi.
To enable trackpad, first figure out what product you have. (the Type cover comes with 3 different ID's)

to do this, open a terminal and type **dmesg** after connecting the type cover.
Then look for the following output:

[I][COLOR=#222222][FONT=Verdana]usb 1-3: Product: Surface Type Cover
usb 1-3: Manufacturer: Microsoft
usb-1.3: New USB device found idVendor=045e, [B][U]idProduct=07dc

[/U][/B][/FONT][/COLOR][/I]Once you have your productId, open /usr/share/X11/xorg.conf.d/50-synaptics.conf in your favourite editor and insert the following code:

```

[COLOR=#000000]Section "InputClass" [/COLOR]
[COLOR=#000000]Identifier "Surface Pro 3 cover"[/COLOR]
[COLOR=#000000]MatchIsPointer "on"[/COLOR]
[COLOR=#000000]MatchDevicePath "/dev/input/event*"[/COLOR]
[COLOR=#000000]Driver "evdev"[/COLOR]
[COLOR=#000000]Option "vendor" "045e"[/COLOR]
[COLOR=#000000]Option "product" "**07dc**"  _<--replace with your ID_[/COLOR]
[COLOR=#000000]Option "IgnoreAbsoluteAxes" "True"[/COLOR]
[COLOR=#000000]EndSection[/COLOR]

```

reboot and you're good to go :-)

---

### Post by josie2 on 2017-01-04
> **keeran_mann said:**
> Hello,

I'm completely new to Linux but have installed Ubuntu 15.10 on my Surface Pro 3 on a separate partition. Everything is working apart from the trackpad on the type cover, I was wondering if anyone knew how to fix this? I've got the latest Linux kernel 4.5 installed. 

If anyone has any advice, that will be greatly appreciated!


[COLOR=#333333][FONT=monospace]I fixed the touchpad by adding the following lines to /usr/share/X11/xorg.conf.d/10-evdev.conf:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Section "InputClass"
    Identifier "Surface Pro 3 cover"
    MatchIsPointer "on"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
    Option "vendor" "045e"
    Option "product" "07dc"
    Option "IgnoreAbsoluteAxes" "True"
EndSection[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]This fix was discussed at [https://github.com/nuclearsandwich/surface3-archlinux/issues/4](https://github.com/nuclearsandwich/surface3-archlinux/issues/4) and [http://askubuntu.com/questions/620726/ubuntu-on-surface-pro-3-or-linux-at-all](http://askubuntu.com/questions/620726/ubuntu-on-surface-pro-3-or-linux-at-all).[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]In my case, the type cover stopped working after upgrading to 15.10 because the upgrade overwrote /usr/share/X11/xorg.conf.d/10-evdev.conf.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I'm not sure whether this matters, but there are two type cover USB IDs, 0x07de and 0x07e2, as discussed at [https://www.reddit.com/r/SurfaceLinux/comments/3dzriz/info_surface_pro_3_patch_status/](https://www.reddit.com/r/SurfaceLinux/comments/3dzriz/info_surface_pro_3_patch_status/). Maybe this fix only works for one of the two IDs.[/FONT][/COLOR]

---

