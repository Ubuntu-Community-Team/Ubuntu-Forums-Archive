---
title: "Installing Ubuntu in a HP dv5-1235dx"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by Diabolis on 2009-03-01
HP dv5-1235dx

**Problem:** no GUI (videocard not working)

I'm booting in safe graphics mode :-S

Using:
```

uname -nrmo
ubuntu 2.6.27-7-generic i686 GNU/Linux

```

Video card:
```
sudo lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

Screen: Generic PnP Monitor
Graphics: Mobile Intel(R) 4 Series Express Chipset Family
Adapter string / Media accelerator: GMA 4500MHD

From the Live-CD I get this:
```

cat /var/log/Xorg.0.log | grep EE
(EE) VESA(0): No valid modes
(EE) Screen(s) found, but none have a usable configuration.
[I]
and then this shows up
[/I]
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.

```

This didn't work:
```
sudo dpkg-reconfigure xserver-xorg
```

I read on intrepid's release page that the xorg.conf file is not used anymore, at least is supposed to be able to work without it.

---

### Post by Diabolis on 2009-03-01
```
uname -nrmo
ubuntu 2.6.27-7-generic x86_64 GNU/Linux
```

The **Xorg.0.log** contains the same errors as before.

---

### Post by Diabolis on 2009-03-01
Found the cause of the errors: [http://www.x.org/wiki/FAQErrorMessages#head-83b2f9b8c18db15e641ed9e0be8f9a8364001e5b](http://www.x.org/wiki/FAQErrorMessages#head-83b2f9b8c18db15e641ed9e0be8f9a8364001e5b)

In most cases this means there are no video modes available for your configuration.

```
sudo cat /var/log/Xorg.0.log | grep Not

(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)

```

Edited the xorg.conf file to look like this:
```

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
	DefaultDepth	8

	SubSection "Display"
        Depth       16
        Modes       "1280x800" "1024x768"
    EndSubSection

    SubSection "Display"
        Depth       32
        Modes       "1280x800" "1024x768"
    EndSubSection
EndSection

```

Still get the same errors.

---

### Post by Diabolis on 2009-03-01
*double post*

---

### Post by Diabolis on 2009-03-01
just had to change the xorg.conf file from vesa to intel :-S

---

