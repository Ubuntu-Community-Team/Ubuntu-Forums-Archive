---
title: "Intel 855GM: brightness not changeable AFTER suspend/resume"
date: 2009-04-24
forum: Hardware
---

### Post by cywhale on 2009-04-24
Hello,

**after a fresh reboot/boot** of Jaunty changing brightness on my Acer Travelmate C110 using FN-left/right or brightness applet **works fine**.

However **after first suspend to ram/resume I am not able to adjust the lcd brightness**. Pulling AC does not result in screen dimming as intended, too.

I'm searching for a soultion to this issue for weeks now (same issue with Arch Linux, came back to Ubuntu with Jaunty beta after one year Arch Linux) - but nothing seems to work.

Last time brightness worked 100% for sure was with Ubuntu Gutsy (Intrepid not tested).

Driver: xf86-video-intel, Jaunty repo
Xorg: Jaunty repo, xorg.conf-device-section unchanged (default)
Kernel: Jaunty repo
Code:

```
echo <value>|sudo tee -a /sys/class/backlight/acpi_video0/brightness

```
Works fine after fresh boot, not after suspend/resume.

- unloading module 'video' did not work
- un/reloading module 'acerhk' did not work (didn't think so but tried)
- using 'video brightness_switch_enabled=1' in /etc/modules did not work
- using most recent Xorg/intel driver (with Arch Linux) did not help
- using Xorg 1.4 and old intel drivers did not work (Arch Linux)
- converted my partitions back to ext3 and tried kernel 2.6.22 - garbeled screen/freeze :(
- compiling kernel with various patches maybe related to this result in freeze after 4-6 hours (always during package building)

This is the last issue with Linux on this little TabletPC and I'm desperately looking for a solution to this so any help would be greately appreciated... maybe an idea about garbeled screen with old kernel in jaunty?

---

### Post by cywhale on 2009-04-26
Hm...
even ```
 sudo setpci -s 00:02.0 F4.B=80
``` works fine before suspend/resume, afterwards there's no reaction, screen brightness remains ~80% (estimated) whatever I do :(

---

