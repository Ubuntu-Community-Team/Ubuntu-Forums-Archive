---
title: "Problem with refresh rates"
date: 2006-05-04
forum: Hardware &amp; Laptops
---

### Post by Final on 2006-05-04
Hello

I am currently using Ubuntu Breezy Badger 5.10 with hardware of 2x GeForce 6600 GT on nForce4 chipset serie motherboard (ASUS A8N-SLI). I have installed drivers for these both, using nvidia.com latest ones.
As a monitor I use Philips 170S6FB. This is a 17" TFT 12ms of which native resolution is 1280x1024 and maximum refresh rate 76Hz.
Linux drivers for this monitor doesn't exist.

I would like to use 1280x1024 resolution and 60Hz refresh rate for my screen, because it looks the best (a reference to Windows that I use same time on this computer). But now we face a problem. When I enter Gnome Control Center to switch the refresh rate that is given automatically to me as I had installed the nVidia drivers on my computer, there exists no such possibility to switch the refresh rate to lower frequencies - the only option is 75Hz.

Well, using 75Hz with this monitor starts eventually to hurt eyes (as sitting 12 hours already wouldn't?) and therefore I had to begin editing xorg.conf. I checked that was everything ok, yes, the 56 - 76 VertRefresh was indeed correct, I saw the exactly same on manufacturer's site. Furthermore, no problems with HorizSync either; albeit 30 - 82 that was informed on the xorg.conf differented by one from the manufacturer's one (30 - 83). However, most certainly, this can't be (and it wasn't) causing the problem.

Now I began wondering, what if I added a modeline there?
I used a modeline generator and google to find other people with same screen and setup.
Firstly I tried this line "1280x1024@75" 156.43 1280 1312 1904 1936 1024 1043 1056 1076 and then "1280x1024@60" 156.43 1280 1312 1904 1936 1024 1043 1056 1076. Nothing helped with the problem. It saw that the problem was certainly with the given values. Thus, I tried this line: "1280x1024@75" 109.62  1280 1336 1472 1720  1024 1024 1026 1062 and then "1280x1024@60" 109.62  1280 1336 1472 1720  1024 1024 1026 1062. Neither helped.

Most likely I am totally missing something here.
Anyway, help would be appreciated.

---

### Post by tseliot on 2006-05-06
```
sudo gedit /etc/X11/xorg.conf
```

Get to the section "Screen",  and look for the subsection SubSection "Display".

You will be able to see the resolution for default depth, usually 24. 

Add _60 to the end of your desired resolution ( _60 stands for 60hz) and make it look like the example below (see the part in red:

```
Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "[COLOR="Red"]1024x768_60[/COLOR]" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

Then save the file, log out and press CTRL+ALT+Backspace to restart the xserver.

---

### Post by Final on 2006-05-06
This setup worked! Thank you very much!

---

