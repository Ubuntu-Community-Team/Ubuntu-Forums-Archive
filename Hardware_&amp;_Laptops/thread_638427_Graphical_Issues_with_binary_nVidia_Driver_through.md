---
title: "Graphical Issues with binary nVidia Driver through Wine"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by abrichr on 2007-12-12
When Half Life 2 first came out, I was still on Windows XP, and it ran extremely well on my Compal HEL80 laptop, which has an Intel Core2 Duo T7400 64-bit processor, 2048MB DDR2 ram, and a GeForce Go 7600 256mb PCI-E video card.

I've been on Ubuntu for a little over a year, and recently I purchased the Orange Box, which has Half Life 2 and its sequels, as well as some other games.  I followed the guide at [http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/](http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/) in order to get it running, although I downloaded and installed a pirated version from mininova.org that does not use the Steam program that I dislike so much.

I used Envy to install the latest nVidia drivers (100.14.23), and am using the latest version of Wine (0.9.50).  I am able to run the game just fine, but even on the lowest resolution with medium graphics settings, there are areas with noticeably laggy framerates, random flickering, and just a solid purple screen when I'm underwater.  All in all, it's terrible compared to how the game works under Windows XP.

Someone commented on the blog post (previous link) that some graphics issues can be fixed by altering the registry value in HKEY_CURRENT_USER\Software\Wine\Direct3D.  But I don't even have a Direct3D folder in this location.

I'm beginning to wonder if I've perhaps missed something?  Am I required to install a driver through Wine?  What else can I do in order to improve on or fix the graphical issues?

---

### Post by abrichr on 2007-12-12
I created the key and added the values, which did increase the graphics level somewhat -- but the choppiness and flickering is still there.  Also, for some reason now my gnome panels are still visible while playing the game, and actually cover the top and bottom of the game window's contents (even though it's set to full screen).  I removed the keys, but they're still there.

---

