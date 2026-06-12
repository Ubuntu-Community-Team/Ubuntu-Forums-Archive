---
title: "TV reports wrong physical size, PDFs are small"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by fa2k on 2007-12-10
Hi,
I have connected an Ubuntu box to a 32" LCD TV screen. I use a DVI-to-HDMI adapter. Most applications work just fine, but here is the problem:
- PDFs are incredibly small! At 400% magnification, I can fit four pages on the screen at once. Naturally, the text is completely unreadable. This goes for evince and gv
- The text in IDLE (a Python editor) is also so small that I can't read it. 

When looking close to the screen, I can see that the text is not rendered correctly, all that shows is a small pattern of pixels.

I suspect that my TV has an inflated self-image, reporting that it's a few meters across ;) It's either the DVI-to-HDMI adapter screwing up the information, or the TV itself being buggy. I should note that when using the open-source driver for my graphics card (a radeon hd 2400), the TV would only display at some weird resolution, like 1080x480 (don't remember exactly)

If the problem is the width and height info, how can I specify this manually (using the newest version of the fglrx driver). Any other ideas?

thanks,
marius


edit: and strangely, yes, I sometimes need to display PDFs on my TV, mostly presentations

---

### Post by fa2k on 2007-12-11
I fixed it! 

In the Monitor section of the Xorg.conf file, set
DisplaySize x y

Where x and y is the width and height of the monitor, in millimeters.
This is mine
```
Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        VendorName   "Plug 'n' Play"
        ModelName    "Plug 'n' Play"
       ** DisplaySize     711 400**
        Gamma        1
EndSection

```

---

