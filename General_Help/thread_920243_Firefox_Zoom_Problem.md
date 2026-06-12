---
title: "Firefox Zoom Problem"
date: 2008-09-15
forum: General Help
---

### Post by chris-at on 2008-09-15
When I use the full page zoom in Firefox on Kubuntu the images look 'pixelated' and hard to read while the same page will look fine in Firefox on Vista (see the attached png for a comparison).

What settings could have this effect and how can I fix it?

The images were taken with Firefox 3.0.1 on Kubuntu 8.04 in VMware and Vista SP1 also in VMware (both on the same host=vista) at [http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/)

The colors on the host and Vista VM are set to 32-bit.

On Kubuntu (with vmware tools installed) xdpyinfo says:
...
screen #0:
  dimensions:    1916x1121 pixels (406x238 millimeters)
  resolution:    120x120 dots per inch                 
  depths (7):    24, 1, 4, 8, 15, 16, 32               
  root window id:    0x40                              
  depth of root window:    24 planes                   
  number of colormaps:    minimum 1, maximum 1         
  default colormap:    0x20                            
  default number of colormap cells:    256             
  preallocated pixels:    black 0, white 16777215      
  options:    backing-store NO, save-unders NO         
  largest cursor:    32x32                             
...
TrueColor                                                        
    depth:    24 planes                                                        
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x23
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x24
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x25
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3e
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits

thanks, chris

---

### Post by gtsantos on 2009-03-01
I had this problem too.

Someone knows how we could correct it?

Thanks.

---

