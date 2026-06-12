---
title: "[SOLVED] Ubuntu 8.10 Screen Resolution (intel)"
date: 2008-11-23
forum: Hardware
---

### Post by icanfly0307 on 2008-11-23
Hi all,
       I've just installed Ubuntu 8.10 after getting rid of 8.04. Everything is working well EXCEPT for my monitor!!!:confused: It's stuck at 800x600. In Hardy, there was an app called "Screens and Graphics". However, I can't seem to find it in Intrepid. I'm running an Intel 82815 Integrated Graphics Card with the i810 driver. Does anyone know how to kick it up to the maximum 1024x768 resolution?

Thanks a lot. :)

---

### Post by king_lear on 2008-11-23
Try System -> Preferences -> Screen Resolution

---

### Post by prshah on 2008-11-23
> **icanfly0307 said:**
> In Hardy, there was an app called "Screens and Graphics". However, I can't seem to find it in Intrepid.

See [Bring Back Screens and graphics Please!]("http://ubuntuforums.org/showthread.php?t=980983&highlight=displayconfig-gtk")

---

### Post by gatman3 on 2008-11-24
It probably didn't load the intel driver and is just using the vesa driver.

Look through the Xorg.0.log and see if you can find which driver it loaded.

You may have to specify it manually in you /etc/X11/xorg.conf file.  You would add a line in the Device section to specify either the "intel" or "i810" driver.  Something like this:

```
Section "Device"
        Identifier  "Configured Video Device"
        Driver      "intel"
.
.
.
EndSection
```

Typically if Xorg can't figure out which driver to load, it falls back to VESA and will max at 800x600.  I've seen this happen especially with Intel graphics for some reason.  Specifying the driver manually in the /etc/X11/xorg.conf usually does the trick.

---

### Post by icanfly0307 on 2008-11-24
Thanks for all your help guys. prshah's link did the trick. Thanks again!

---

