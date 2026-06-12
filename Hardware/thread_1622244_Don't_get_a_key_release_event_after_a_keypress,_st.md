---
title: "Don't get a key release event after a keypress, stuck key"
date: 2010-11-15
forum: Hardware
---

### Post by Viciou§ on 2010-11-15
Hi!

I am running 10.04 on a Dell Optiplex 745
Intel E6300 CPU
1GB RAM

I have a USB HID "keyboard" that have a few (5) media buttons.
All the buttons work but the problem is that when pressing a media button there isn't a key release event accompanied by it.
So after pressing the key it keeps being pressed (forever!).
One of the media buttons is XF86Stop and is used frequently :(

I have found a post that suggests running:
echo keycode > /sys/devices/platform/i8042/serio0/force_release
But force_release doesn't exist.
Do certain keyboard drivers create this or is it something else?
I believe that the driver used for the keyboard is hidraw.

I have searched and searched but can't find a solution for this so any help is appreciated.

---

### Post by Viciou§ on 2010-11-18
Doesn't anyone know an answer to this?

---

