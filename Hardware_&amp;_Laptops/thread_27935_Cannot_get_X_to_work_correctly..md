---
title: "Cannot get X to work correctly."
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by mrambo3501 on 2005-04-18
I decided to give Kubuntu a whirl as I've seen it mentioned quite a bit recently. I'm using an IBM NetVista that has an integrated 15" LCD Display (an all-in-one) and uses an SIS 630 chipset.

The installation has went ok except for X. The symptoms are (listed in order of occurance frequency) (1) Black screen (2) Blue screen with no content shifted about 20% to the right (3) Gray screen with varying numbers of vertical lines that seems pretty clearly to be KDE (also shifted right about 20%). I can see a vertical line move when I move the mouse.

I've tried using dpkg-reconfigure xserver-xorg and tried numerous options therein. It looks like it is detecting the chipset correctly. I'm not as sure about the monitor as I'm not sure how it _should_ appear.

I've tried editing xorg.conf and manually defining different resolutions and color depths.

The only thing I see that obviously appears to be an error in the X log is that the x font server at 7100 is not running but there also appears to be files listed as a backup so I don't know how significant that is. I've spent the most amout of time trying to figure out how to tell X it is using an LCD screen instead of a normal monitor but don't see that option.

Any suggestions out there on getting Kubutu to work on this hardware of is it just incompatible?

Thanks.

---

### Post by heimo on 2005-04-18
Sounds like driver issue, but I'm not certain. I'd try vga or vesa driver just to find out if it's about that. Also can you post the Monitor section? Is there VertRefresh and HorizSync lines defined? (that has caused about 90% problems I've seen here about Ubuntu+xorg)

---

### Post by mrambo3501 on 2005-04-18
Yes, there are HorizSync and VertRefresh lines present.
Here is the way it was originally setup.

Section "Monitor"
          Identifier "Generic Montor"
          Option "DPMS"
          HorizSync "28-49"
          VertRefresh "43-72"
EndSection

Here is how I have it setup now.

Section "Monitor"
          Identifier "Generic Montor"
          ModelName "Flat Panel 1280x768"
          Option "DPMS"
          HorizSync "31.5-37.9"
          VertRefresh "50-70"
EndSection

The above comes mostly from guesses I have made after looking at how Mandrake 10 set up my laptop. It has fixed the screen shifted right problem but nothing else. The 1280x768 part comes from how knoppix 3.6 set up X. Unfortunately nothing else in the way knoppix set things up seemed to help. One of the things I noticed is that there are no modelines anywhere. My laptop has them and knoppix had them when I tried that (though they didn't help though when I copied them xorg.conf on this unit).

Thanks for the help.

---

### Post by heimo on 2005-04-18
My long post on this thread has instructions how to setup a custom modeline:
[http://www.ubuntuforums.org/showthread.php?t=21984]("http://www.ubuntuforums.org/showthread.php?t=21984")
If it's about that. You should check logs and see if there are valid modelines selected, or are they disabled (hsync out of range etc). If you make a custom modeline, make sure that it's hsync is in range (HorizSync "31.5-37.9").

---

### Post by mrambo3501 on 2005-04-18
I can add now that the vesa driver works and the setup looks otherwise the same. Looks like it is indeed the sis driver and this hardware.

Thanks for the help. At least I can see a display now.

---

### Post by Stormy Eyes on 2005-04-18
You don't need Horizontal and Vertical sync lines if your display is a flat panel. Comment them out; they're for CRT displays, not flat panels.

---

### Post by heimo on 2005-04-18
[QUOTE=Stormy Eyes]You don't need Horizontal and Vertical sync lines if your display is a flat panel. Comment them out; they're for CRT displays, not flat panels.[/QUOTE]

Not quite. I'd say that it has more to do with the video signal (digital/analog). Most TFTs still have analog inputs and those values still apply (even those without d-sub connectors can - at least technically - take analog signal). You can also leave those values out for CRT and get a picture on your screen (done that) - Xorg just uses default values.

---

