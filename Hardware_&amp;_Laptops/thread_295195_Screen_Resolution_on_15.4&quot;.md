---
title: "Screen Resolution on 15.4&quot;"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by DannyG on 2006-11-07
Hello,

I've just finished setting up Ubuntu on my Dell Inspiron 1300, and the last problem i'm having is with the screen.

The Inspiron 1300 has a 15.4" Widescreen, that uses Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller.

Now, when I check my Screen Resolution under System, I see that it is set to 1024x768 and 60Hz, and the screen does give a corner to corner picture but it seems very stretched. I don't have any other options to select here.

When I access /etc/X11/xorg.conf I see that I have

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection
```

Now, should this not mean that my screen should be displaying resolutions of 1280x800? Anyone got any advice on what to do here?

Thanks,

Daniel.

---

### Post by DannyG on 2006-11-07
Found this:

[http://ubuntuforums.org/showthread.php?p=1729147#post1729147](http://ubuntuforums.org/showthread.php?p=1729147#post1729147)

Worked perfectly.

---

### Post by ReaderRat on 2006-11-07
EDIT Too late...

---

### Post by dogman24 on 2007-05-17
Check this out, it does work I use it :popcorn:

[http://ubuntuforums.org/showthread.php?t=227045&highlight=resolution+1300](http://ubuntuforums.org/showthread.php?t=227045&highlight=resolution+1300)

---

### Post by Prometheus.172214 on 2007-05-17
I don't have the Dell notebook, what I have is the Hewlett Packard M2201TU. I see the same information when I run a /etc/X11/xorg.conf and I have tried the suggestions from the links mentioned above. I am still stuck at 1024X768. Any ideas what I can do, or is there a different method for this? The chipset in use is the same Intel 915 GM

---

### Post by heimo on 2007-05-17
Yeah, according to this, for Inspiron 1300 correct resolution is 1280x800.
[http://support.dell.com/support/edocs/systems/ins1300/en/om/om_en.pdf](http://support.dell.com/support/edocs/systems/ins1300/en/om/om_en.pdf) **warning, large PDF (37MB)**

For widescreen and Intel graphics chipset, try this:
[http://ubuntuforums.org/showthread.php?t=351647](http://ubuntuforums.org/showthread.php?t=351647)

---

