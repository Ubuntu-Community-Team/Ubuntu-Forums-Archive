---
title: "Boot freezes w/out Monitor"
date: 2009-12-17
forum: Hardware
---

### Post by wlraider70 on 2009-12-17
I doesn't make sense to me, but my 9.10 will not boot if i dont have a monitor attached. It freezes.

I did not do it in 9.4.

I don't want to run this machine with a head, its designed for VNC connection,

---

### Post by michael-wd21 on 2009-12-17
Hi,

If you've not created a configuration file /etc/X11/xorg.conf then I suppose Xorg will fail to start when it tries to probe your monitor and finds you don't have one! Then it won't be able to autoconfigure a display resolution. The solution might be to create an xorg.conf file which has the right settings.

If you do have an xorg.conf then maybe setting the NoDDC option will help. This disables probing of the monitors. My xorg.conf file has (amongst other things!):

```

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "ColorKey"                  # <i>
        #Option     "CacheLines"                # <i>
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "DRI"                       # [<bool>]
        #Option     "NoDDC"                     # [<bool>]
        #Option     "ShowCache"                 # [<bool>]
        #Option     "XvMCSurfaces"              # <i>
        #Option     "PageFlip"                  # [<bool>]
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "Mobile 945GME Express Integrated Graphics Controller"
        BusID       "PCI:0:2:0"
EndSection

```Maybe removing the '#' comment from the NoDDC line will help.

Otherwise, it might be useful if you could attach your Xorg log file from a failed startup. I suppose that would be /var/log/Xorg.0.log.old as you'll have to boot with your monitor disconnected (generating /var/log/Xorg.0.log) then with it attached (which will rename that file to /var/log/Xorg.0.log.old and create a new Xorg.0.log).

Hope this helps.

Michael

---

### Post by wlraider70 on 2009-12-22
there was no xorg.conf file.
so i created it just like yours, with no comment on "NoDDC"

It still froze...

---

