---
title: "screen resolution"
date: 2008-11-28
forum: General Help
---

### Post by 2handband on 2008-11-28
I just installed Ubuntu 8.10 on my wife's desktop computer with a standard 15 inch monitor and for some reason the largest screen resolution available is 800 x 600. I have it on my laptop and I have the option of 1280 x 800. Does anyone know why this is and what I might be able to do about it?
Thanks!

---

### Post by pumkinut on 2008-11-28
You're probably going to have to edit the xorg.conf file by hand and insert the resolutions needed.  I recently had to do this with my Dell Latitude laptop.

---

### Post by Coreigh on 2008-11-28
It is likely a video display driver issue. Are you using a safe-mode or generic driver? What video chipset is in the computer, Intel ATI or nVidia?

Enable restricted and universe repositories in your sources (System >> Administration >> Software Sources, Ubuntu tab). And Check the Hardware Drivers applet (System >> Administration >> Hardware Drivers) for restricted drivers.

Less likely but possible is a limitation of the monitor. Is it a 15" CRT or flat panel? If it is a CRT (glass tube) it *could* be limited to a low resolution.

Edit:
In 8.04 and later the xorg conf is generated on the fly like the LiveCD, you shouldn't have to edit it. However if the problem turns out to be the small monitor then you may benefit from a customized xorg.conf.

---

### Post by ajgreeny on 2008-11-28
This is impossible to answer without more information;  what graphic card and what driver are you using?  It may be possible to adde the required resolution to your /etc/X11/xorg.conf file, but it would be good to know what resolution you want before suggesting what to add to the config file.

As an example, my machine detected and gave me a resolution too high for the monitor, so half the screen was missing at the bottom.  I could change it for my user account, but the guest account always came with the too large screen size, so was useless to any casual user who wanted to use the machine.  I added the following to my xorg.conf file so as to have a 1280 x 1024 resolution and now all is OK.  The lines in bold are those I added to the already existing other lines.

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
   [B] DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection[/B]
EndSection

---

### Post by 2handband on 2008-11-28
It's a 4 year old walmart emachine and therefore uses whatever crappy video chip is on the motherboard. It doesn't have a separate graphics card.

It's a standard glass-tube monitor, but I know we had a higher resolution when we were using windows so I doubt it's an inherent limitation with the monitor.

How do you go about modifying those files? I'm very new to linux.

---

### Post by Coreigh on 2008-11-28
this command may shed light on what video chipset your emachine uses
in a terminal window:
```
lspci
```
Or this may narrow it down:
```
lspci | grep VGA
```

Another possibility is to try to reconfigure xorg:
```
sudo dpkg-reconfigure xserver-xorg
```
But there is no guarantee that it will come up with any better a config for you

---

### Post by UpsideDownFace on 2008-11-28
I had the same problem when I upgraded from Ubuntu 7.10 to 8.04.
The problem is due to Canonical not liking commercial video cards, so they have stopped coping with some.

ajgreeny has given a very similar solution to the one I used

I have used "gksu /etc/X11/xorg.conf" to edit from the terminal.
or under Applications=>System Tools I have Root Terminal, but that is asking for trouble!

dpkg-reconfigure will set your video back to a display you might not want, so the you will have to edit xorg.conf again.

Practice makes Perfect
Wrong Practice makes Perfectly Wrong

---

