---
title: "External monitor problem after package update."
date: 2012-04-16
forum: Hardware
---

### Post by f1r3br4nd on 2012-04-16
Hello. I have a Dell Vostro 1220, i915 Intel video, running Ubuntu 10.04...

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid

$ uname -a
Linux dillo 2.6.32-40-generic #87-Ubuntu SMP Tue Mar 6 00:56:56 UTC 2012 x86_64 GNU/Linux

```

This shouldn't make a difference, but the Ubuntu variant I'm running is Kubuntu.

As of today, when I plug in my external VGA at work, it fails to be recognized:

```

$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       58.1*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DP1 disconnected (normal left inverted right x axis y axis)

```

It's been ages since I've messed with my video settings in any way, so this must have been a package update that happened between Friday the 13th and today. Does anybody have suggestions on how to troubleshoot this problem and, if I can't fix it, how to at least identify which packages to roll back? Thanks.

---

### Post by f1r3br4nd on 2012-04-16
It might have something to do with the lines showing up in my dmesg saying
```

[drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 130

```

And apparently there is a device option in xorg.conf that can override this with either...

```

Option "UseEDID" "False"

```

or

```

Option "IgnoreEDID" "True"

```

The problem is that there is no longer a global xorg.conf in Ubuntu, just device-specific files in /usr/lib/X11/xorg.conf.d/. I ran ```
X :1 -configure
``` and it created an xorg.conf.new file, but I only want to statically configure Xorg only to the minimum extent necessary to make the video driver ignore EDIDs. So, should I just copy the following section into a file in the xorg.conf.d directory?

```

Section "Device"
        Option "IgnoreEDID" "True"
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
        BusID       "PCI:0:2:0"
EndSection

```

Does it matter what number I give the file? Is the above sufficient information for Xorg to know that these are my intentions for the video driver? Do I need to have a line with [FONT="Courier New"]Option "Monitor-XXX" "MonitorName"[/FONT] for each monitor?

---

