---
title: "Making a custom xorg.conf file"
date: 2012-07-19
forum: Hardware
---

### Post by enewe101 on 2012-07-19
I just got my dual screen set up in ubuntu using an nvidia GeForce 8400 GS video card.  The nice thing is that it worked as an extended desktop right away.  But the resolutions available are wrong.  They are not as high as the monitor can go (1440x900), and they are not the right aspect ratio either.

I haven't been able to add new display modes using xrandr commands -- it seems to refuse to allow the modelines with higher res to be added to the outputs, as if I am asking for a res beyond what my screens or video card are capable of (however, in windows the displays can go to the full res.)

But I'd rather achieve this by editing xorg.conf anyways.  I believe this is a good way to alter the display characteriscs persistently.  I've tried about a dozen permutations of xorg.conf files based on examples from the net, but they nearly all cause the screen to go black on booting up.

My system did not come with an xorg.conf file to begin with.  While I've tried many more complicated ones, I'm posting this simple one hoping that it will be more obvious what might be wrong with it.

```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
EndSection

Section "Monitor"
    Modeline    "1440x900@75" 136.75  1440 1536 1688 1936  900 903 909 942
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Modes "1440x900@75"
    EndSubSection
EndSection

```If I delete the lines beginning with "Modeline..." and "Modes..." the system can boot up and load the desktop environment fine (though without 1440x900 res available). Including these lines gives me a solid black screen.

Any clues?

---

