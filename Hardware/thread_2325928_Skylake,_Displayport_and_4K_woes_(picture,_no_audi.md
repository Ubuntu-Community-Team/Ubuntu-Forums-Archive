---
title: "Skylake, Displayport and 4K woes (picture, no audio)"
date: 2016-05-26
forum: Hardware
---

### Post by zuti on 2016-05-26
Ok. I've been fighting with this issue for weeks now. 

I have fresh Intel NUC ([http://www.intel.com/content/www/us/en/nuc/nuc-kit-nuc6i5syk.html](http://www.intel.com/content/www/us/en/nuc/nuc-kit-nuc6i5syk.html)) set up as a HTPC and connected to a UHD tv, which is capable of doing 3840x2160@60fps. The computer is connected with a DP1.2->HDMI 2.0 adapter ([http://www.club-3d.com/index.php/products/reader.en/product/mini-displayport-12-to-hdmi-20-uhd-active-adapter.html](http://www.club-3d.com/index.php/products/reader.en/product/mini-displayport-12-to-hdmi-20-uhd-active-adapter.html)) and even though the system doesn't automatically detect a 60Hz mode, I can get it to work with a modeline based on the displays EDID information. 

```
Modeline "3840x2160" 533.28 3840 3888 3920 4000 2160 2163 2168 2222 +hsync -vsync
```
The above modeline (CVT-RB) gives a stable image, but no sound. No matter what I do. If I drop down to 1080p, I get sound. 

If I use a slightly "invalid" modeline, which has a much higher pixel clock and isn't a "reduced blanking" mode, I get a picture with some flickering pixels and clipping/popping audio. 
```
"3840x2160_60.00" 594.000 3840 4016 4104 4400 2160 2168 2178 2250 +hsync +vsync 
```
(basically just 2x pixel clock from a 30Hz mode)

I tried a Windows to Go USB media to check if there is any difference, and 4K@60Hz works fine with audio, and apparently exactly the same info as the first listed modeline. 

I just can't understand what to do next. Any help getting the modeline in order would be very welcome.

---

