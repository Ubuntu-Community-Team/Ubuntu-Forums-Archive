---
title: "EDID of Samsung 941BW (or 940BW)"
date: 2011-11-26
forum: Hardware
---

### Post by insomniaccanuck on 2011-11-26
Could someone read their EDID of a working Samsung 941BW (or 940BW - Think it might work too).

Mine has been an issue for years and am tired of looking at a blurry monitor.  (Tried many a work around but none have worked with my NVIDIA card)

read-EDID pkg can be used to get it with get-edid.
The hex version of the file would be great.  (can be read with the ghex2 pkg)

Tried all the other options through the years but the EDID isn't right and the driver won't let me force the resolution.
Thanks

---

### Post by insomniaccanuck on 2011-11-29
Did a bunch of leg work but got it to work.

Here's a how to with the EDID that worked in hex at the end:

First when into the terminal and ran cvt (with desired hor res, vert res, refresh freq)

cvt 1440 900 60

it returned this modeline:

# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync


Than grabbed this:
[http://read.pudn.com/downloads110/ebook/456020/E-EDID%20Standard.pdf](http://read.pudn.com/downloads110/ebook/456020/E-EDID%20Standard.pdf)
and
a edid editor.
If you know what your doing from the above document you can probably get away with ghex.
I downloaded this(download link top left):
[http://www.entechtaiwan.com/util/moninfo.shtm](http://www.entechtaiwan.com/util/moninfo.shtm)
It's windows based but the most explicit and simple interface I could find.

I altered the screen size and the first standard timing to match the modeline cvt gave me following the VESA EDID doc from above.

The attached PNG shows the EDID.BIN as viewed in ghex.

To used the custom edid you need this line in your xorg.conf in the Device section:
Option "CustomEDID" "DFP-0:/yourlocation/yourEDIDfilename"


I hope this helps someone else avoid some of the leg work.

---

