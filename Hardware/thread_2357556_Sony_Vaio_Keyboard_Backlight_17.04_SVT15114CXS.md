---
title: "Sony Vaio Keyboard Backlight 17.04 SVT15114CXS"
date: 2017-04-03
forum: Hardware
---

### Post by miyoung on 2017-04-03
I recently installed Ubuntu on my Sony SVT15114CXS and almost everything works out-of-the-box except for the keyboard back light.  I've already done a good amount of searching the forums both here and other places but haven't been able to find a solution that works.  I have looked at the following pages: [here]("http://askubuntu.com/questions/276983/cant-disable-control-keyboard-backlight-on-sony-vaio-vpcf236fm"), [here]("http://askubuntu.com/questions/475711/turn-off-keyboard-back-light-sony-vaio-svf1521dcxw"), and [here]("http://askubuntu.com/questions/345475/how-can-i-enable-keyboard-backlight-on-sony-vaio-pro-with-ubuntu-13-10").  The file [highlight]kbd_backlight[/highlight] and [highlight]kbd_backlight_timeout[/highlight] are located in [highlight]/sys/module/sony-laptop/parameters[/highlight] and not in [highlight]/sys/devices/platform/sony-laptop/[/highlight].  I have tried making a [highlight]conf[/highlight] file in [highlight]/etc/modprobe.d[/highlight] where I change the values of [highlight]kbd_backlight[/highlight] and [highlight]kbd_backlight_timeout[/highlight].  The values do change to match what I've set but they don't affect the keyboard.  Interestingly, when the boot loader loads the keyboard is illuminated but once the login screen for ubuntu loads the lights turn off.  Any insight would be greatly appreciated.

---

