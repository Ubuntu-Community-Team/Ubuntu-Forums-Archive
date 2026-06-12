---
title: "Logitech Quickcam Pro 4000 Not Working In Hoary"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by mac57 on 2005-04-12
I have just tried out the final release of 5.04. I have a Logitech Quickcam Pro 4000, which is supported by the pwc kernel module. I was pleased to see that the latest 10.0.6a pwc was included with 5.04. However, whenever I try to use Gnomemeeting, I get an error dialog saying that it can't open /dev/video0. A quick check of dmesg shows that this is what the pwc driver has registered my Quickcam Pro 4000 as.

Thinking it was just permissions, I tried it as root. Same problem.

Thinking it might be a kernel version issue, I downloaded the correct linux-headers package, went over to the pwc website and got the source, and rebuilt against the linux headers. I got further this time. No error opening /dev/video0, but the screen was just a mass of colored lines - no real video. When I tried to change the size from "small" to "large" Gnome froze, and I had to hit the power button.

Has anybody got their Logitech Quickcam Pro 4000 working under 5.04 Hoary?

---

### Post by ember on 2005-04-12
[QUOTE=mac57]I have just tried out the final release of 5.04. I have a Logitech Quickcam Pro 4000, which is supported by the pwc kernel module. I was pleased to see that the latest 10.0.6a pwc was included with 5.04. However, whenever I try to use Gnomemeeting, I get an error dialog saying that it can't open /dev/video0. A quick check of dmesg shows that this is what the pwc driver has registered my Quickcam Pro 4000 as.

Thinking it was just permissions, I tried it as root. Same problem.

Thinking it might be a kernel version issue, I downloaded the correct linux-headers package, went over to the pwc website and got the source, and rebuilt against the linux headers. I got further this time. No error opening /dev/video0, but the screen was just a mass of colored lines - no real video. When I tried to change the size from "small" to "large" Gnome froze, and I had to hit the power button.

Has anybody got their Logitech Quickcam Pro 4000 working under 5.04 Hoary?[/QUOTE]
 Try to install libpt-plugins-v4l and lippt-plugins-alsa ... that did help for me under warty

---

