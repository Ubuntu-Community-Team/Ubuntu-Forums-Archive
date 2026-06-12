---
title: "Overscan over HDMI with intel GM45 on 11.04"
date: 2011-05-02
forum: Hardware
---

### Post by Joshua66 on 2011-05-02
Hi,
I have a Lenovo T500 laptop with a GM45 graphics chip. * Under*Ubuntu 11.04 (which shows intel Xorg driver version 2.14.0 in /var/log/Xorg.0.log),*when I connect an external LCD tv (sony bravia 46ex620) to the laptop via HDMI at 1080p, the 1920x1080 image on the tv extends beyond the borders of the tv by about 10%.
Anyone know what option can I set in the intel driver to tell it to send the raw 1920x1080 image without scaling it?

I presume there is an option because when I boot into windows Vista on the laptop and connect the external display, I have the same problem,*and the*"Intel Graphics and Media Control Panel" has an option to adjust horizontal and vertical scaling, which I can use to get rid of it. *I have the LCD tv "wide mode" set to "Full" (the other modes distort the image even more).

I saw the "scaling mode" option for LVDS and got excited because it sounds like that almost would do it, but alas, it is not available*for HDMI output.
Many thanks for any suggestions.
Josh

---

