---
title: "Brightness Function Keys not Working - 12.04 Beta 2"
date: 2012-04-14
forum: Hardware
---

### Post by denakitan on 2012-04-14
Hi guys!

I installed Ubuntu 12.04 Beta 2 Precise Pangolin in my laptop, a Compaq Presario CQ43, and my brightness control function keys (F2 and F3) are not working. No indicator notification and also no changes in the brightness when I use then. Changing it through "Brightness and Lock" settings works.

A strange thing is the fact that I could use then after installation. Probably some update might have been caused the problem.

I have already tried to boot using "acpi_osi=Linux" and/or "acpi_backlight=vendor" as Grub 2 parameters, but this hasn't solved my problem.

Do you guys know of any solution to this problem?

Thank you,
Dennis

---

### Post by Luz77 on 2012-05-01
you could try this: (worked at my nvidia on my Thinkpad W520)

1) make a backup of /etc/X11/xorg.conf and run nvidia-xconfig:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
sudo nvidia-xconfig
```(nvidia-xconfig will make another backup, but when you run nvidia-xconfig twice, then the backup isn't the original file anymore)

2) add the line with the brightnesscontrol to the /etc/X11/xorg.conf
```

...some other lines...
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
**    Option         "RegistryDwords" "EnableBrightnessControl=1"**
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
...end of file...
```3) reboot
4) make bug report :)
(I don't got the time and also don't know where :( )

---

