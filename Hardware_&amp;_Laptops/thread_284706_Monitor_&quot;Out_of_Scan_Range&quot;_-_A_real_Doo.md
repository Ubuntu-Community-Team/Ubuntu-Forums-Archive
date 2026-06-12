---
title: "Monitor &quot;Out of Scan Range&quot; - A real Doozie"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by rebelfallen on 2006-10-26
Pretty please see this thread to help me out, I am desperate:

[http://ubuntuforums.org/showthread.php?t=284703](http://ubuntuforums.org/showthread.php?t=284703)

---

### Post by hikaricore on 2006-10-26
Using a dual head can be kinda complicated.  You HAVE to set both monitors to use the same resolution (unlike in windows) or it will not work, you'll see graphical corruption or the monitor just won't come on at all.  It's best to use two monitors with relatively similar ranges.

But this right here is your main problem:

```
Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                [SIZE="2"]**Modes    "1280x1024" "1024x768"**[/SIZE]
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "Videocard0"
        Monitor    "Monitor1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                **[SIZE="2"]Modes   "1024x768" "800x600"[/SIZE]**
        EndSubSection
EndSection
```

I'm assuming either both monitors are trying to use 1280x1024 at the same hz range and one doesn't support it... or more like you confused the @$%@ out of xserver.  Also try setting your color depth to 16 instead of 24 as this causes conflicts in some setups... especially dual heads.  Once you get it working and learn the limitations of each display then you can backup that xorg.conf file and experiment.

One more think, even tho you said please, posting a HELP ME thread linking to another thread you only wrote 20 minutes ago and redirecting folks is kinda rude.  :)

---

