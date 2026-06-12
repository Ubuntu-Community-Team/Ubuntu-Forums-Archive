---
title: "Is 3D accel possible with ATi M6 LY (thinkpad x31)?"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by ac251404 on 2006-08-08
I have been reading about people trying to get 3d accel working with this card (namely in Thinkpad X31's) and haven't really seen any definitive answers. I would love to get XGL/Compiz working with Ubuntu but I don't want to beat my head into the desk for nothing. It seems pretty complicated but I am more than willing to jump in head first if I know it can be done. The fact that I am extremely new to linux doesn't help but I have used it before and am fairly tech oriented. I swithced to the proprietary ATi drivers because the "vesa" driver seemed kinda poor performance-wise.

 Out of curiosity when I first loaded Ubuntu I did a glxinfo and it said Direct Rendering: yes. After the ATi drivers it says no. Two questions arise from this. 1) Can I run Xgl/Compiz with the default driver? If so why so many posts about getting this working? 2)Why would the built in driver have Direct Rendering support but the one from ATi not?

thanks,
-ac

---

### Post by gruffy-06 on 2006-08-08
Yes.

Ubuntu comes with propietary drivers for ATI cards and other things which helped me run Ubuntu properly and connect to the net. This is in the "resticted" section in the software channels.

---

### Post by gruffy-06 on 2006-08-08
If that didn't help, then go to the ATI site, then download the binary-only driver there.

---

### Post by gruffy-06 on 2006-08-08
Me too. You'll have to wait until XGL/Compiz moves from universe to main AND get the latest driver updates.

---

### Post by wiresquire on 2006-08-09
I used to have the same card (I think) in a HP laptop. aka 320M, aka Radeon Mobility U1.

There's no support from the ATI proprietary drivers because they only support later model graphics cards. I don't think the proprietary drivers will help you at all.

The open source drivers included with ubuntu include support for older cards.

I believe the card uses shared memory, not dedicated memory on the graphics chip. This was the main reason I ended up selling the HP, as performance was not good. Unfortunately, I never got to the stage of getting 3d working with the M6, as this was a good 3 years ago.

So, even with 3d acceleration, do not expect performance to be good. I'm not convinced it would be able to run later games, or Compiz etc. At least not with decent speed.

hth
ws

---

### Post by ac251404 on 2006-08-09
The card has 16mb dedicated memory I do believe. Also I have heard that Compiz can run on fairly anything, including i985 (or whatever the numbers are) intel integrated graphics, but I think it was just in a forum somewhere so could be innaccurate, thats why I'm asking.

Edit: Also this card runs WarCraft 3 on medium settings just fine so I think (read: hope) it can handle Compiz.

---

### Post by gustl87 on 2006-08-16
yes open gl works !

i am using an ati m6 and 3d acceleration works with the "ati" driver, but sometimes it used to freeze / lockup.

but then i found this on the web^^:

[http://forums.gentoo.org/viewtopic-p-3237995.html](http://forums.gentoo.org/viewtopic-p-3237995.html)

and it worked after some modifications.
so it never freezed again (till now).

so you should use the driver called "radeon" and if freezing continues, you might edit it as follows:

```
Section "Device"
        Identifier      "[PUT YOUR CURRENT CARD NAME HERE]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        #Option          "AGPMode" "4"
        #Option          "AGPSize" "16" # default: 8
        Option          "AGPFastWrite" "false" # MUST BE FALSE!!!
        Option          "SWcursor" "true" # MUST BE TRUE!!!
        #Option          "RingSize" "4"
        #Option          "BufferSize" "2"
        Option          "EnablePageFlip" "false" # necessary?
        Option          "EnableDepthMoves" "false" # MUST BE FALSE!!!
        #Option          "RenderAccel" "false"
        #Option          "AccelMethod" "XAA" # or XAA, EXA
        #Option          "DDCMode"
        #Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "false" # MUST BE FALSE???
        #Option          "DynamicClocks" "true"
        #Option          "bioshotkeys"   "True"
        #Option          "XAANoOffscreenPixmaps" "true"
EndSection

```

#sorry for my bad english.

---

