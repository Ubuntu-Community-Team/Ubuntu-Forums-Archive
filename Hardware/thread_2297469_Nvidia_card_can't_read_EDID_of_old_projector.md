---
title: "Nvidia card can't read EDID of old projector"
date: 2015-10-04
forum: Hardware
---

### Post by paul233 on 2015-10-04
Problem solved with help from existing threads - posting solution for ref by others.  Note that this solution requires the same display device (projector in this case) to have the EDID recognised correctly on another Linux system. The solution is to grab the EDID from that system and configure it into xorg.conf.

I was having trouble with an Nvidia card (EVGA GeForce GTX 700 series) on a new system reading the EDID for an old iGo projector.

The projector is recognised correctly on my old ASUS motherboard (integrated graphics) and my raspberry pi, but the new EVGA card declared the EDID corrupt (failed chceksum) no matter what I did.

So after a few days of digging I connected the projector to my old system which read the  EDID correctly and used 
```
xrandr --verbose
``` to access the raw EDID bytes:

```

DVI-0 connected 1920x1080+0+0 (0x55) normal (normal left inverted right x axis y axis) 708mm x 398mm
    Identifier: 0x52
    Timestamp:  455757
    Subpixel:   horizontal rgb
    Gamma:      0.88:0.88:0.88
    Brightness: 1.0
    Clones:    
    CRTC:       1
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff0024ef951260020000
        2b140103802f1d78ee54b3ab5238ab25
        b8505321080081c08100010101010101
        0101010101012f0d50f030e025101070
        6800c48e21000018000000ff0047384b
        4b30343341303630380a000000fc0055
        502d323032300a2020202020000000fd
        00384c1e5308000a202020202020011e
        02031cf2490504830192131416072309
        07078301000065030c001000011d80d0
        721c1620102c2580c48e2100009e8c0a
        d090204031200c405500c48e21000018
        011d007251d01e206e285500c48e2100
        001e011d00bc52d01e20b8285540c48e
        2100001e011d8018711c1620582c2500
        c48e2100009e0000000000000000002a

```

 I  transferred this as text to the new system, copied the hex bytes (below EDID: above)  into a new text file called 'edid.txt' then used xxd to create a binary  file from them:
```

xxd -r -p edid.txt edid.bin

```
copied it to /etc/X11/
```

sudo cp edid.bin /etc/X11/

```
then got the nvidia utility to create a new xorg.conf referencing it
```

sudo nvidia-xconfig --custom-edid=/etc/X11/edid.bin

```
But before rebooting, I needed to edit this new line in xorg.conf to reference the specific display port -
```

Option         "CustomEDID" "**HDMI-0:**/etc/X11/edid.bin"

```
Then I rebooted and didn't expect it to work straight away but it did.

Thanks to [papibe]("http://ubuntuforums.org/member.php?u=774785") and others who've posted similar problems and solutions.

---

