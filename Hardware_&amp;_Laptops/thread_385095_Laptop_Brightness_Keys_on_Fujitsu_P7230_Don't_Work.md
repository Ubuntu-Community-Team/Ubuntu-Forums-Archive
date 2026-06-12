---
title: "Laptop Brightness Keys on Fujitsu P7230 Don't Work"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by Apreche on 2007-03-15
I recently became the proud owner of a brand new Fujitsu P7230 notebook. It's pretty awesome. What's more awesome is that just about everything "just works" in Edgy. That includes even the rough stuff like frequency scaling, wireless, suspend and hibernate. However, there are two things that do not "just work". One of those things is the screen resolution, which I fixed using 915resolution. 

The other thing, the one I can't fix on my own, is that the LCD brightness can not be changed using Fn+F6 and Fn+F7. When the system is booting or when the system is running windows these buttons will make the brightness of the LCD go up and down. As soon as grub loads the kernel, this no is no longer true. 

Here is the information I have.

The file  /proc/acpi/video/GFX0/LCD/brightness contains the following.
```
levels: 100 43 1 15 29 43 57 71 85 100
current: 0
```Commands like the following one do successfully change the brightness of the screen. However, I am unsure if every possible brightness level is achievable with this method.```
echo "85" > brightness
```If I press the Fn+F7 keys (brightness up), I see the following lines appear in /var/log/acpid. Nothing appears in this log if I press Fn+F6 (brightness down).```
received event "video LCD 00000086 00000000"
notifying client 4161[106:110]
completed event "video LCD 00000086 0000000"
```

I'd really like to fix this issue myself, and maybe submit the fix so others can have an easier time if they buy this great laptop. However, I have no idea where to start. Here is the info from /var/lib/acpi-support.```
bios-version:Version 1.04
system-manufacturer:FUJITSU
system-product-name:LifeBook P7230
```

---

### Post by Apreche on 2007-03-16
I did some more research. Apparently if I watch dmesg I can see some messages when I push either one of these buttons. ```
[17182217.360000] video device notify
```

Something is definitely going on here. The kernel is clearly seeing these acpi events, but its not using them to any effect. If it simply let them through to the BIOS/hardware they would change the brightness, so why bother paying attention at all? I tried to blacklist the acpi video module in hopes that this would be the result, but it didn't work.

---

### Post by tablanon on 2007-05-04
I have the same notebook and the brightness adjusts correctly using fn+f6/f7. I am using feisty without any special changes... weird. Maybe reinstall?

btw, sorry to change the subject- but have you been able to get your webcam to work?

---

### Post by Apreche on 2007-10-25
I don't have the webcam.

---

### Post by stuart brogan on 2008-04-12
I also have the Fujitsu Lifebook P7230 (this has a camera) and under Hardy Heron, almost everything works fine, I am actually using the xubuntu 8.04. I am still trying to get sound to work, but the Fn+F6 andF7 work ok here.

One thing I noticed was when I reinstalled windows (attempt to provision sprint pc-5740 evdo) then installed 8.04 and pushed windblows onto 5GB that the lights started working on the evdo card. I realize this is an unrelated issue, but maybe having that windows partition allows some of the proprietary drivers to be read. (just a wild guess).

I still have issues with sound and getting an IP from a wrt54gx model AP. 

Assuming you're using Gnome, have you tried their power management interface from the screensaver settings?

Good luck.

---

