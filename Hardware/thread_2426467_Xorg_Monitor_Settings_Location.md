---
title: "Xorg Monitor Settings Location"
date: 2019-09-09
forum: Hardware
---

### Post by dora5 on 2019-09-09
Point of xorg.conf is allegedly that it keeps track of your monitor settings.  

My system doesn't have one and refused to use the one I created.   I'm using Ubuntu 18.04.

Where, please does Xorg actually keep the monitor settings?   I can NOT find that information ANYWHERE.   Not even in books about Ubuntu 18.04.

If you start changing things about how the system functions and refusing to share what changes you made when something goes wrong, you're no better than Mint - and that's the most important reason why I won't use Mint!

---

### Post by dora5 on 2019-09-09
Uno mas.  What IS the configuration file, what is its name, and where is it stored?   Mary Poppins is not running our systems by magic from the clouds!   "Modern" or not, our monitor and video settings are programmed somewhere.

---

### Post by CatKiller on 2019-09-09
The resolution that you've set for your desktop environment is stored in ~/.config/monitors.xml, and has been for some time.

Otherwise resolutions are auto-detected at startup.

---

### Post by TheFu on 2019-09-09
/etc/X11/xorg.conf but it doesn't exist by default.  There are a few other places X11 settings can be stored.  According to the manpage:
       Xorg uses a configuration file called xorg.conf and files ending in the
       suffix .conf from the directory xorg.conf.d for its initial setup.  The
       xorg.conf configuration file is searched for in  the  following  places
       when the server is started as a normal user:
```

           /etc/X11/<cmdline>
           /usr/etc/X11/<cmdline>
           /etc/X11/$XORGCONFIG
           /usr/etc/X11/$XORGCONFIG
           /etc/X11/xorg.conf
           /etc/xorg.conf
           /usr/etc/X11/xorg.conf.<hostname>
           /usr/etc/X11/xorg.conf
           /usr/lib/X11/xorg.conf.<hostname>
           /usr/lib/X11/xorg.conf
```

Also, /etc/X11/xorg.conf.d/ works.  I put my settings in that directory.  If it doesn't exist, create it.  I've had to override the EDID information from a DVI-D to VGA adaptor to get the true resolutions supported by the monitor.  If you google for "modeline", some examples will probably be shown.  Really, the best solution is to get the EDID information from the monitor directly, which includes all the modes and timings. If that doesn't work automatically, then you can force it to be used by saving the EDID information into a binary format and telling the xorg.conf file to use it.

Most of my systems don't have monitors.xml files anywhere. Don't know why. Perhaps because I don't run any of the KDE or Gnome-based DEs.

---

