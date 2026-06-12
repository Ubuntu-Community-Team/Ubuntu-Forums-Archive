---
title: "My resolution is too low in my Toshiba laptop"
date: 2009-05-27
forum: Hardware
---

### Post by s1l1c0n on 2009-05-27
Hello,
I am new in the ubuntu space. I recently installed it in my very old laptop, a **Toshiba Satellite A20 **([http://www.toshiba.ca/web/product.grp?section=1&group=223&product=1912](http://www.toshiba.ca/web/product.grp?section=1&group=223&product=1912)). However, my display resolution is terrible.

When I open System->Preferences->Display, the following dialog box pops up saying:
[I][COLOR=Red]
"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"[/COLOR][/I]

If i say that I** DO NOT **want to use the graphics driver vendor's tool, the Display box opens, I only have access to four resolutions, with the highest being 800x600 pixels. My laptop monitor is designed to take 1024x800. Hence, my display is terrible at this moment.


If i say that I **DO** want to use the graphics driver vendor'stool, I get a warning message that reads:
[COLOR=Red]
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.[/COLOR]

I am at a loss of what to do here. 

In case it might be useful, here is what my xorg.conf file looks like:

[COLOR=Red]Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection[/COLOR]

How do I fix this issue?

Thanks!

---

### Post by pro003 on 2009-05-27
seem like you don't have installed driver for nVidia.

download from terminal envyng and then run it, it will detect automatically the best recommended driver for your video card

in terminal:
```

sudo apt-get update
sudo apt-get install envyng-qt envyng-gtk envyng-core
sudo apt-get install -f
sudo envyng
```
 
the rest of it it;s easy, just follow steps..

---

### Post by caco on 2009-05-27
hello, please what version of ubuntu are you using 9.04, 8.10 or 7.10?

We are waiting to help you out if possible.

---

