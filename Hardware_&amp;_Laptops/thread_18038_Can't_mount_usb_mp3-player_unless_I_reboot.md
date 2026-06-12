---
title: "Can't mount usb mp3-player unless I reboot"
date: 2005-03-04
forum: Hardware &amp; Laptops
---

### Post by per on 2005-03-04
I can't mount my "asono eight" mp3-player on warty. It has a 256MB flash-drive and is using usb. No /dev/sda* devices shows up, though dmesg says:
[FONT=Comic Sans MS][INDENT]usb 1-2: new full speed USB device using address 3
scsi0 : SCSI emulation for USB Mass Storage devices[/INDENT][/FONT]
If it is atached when hotplug starts, it works fine. It shows up as /dev/sda1, and even automounts sometimes. Restarting hotplug doesn't help either, because I can't restart it; nothing happens.

Does anyone have a suggestion to how this could be solved? It's pretty anoying having to reboot each time I want to change the content of my mp3-player.

---

### Post by jerome bettis on 2005-03-04
it's probably called /dev/sdb* (maybe even sdc) because the order you plug your devices in makes a difference.  it can be annoying.

---

### Post by per on 2005-03-07
Thanks for your suggestion, but no, it doesn't create any sd* devices. Sometimes my mp3-player doesn't respond by saying that it's "pc-linked", either, which it should.

---

