---
title: "External monitor and resolution problems"
date: 2010-10-13
forum: Hardware
---

### Post by huzzak on 2010-10-13
Hello!

I just upgraded to Maverick from Lucid and I am having problems configuring my external monitor to play nicely with my laptop.

[IMG]http://img.photobucket.com/albums/v101/Huzzak/Screenshot-1.png[/IMG]

The problem seems to be the size of the virtual monitor.  The medium grey box in the image doesn't expand as I resize the individual monitor resolutions, so parts of it get cut off.

I think in 10.04 the medium grey box in the upper left corner was set to the height of the external monitor and then the width of the laptop and the external monitors side by side.  This left some empty space that I couldn't really see below the laptop monitor since it isn't as tall as the external monitor, but I'm okay with that.

SO, does anyone know how to increase the size of the medium grey box?  Thanks!

---

### Post by huzzak on 2010-10-20
[Here is a relevant bug report]("https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/619663"), I think.  The good news is that it is fixed!  Right now you have to enable the proposed repository and upgrade the libdrm packages but I imagine that soon enough the proposed will filter to the accepted and it will just be included in the regular old updates.  Huzzah!

If you are impatient:

Open Synaptic Package Manager.
Settings > Repositories > Updates > select Pre-released updates (maverick-proposed)
Reload the sources.
Search for libdrm and upgrade the packages.
Reboot your computer, enjoy dual monitors at full resolution!

---

### Post by KristinaK on 2010-10-22
thanks I'll try this

---

