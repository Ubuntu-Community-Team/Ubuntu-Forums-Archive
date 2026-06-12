---
title: "Looking for video driver, Sager 5600P laptop, ATi 7500 graphics"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by oldsmobile_mike on 2008-01-25
Hi, I have some issues that I suspect are video driver related (specifically, I can't get VLC or other media players to play in full-screen mode, and even when I do open them up in "full-screen mode" (by which, they actually use a box that's about 3/4 of actual screen size) playback is often jerky and with low frame rates.

Anyhow, I'd like to try updating the video driver for my laptop, but I can't find one specifically for my model.  Laptop is a Sager 5600P with ATi 7500 graphics card, 64Mb of video ram, 2.0Ghz P4, 512Mb system ram.  The Sager site only has Windows drivers, and the ATi site only has Linux drivers going back as far as the 8500.  I tried Envy, but it wasn't able to find an appropriate driver, and said "install one of these others at your own risk".

Any suggestions?

Thanks!

---

### Post by Mikecore on 2008-01-25
> **oldsmobile_mike said:**
> Hi, I have some issues that I suspect are video driver related (specifically, I can't get VLC or other media players to play in full-screen mode, and even when I do open them up in "full-screen mode" (by which, they actually use a box that's about 3/4 of actual screen size) playback is often jerky and with low frame rates.

Anyhow, I'd like to try updating the video driver for my laptop, but I can't find one specifically for my model.  Laptop is a Sager 5600P with ATi 7500 graphics card, 64Mb of video ram, 2.0Ghz P4, 512Mb system ram.  The Sager site only has Windows drivers, and the ATi site only has Linux drivers going back as far as the 8500.  I tried Envy, but it wasn't able to find an appropriate driver, and said "install one of these others at your own risk".

Any suggestions?

Thanks!

Xorg comes with a open source driver called "radeon" which should support your card just fine. all you need to do is edit your /etc/X11/xorg.conf file this is the configuration file for your X server ( your GUI ). make sure you don't screw it up cause if you do you will break your system. and all you will have is a command prompt. the file looks similar to this. ( mine happen to be using the nVidia driver " but your will be probably using the 
ATI driver. )

```


Section "Device"
        Identifier      "nVidia Corporation C51 [Geforce 6150 Go]"
        Driver          "nvidia"
        Busid           "PCI:0:5:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"


```

anyhow find this section in your /etc/X11/xorg.conf file and edit it. where it says 

( Driver  "nvidia" ) you put  ( Driver "radeon" )

save the file then restart xorg/ or restart your computer. 

one suggestion I would back up this file incase you do screw it up then just reload it to get back to where you are now. ( note to edit this fiel you will need to be "root"
you can do all this at the command line.

---

