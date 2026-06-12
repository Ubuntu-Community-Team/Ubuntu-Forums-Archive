---
title: "x700 mobile resolution lower with fglrx"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by roodhoedje on 2005-10-14
I have a acer aspire 5024 with a x700 from ati. I installed the ati driver in the repository and it loads and does everything it is supposed to do except using the 1280*800 resolution wich is default with my tft panel. Instead it uses 1024*768 wich is very annoying cause it displays fonts wrong ect ect.. 

Does anybody know how to force the ati driver in using the 1280*800 resolution.

(xorg.conf did not change except the driver of the x700, wich changed from ati to fglrx)

---

### Post by DaveA on 2005-10-19
You can modify display settings in xorg.conf; look for a section like this (near the end of the file):

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection

Modify "1280x1024" with "1280x800", save, close, restart X.. that's it!

If for some reason you don't have "1280x1024" you can just add "1280x800", the only inportant thing is that it must come first in the line Modes, for ex:

Modes "1280x800" "1024x768" ...

as this is the order in which X parses preferred resolutions.

Cheers ;)

---

### Post by grinias on 2005-10-19
[QUOTE=roodhoedje]I have a acer aspire 5024 with a x700 from ati. I installed the ati driver in the repository and it loads and does everything it is supposed to do except using the 1280*800 resolution wich is default with my tft panel. Instead it uses 1024*768 wich is very annoying cause it displays fonts wrong ect ect.. 

Does anybody know how to force the ati driver in using the 1280*800 resolution.

(xorg.conf did not change except the driver of the x700, wich changed from ati to fglrx)[/QUOTE]

This is a known bug of this version of ATI driver. See these

[http://www.ubuntuforums.org/showthread.php?t=76116]("http://www.ubuntuforums.org/showthread.php?t=76116")
[http://ubuntuforums.org/showthread.php?p=423589&posted=1#post423589]("http://ubuntuforums.org/showthread.php?p=423589&posted=1#post423589")

---

