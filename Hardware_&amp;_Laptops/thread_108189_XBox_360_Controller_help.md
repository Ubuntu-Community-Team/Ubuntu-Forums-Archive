---
title: "XBox 360 Controller help"
date: 2005-12-25
forum: Hardware &amp; Laptops
---

### Post by dude2425 on 2005-12-25
I just got a new XBox 360 controller for X-Mas, and I plug it in, and all it does is blink a green light in the middle. It doesn't show up anywhere as being pluged in, it doesn't show up in the device manager, I don't even think it makes anything in /dev to get it to work.
Does anybody have any help on this? I'm anxious to get it to work, and I will NOT install windows just to play games with this thing.

---

### Post by tseliot on 2005-12-25
Try Automatix and select "USB Gamepads" but it works only on Breezy (not on Dapper yet).

Or follow this guide [HOWTO: Get USB Gamepads to Work in Hoary]("http://www.ubuntuforums.org/showthread.php?t=28538&highlight=usb+gamepad")

---

### Post by dude2425 on 2005-12-25
joystick does't seem to work for me. anyway to combat this problem:
$ sudo /etc/init.d/joystick restart
Oops, please create some joystick device nodes with MAKEDEV first!Starting the j oystick device check: 


I have no idea how to use MAKEDEV to create the joystick device nodes like it asks.

---

### Post by atf487 on 2005-12-27
I need help with this too.

I can see the gamepad in device manager, and i did "MAKEDEV js" to make js0, js1, js2, and js3 but i still can't get it to work.

[http://i2.photobucket.com/albums/y2/atf487/xbox180.png](http://i2.photobucket.com/albums/y2/atf487/xbox180.png)

---

### Post by dude2425 on 2005-12-29
When I run MAKEDEV like that, it tells me it's creating the device nodes, but when I check, there's nothing there. Anybody have a remedy for this? I had a similar problem with my modded XBox controller a while ago in Breezy, but I can't seem to remember how exactly I fixed it.

Also, why does it show up in Device Manager as having four "USB Vendor Specific Interface" under a "Controller" (Gamepad in your case)

---

### Post by luopio on 2006-03-06
Hi everyone!

I bought the gamepad and so far it has been useless. I do however know that it is possible to get it working by compiling a driver from xbox-linux.org. [Here's a howto]("http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux") relating to the matter.

I tried it on my Dapper setup, but didn't get it working. I'll just wait for the stable version of Dapper until I try again. I believe it'll work on breezy. Please let me know if it does.

---

