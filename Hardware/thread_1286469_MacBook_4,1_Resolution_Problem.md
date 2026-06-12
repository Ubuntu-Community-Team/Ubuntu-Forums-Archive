---
title: "MacBook 4,1 Resolution Problem"
date: 2009-10-09
forum: Hardware
---

### Post by Lensflare on 2009-10-09
It's been a while since I've used Ubuntu, and back then I was running an old Gateway MX3215 with a piece of junk UniChrome card.  This time I'm running an Intel GMA X3100, so I still don't have a great graphics card.

I just installed Ubuntu 9.04 64-bit onto my 4,1 MacBook.  It's maximum resolution is 1280x800, but whenever I use Ubuntu (through Parallels) it doesn't detect my LCD screen and the maximum resolution is 1024x768.  Is there a driver I can install to edit this setting?  

Thanks in advance.

(Oh, and I'm not sure if I need to post the xorg.conf, but I don't know where it is anyways.)

---

### Post by nixscripter on 2009-10-11
Posting xorg.conf wouldn't hurt (it's in **/etc/X11/xorg.conf**), but the first thing I would suggest is just to tell it to run at the resolution. Just put this in your Screen section:

```

SubSection "Display"
    Depth           24
    Modes           "1280x800"
EndSubSection

```

See if that just works.

---

