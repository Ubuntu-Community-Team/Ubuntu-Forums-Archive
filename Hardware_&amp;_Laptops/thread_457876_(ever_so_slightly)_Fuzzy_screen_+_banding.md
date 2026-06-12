---
title: "(ever so slightly) Fuzzy screen + banding"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by smylie on 2007-05-29
I've got an Intel GM965 video card on a laptop with a 1680x1050 screen.
It works, and runs at the correct resolution at 24 bit color depth, but every thing is slightly fuzzy and there is pretty severe banding with the default fiesty wallpaper - more like it was running at 16 bit, rather than 24.

The screen looks nice and crisp in Windows XP, so i'm fairly sure it's a configuration thing.

xdpyinfo states:

```
screen #0:
  dimensions:    1680x1050 pixels (331x207 millimeters)
  resolution:    129x129 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
```

Which i suspect (or guess at least) is the problem - shouldn't the resolution be 96x96 dpi?

Does anyone know if that's likely to be the problem? I can see that would account for the fuzzyness, but I'm not sure what would account for the banding . . . 

Cheers 
Dave Smylie

For reference my xorg.conf:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
```

---

### Post by smylie on 2007-05-31
Turns out it's not the dpi setting. I found eventually, I could specify the dpi by
```
$ startx -- -dpi 96x96
```

That worked, in that X started, and xdpyinfo claimed it was running at 96x96 dpi.
However, it made no difference to the blurriness of the screen.

So

 - definitely running at 1680x1050
 - the dpi setting seems to be irrelevant to the issue. 
 - x says it is running at 24 color depth (but I don't believe it).
 - the screen itself is blurred - it's not just the fonts, but everything.

Any one got any ideas?   This feels like it's going to start making my eyes bleed . . .  (or at the very least, drive me back to XP where at least I can look at the screen without my eyes starting to water . . . )

Cheers
Dave Smylie

---

### Post by smylie on 2007-06-04
*bump*

---

### Post by smylie on 2007-06-21
this issue is (mostly) sorted. See this thread  [here]("http://ubuntuforums.org/showthread.php?t=464907") for details

Cheers
Dave Smylie

---

