---
title: "Acer Aspire One"
date: 2011-04-20
forum: Hardware
---

### Post by josempans on 2011-04-20
I've recently installed Ubuntu in my desktop machine, and I really liked it. So, when my sister told me about the problems that she was having with Vista in her Acer Aspire One (registry, hangings, too too slow, some virus, etc), I didn't doubt about telling her to install Ubuntu. So, I've downloaded Netbook Edition from the ubuntu page... Everything seems to work... except for:

First: an error with "Unity" telling that it can't work cause some controllers wrong function
Second: When I've tried to install drivers for video, and tried to change the effects.

From there everything went wrong, I couldn't find any sure guide, or "final guide" to solve this. Is possible to solve this... I've read a lot, lot, of threads... spanish, english... and nothing worked... I've tried installing some xorg-something but then... Ubuntu never started again... so, I want to give my sister a solution... (an open source one, hehe).

Thanks!! in advance

---

### Post by mikewhatever on 2011-04-20
What version of Ubuntu did you try installing? What graphics card is there? What driver (or drivers - how many?) did you try installing?

---

### Post by josempans on 2011-04-21
Ubuntu Netbook Edition 10.10
I guess some Intel Graphics Card (GM965?) I've tried to find the name but lspci doesnt show it
I've tried with Xorg-something-video-intel

---

### Post by dandnsmith on 2011-04-21
"Intel Graphics Media Accelerator 950" from the official sources.
Perhaps it's visible in a *lshw* listing - I've never tried it with mine (which my wife won't hear of having linux on).
When I tried the netbook version of 10.04 it seemed OK - 10.10 seems to have thrown up problems, some of them graphics, for a number of people.

---

### Post by josempans on 2011-04-21
I've did that and lshw shows me:
Video UNCLAIMED
Vga Compatible controller
vendor Intel...

---

### Post by josempans on 2011-04-21
ok, I was able to fix the screen resolution. No desktop effects, but at least the screen is 1360x768 now...

this is what I've did:

> *sudo add-apt-repository ppa:gma500/ppa && sudo apt-get update*

*sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config*

Source: [http://setupguides.blogspot.com/2010/10/installing-gma500-drivers-in-ubuntu.html](http://setupguides.blogspot.com/2010/10/installing-gma500-drivers-in-ubuntu.html)

Hope this helps to anyone with ACER ASPIRE ONE Video card trouble. Poulsbo drivers.

---

