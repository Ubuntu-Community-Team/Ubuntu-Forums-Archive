---
title: "nvidia-settings screen resolution"
date: 2012-10-17
forum: Hardware
---

### Post by mikestormxs on 2012-10-17
Hey guys, I have an interesting problem here. In Ubuntu 11.10 I could set my monitor to the resolution of 1920x1200. I tried to do this in Ubuntu 12.04, but nvidia-settings is telling me that my maximum resolution is 1920x1080 - is there anyway I can force the custom resolution on there?

---

### Post by vaul on 2012-10-18
I have to agree to this. In 12.04 there was a way to easily set a custom resolution via the nvidia-settings utility, however in 12.10 Nvidia drivers have been updated and this option is gone.

Can anyone offer a solution?

---

### Post by nerd65536 on 2012-10-19
I was struggling with this during 12.10 beta. The newest Nvidia drivers change how resolutions are handled: The only available resolutions are the few your monitor explicitly defines (using EDID), often excluding many 'standard' resolutions.

To enable more resolution choices, custom resolutions, and custom Modelines:

If you don't have an /etc/X11/xorg.conf, we need to create one: Open nvidia-settings.
"X Server Display Configuration" -> "Save to X Configuration File", then click "Save"

Now edit /etc/X11/xorg.conf as root:
(Ubuntu)
```
sudo gedit /etc/X11/xorg.conf
```
(Kubuntu)
```
sudo kate /etc/X11/xorg.conf
```

We need to add the following line to the "Device" section:
```
    Option         "ModeValidation" "AllowNonEdidModes"
```

My "Device" section looks like:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    Option         "NoLogo" "on"
    Option         "ModeValidation" "AllowNonEdidModes"
EndSection
```

Save, and reboot (or restart X) to apply the changes.

---

### Post by vaul on 2012-10-20
Thank you, this have solved my problem. I think this thread should be made sticky to enhance visibility.

---

### Post by beerslayer on 2012-11-23
I apologize in advance if it looks like I'm side-tracking this thread too much.  This may or may not be a dumb question, but does this information apply to Intel-based drivers as well as nVidia?  I'm running Kubuntu 12.04 and until a few days ago I was able to get 1280x800 resolution without any difficulty.  Following a recent update a few days ago, I am now limited to 1024x768, which looks *horrible* on my screen.  I cannot find any way to restore the previous resolution.

If these options would be expected to work with Intel drivers instead of nVidia, I'd be willing to try.  But I'm no guru, and the file /etc/X11/xorg.conf does not exist on my system, so I'm afraid to try to create one from scratch.

---

### Post by clark22 on 2013-06-20
When I boot my laptop standalone, I get 45 lines of emacs, but when I  boot docked with a second 1920x1200 monitor in side-to-side twinview, I  get 74 lines of emacs.

I get a comparable increase in the number of Firefox tabs (stacked vertically), and everything else.

Attached are screenshots of the nvidia-settings windows. Notice that the  fonts end up being displayed smaller in the Twinview picture than in  the single screen, implying that the screen resolution is different in  these two modes.

---

### Post by Gfurst on 2013-09-13
Hey there, I'm having the same problem but not the solution. I've been looking around this for days now.
with the options
```
    Option         "ModeValidation" "AllowNonEdidModes"
```
A lot of non-native resolutions appear but none are good. Also switching to any other than native, gives a black or distorted screen.
My monitor is a iMac 21,5 inch, with 16:9 aspect and native res of 1920x1080, others used resolutions were 1600x900, 1280x720, none of which appear on the list.
With or without these options lines I'm unable to add my desired res with xrandr.

---

