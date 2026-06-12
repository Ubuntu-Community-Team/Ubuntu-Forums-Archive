---
title: "Problems with built-in webcam on 8.10"
date: 2008-12-07
forum: Hardware
---

### Post by Eeeff on 2008-12-07
Ok, there is no real simple way to describe this, so I'm just going to say exactly what happens and you can access this situation.
I actively visit a site called BlogTV.com. This website uses your webcam and mic devices to broadcast through Adobe Flash player.

When I get there first it says "Click to begin broadcasting". That works pergect, then Adobe Flash asks permission to acess my webcam and mic. That works perfect. But before I click allow, I see my cam in the background, and it's streaming fine. So I click allow for the flash player. It tells me one last time to cimply click on the screen to begin, and at this time my cam is still streaming. But as soon as I click it for the final time, it just freezes onto a still image.

So for some background information, I'm running a Dell Inspiron 1720 with a built-in webcam.

Please ask if anymore information is needed.

Thanks,

---

### Post by d3drocks on 2008-12-07
Totally know what you mean.
I have no idea how to fix this, but i also need to know, cause when i get a laptop, I'll not accept vista on it.

---

### Post by Eeeff on 2008-12-07
Bump

---

### Post by Eeeff on 2008-12-07
When I type lsusb in the terminal, this is what comes out.

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Eeeff on 2008-12-07
bump

---

### Post by bdoe on 2008-12-07
I don't have an answer for you, since I don't use my webcam, other than maybe check your system logs and see if something is throwing errors or exceptions.

I just wanted to comment that, you only posted this an hour ago, and already bumped it twice. This is generally considered poor forum etiquette. It usually takes about 24 hours for someone knowledgeable to see and reply to your post. By continually bumping it, all you're accomplishing is to bump someone else's thread off the first page and irritate people. It will not get your problem solved any faster.

---

### Post by residualbit on 2008-12-07
I had exactly the same problem. What I did you fix it was to remove "flashplugin-nonfree" and install the actual package straight from adobe. I think it's called adobe-flashplugin in synaptic.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
they even have it in a deb package.


If you already have that one installed, then i'm not too sure.

---

