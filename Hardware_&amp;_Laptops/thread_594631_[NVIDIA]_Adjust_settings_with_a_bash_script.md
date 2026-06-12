---
title: "[NVIDIA] Adjust settings with a bash script"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by LucaTNT on 2007-10-28
Hi,
i'm using an Acer Aspire 5633 WLMi laptop with an nVIDIA GeForce Go 7300 graphics card and Kubuntu Gusy Gibbon.
With nvidia-settings I can adjust my settings to activate my Samsung LE52M86BD Full HD TV, connected with a VGA cable at 1920x1080 resolution in Twin View mode.
After I finished using it, I restore the original settings, because of course the laptop's screen shows just a part of the image (1280x800).

I'd like to know how I could do this in a shell script.
I need this because I set up an account that activates Bluetooth remote controlling and launches Elisa Media Center on log-in, and I always have to adjust manually the settings to have the image visualized on the TV.

Another question: how can I make the TV continue visualizing the image when I close the lid?

Thanks in advance,
Luca Zorzi

---

### Post by morticul on 2008-02-29
Hi Luca. 

Did you found any solution about scripting nvidia-settings. I'm having the same problem...

[http://ubuntuforums.org/showthread.php?t=710918](http://ubuntuforums.org/showthread.php?t=710918)

---

### Post by LucaTNT on 2008-03-01
No, unnfortunately.
But I discovered that the TV is automatically set at the maximum resolution when it's connected *before* when the laptop is turned off, so it quite resolved my problems.

---

