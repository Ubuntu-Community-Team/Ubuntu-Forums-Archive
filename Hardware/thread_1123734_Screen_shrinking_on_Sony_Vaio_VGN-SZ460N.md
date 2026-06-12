---
title: "Screen shrinking on Sony Vaio VGN-SZ460N"
date: 2009-04-12
forum: Hardware
---

### Post by dhouse on 2009-04-12
Hi,

I recently installed Ubuntu 8.10 on my Sony Vaio Laptop (model VGN-SZ460N) and it was running fine for a while until one time I started the computer and when Ubuntu was loading it gave an error message concerning the computer graphics. I selected to run the computer in the low graphics mode and the display shrunk to about 3/4 of the size of the computer screen. 

I know this could be something to do with the laptop having a Nvidia graphics card. Could you please help me out with this problem?

---

### Post by ajgreeny on 2009-04-12
You probably had an update of the kernel and simply need to reinstall the nvidia driver for your card using *System > Administration > Hardware Drivers*,  at least that is where it is in Hardy.  Look for something similar in Intrepid.

---

### Post by dhouse on 2009-04-12
I went to the check the hardware drivers option but it simply says "No proprietary drivers are in use on this system" and there are no drivers that I can select to install. Any other suggestions?

---

### Post by ajgreeny on 2009-04-13
Start in recovery mode (second item in grub menu) and choose **xfix** when the small menu appears.  It should detect your card again as it did at install.  If that doesn't work you may need to manually edit your /etc/X11/xorg.conf file to include the resolution you want.

---

### Post by dhouse on 2009-04-13
> **ajgreeny said:**
> Start in recovery mode (second item in grub menu) and choose **xfix** when the small menu appears.  It should detect your card again as it did at install.  If that doesn't work you may need to manually edit your /etc/X11/xorg.conf file to include the resolution you want.

Thanks for the tip ajgreeny, that actually fixed the problem. However, I wanted to ask how to manually edit my /etc/X11/xorg.conf file so that this problem doesn't happen again?

Thank you for your time and help!

---

### Post by ajgreeny on 2009-04-14
In my case I had to edit my xorg.conf file to look like this:
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```Once you know your required resolution make your file look like this in format, ie change the figures but leave the text pattern the same, and hopefully it will work OK.  Backup your current file first with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.confbak
``` so you can restore it if anything goes wrong.

---

