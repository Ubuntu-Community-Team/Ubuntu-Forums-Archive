---
title: "Keyboard and Touchpad Problem"
date: 2012-08-02
forum: Hardware
---

### Post by hummingway on 2012-08-02
1. 12.04 LTS Precise Pangolin
2. Toshiba
3. Sattelite L775D


I've had some problems with the keyboard working as well as shutdown issues. They may be related. Last night shutdown acted like logout and there was no way to shutdown except to kill the power. This morning she booted but the keyboard and touchpad wouldn't work. After several boot attempts, including disconnecting power and removing battery, without success I found the suggestion, on the web, that Ctl-Alt-F2 followed by sudo apt-get -f install was the answer. Ctl-Alt-F2 didn't appear to do anything but the keyboard did work.

I have had both the shutdown and keyboard problem upon reboot before though this was the most persistent. I believe they're connected.

---

### Post by hummingway on 2012-08-02
I don't know if any of this helps:

67: PS/2 00.0: 10800 Keyboard
  [Created at input.161]
  Unique ID: 9ui9.+49ps10DtUF
  Hardware Class: keyboard
  Model: "AT Translated Set 2 keyboard"
  Vendor: 0x0001 
  Device: 0x0001 "AT Translated Set 2 keyboard"
  Compatible to: int 0x0211 0x0001
  Device File: /dev/input/event3
  Device Files: /dev/input/event3, /dev/input/by-path/platform-i8042-serio-0-event-kbd
  Device Number: char 13:67
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown

68: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.183]
  Unique ID: AH6Q.ZHI3OT7LsxA
  Hardware Class: mouse
  Model: "SynPS/2 Synaptics TouchPad"
  Vendor: 0x0002 
  Device: 0x0007 "SynPS/2 Synaptics TouchPad"
  Compatible to: int 0x0210 0x0002
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event6, /dev/input/by-path/platform-i8042-serio-2-event-mouse, /dev/input/by-path/platform-i8042-serio-2-mouse
  Device Number: char 13:63 (char 13:32)
  Driver Info #0:
    Buttons: 2
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by hummingway on 2012-08-03
If you're looking at this problem I'll direct you here: [http://ubuntuforums.org/showthread.php?p=12149016](http://ubuntuforums.org/showthread.php?p=12149016)

---

### Post by hummingway on 2012-08-19
I have solved my keyboard and touchpad problem which seems to have solved the shutdown and reboot problem as well. 

This page: [https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340](https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340)

contains the solution for grub. Applying it to grub2 you can add "i8042.nomux=1 i8042.resetd" to the kernel boot line in /boot/grub/grub.cfg

---

