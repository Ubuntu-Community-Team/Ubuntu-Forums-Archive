---
title: "Cr-48 (Chrome Netbook) Issues"
date: 2011-06-12
forum: Hardware
---

### Post by Mars11 on 2011-06-12
I've had my Cr-48 since the 9th of December and flashed a new BIOS to install Ubuntu. Now that I've had Ubuntu running on it for ~6 months I want to get some things fixed that I haven't been able to:
[LIST]
[*]Ambient Light Sensor
[*]3G (I've heard the Gobi 2000 also has GPS)
[*]LEDs on the Mute "F8" and Shift keys
[/LIST]
I would also like to see a Notification via notify-osd when I change the brightness.
Thanks in advance to who ever is willing to help. :D
Edit: I would also like to change the keys at the top to do what they're specified and not show up as F1, F2, F3 etc... So F1 would go forward, F2 would go back, F3 would refresh, F4 would put the application into full screen mode, F5 would switch workspaces. I have F6-F10 working, but I wish they didn't show up as the FX keys. If I could fix that I would need help also setting up brightness up/down, mute, and volume up/down.

---

### Post by kerry_s on 2011-06-12
I haven't seen any working fixes for those. 
When i did mine i wiped the whole drive, so i have no chrome os to try 3g fixes, it's said all you need to do is copy something from that partition.

---

### Post by Mars11 on 2011-06-12
I also wiped Chrome OS so I guess I couldn't do that either, but I've been told I need a firmware upgrade. It shows up when running an OS in Virtual Box, but it wouldn't let me use it. I'm guessing I just need a driver, but I can't find one.

---

### Post by kerry_s on 2011-06-12
for the keyboard keys.
install keytouch from the repos.

then unzip & import the file i've attached into keytouch.

---

### Post by Mars11 on 2011-06-12
Thanks, but F4, F5, F6, and F7 aren't working.

---

### Post by kerry_s on 2011-06-12
> **Mars11 said:**
> Thanks, but F4, F5, F6, and F7 aren't working.

there was a change in something & those stopped working, haven't found a fix for those yet.

---

### Post by Mars11 on 2011-06-12
F6 and F7 were working for about the first 10 minutes, but then stopped suddenly.

---

### Post by kerry_s on 2011-06-12
> **Mars11 said:**
> F6 and F7 were working for about the first 10 minutes, but then stopped suddenly.

i haven't looked into it, i rarely see my cr-48 since mom started using it. you know how that go's, when they say borrow, they never tell you how long, it's payback for all the times i've done it. :lolflag:

---

### Post by Mars11 on 2011-06-13
Nice...thanks for the help btw. I REALLY want the 3G to work though. I was hoping somebody could have found the fix by now. It would be nice if I could get the keyboard LEDs to work too, but I don't know if that's even possible. I know they work because when I take the battery out and put it back in the Mute Key's LED flashes orange and the Shift Key's LED flashes white.

---

### Post by Mars11 on 2011-06-15
Also, btw, it's not really the 3G I want working, it's the GPS. I've done some searching and it seems that the [Gobi 2000 worked before 10.04]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099"). I [found some directions on installing a driver]("http://blog.bagearon.com/?p=69") for it, but it must not work in 11.04. But putting that to the side. Does ANYONE know if I can get the Mute LED and Shift LED and Ambient Light Sensor working?

---

### Post by bupahs on 2011-06-19
> **Mars11 said:**
> I've had my Cr-48 since the 9th of December and flashed a new BIOS to install Ubuntu. Now that I've had Ubuntu running on it for ~6 months I want to get some things fixed that I haven't been able to:
[LIST]
[*]Ambient Light Sensor
[*]3G (I've heard the Gobi 2000 also has GPS)
[*]LEDs on the Mute "F8" and Shift keys
[/LIST]
I would also like to see a Notification via notify-osd when I change the brightness.
Thanks in advance to who ever is willing to help. :D
Edit: I would also like to change the keys at the top to do what they're specified and not show up as F1, F2, F3 etc... So F1 would go forward, F2 would go back, F3 would refresh, F4 would put the application into full screen mode, F5 would switch workspaces. I have F6-F10 working, but I wish they didn't show up as the FX keys. If I could fix that I would need help also setting up brightness up/down, mute, and volume up/down.

All of those items can be fixed.

1. the Ambient Light Sensor is part of the camera, so unless you want the camera activated all the time (like it actually is on the CR48 Chrome OS) its best to ignore it.
2. I have the Gobi fully operational with GPS, it requires a bit of work but can be done.
3. the LEDs I am still working on, they work some of the time, but not stable.
4. the F Keys is probably the simplest fix, simply use key mapping to get the job done. You will need to install xvkbd
xbacklight then use Key Mapping to set the F Keys. For example if you wanted the right facing key to be browser forward you would enter this:

Browser forward
/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]"

I could write up a simple tutorial if you need it to walk you through getting everything working.

Are you running Ubuntu 10.10 or 11.04?

---

### Post by Mars11 on 2011-06-25
I was running Ubuntu 11.04, but I've recently switched to Fedora 15.

---

### Post by Mars11 on 2011-06-26
I didn't really like Fedora, it's a little more buggy then Ubuntu. So now I'm using Ubuntu 11.04 64-bit. I would like the a simple tutorial, but by part of the camera do you mean it uses the camera because I know it doesn't. There's a sensor off to the right of it.

---

### Post by Mars11 on 2011-06-29
*Bump*
I would really like the GPS working before I go on my trip tomorrow. Please, if anyone knows how to get it working can you tell me how?

---

### Post by Mars11 on 2011-06-29
I got the 3G and GPS running thanks to bupahs, but it stops when suspending the laptop. Is there anyway to get the 3G and GPS running after suspending without rebooting?

---

