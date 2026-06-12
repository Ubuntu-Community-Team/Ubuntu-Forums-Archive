---
title: "no choice for screen resolution"
date: 2005-02-17
forum: Hardware &amp; Laptops
---

### Post by jamaas on 2005-02-17
I've just loaded Hoary and it seemed to work fine, booted again and it set up the screen resolution as 640x480 ... not good.  When I go to the screen resolution menu it is also the only choice I have ... which is also not good.  Did I overlook loading something important?  Can I fix it with synaptic or apt-get?

Thanks

Jim

---

### Post by csindone on 2005-02-17
[QUOTE=jamaas]I've just loaded Hoary and it seemed to work fine, booted again and it set up the screen resolution as 640x480 ... not good.  When I go to the screen resolution menu it is also the only choice I have ... which is also not good.  Did I overlook loading something important?  Can I fix it with synaptic or apt-get?

Thanks

Jim[/QUOTE]
 I had the same problem when I upgraded to Hoary with my Nvidia. I downloaded the drivers and activated them but the resolutions wouldn't go as high as I wanted(1280x1024). I found that dropping the refresh rate to 75Hz and saving the settings then restarting gave me more choices.

---

### Post by cyberchills on 2005-02-17
Does Hoary have an XF86Config-4?  If so it should be located /etc/X11/
You may want to check this out the "Screen" section.  Make sure you have a Display Subsection that has your DefaultDepth, with a valid mode such as 1024x768

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. SuperSavage IX/C SDR"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection

---

### Post by cyberchills on 2005-02-18
It looks like Hoary uses xorg so just use the file :  /etc/X11/xorg.conf.  Everything else should still be relevant.

---

### Post by jamaas on 2005-02-18
Thanks guys,  I got it to work, for some reason it seems to work with the vesa driver .... don't ask me why it won't with ati, which it is.  At least I can see something again!

Jim

[QUOTE=cyberchills]It looks like Hoary uses xorg so just use the file :  /etc/X11/xorg.conf.  Everything else should still be relevant.[/QUOTE]

---

