---
title: "Inspiron 1100 SLOW!"
date: 2008-05-25
forum: Hardware
---

### Post by Z_o-s-o on 2008-05-25
I'm still having some issues with this Inspiron 1100 I was given.

Its got a Celeron M 2.3 ghz....256mb ram....20 gig HDD....and intel 845G graphics.

The thing is, it's totally slow in Gutsy / Hardy. In windows XP this thing is snappy, but in ubuntu, even with the clock speed loked at 2.3 ghz, it crawls.

One thing of note, is that the onboard USB ports are burned out (known issues with the southbridge?), but Im thinking tthat because XP runs so well on it, thats not hindering performance.

Compiz will enable just fine (only 8mb gfx memory) but even with desktop effects turned off, its slow.

The one thing I noticed is that it appears to be using Mesa when I type "glxinfo | grep OpenGL".....

Any help is great,

Z_o-s-o

---

### Post by Z_o-s-o on 2008-05-26
*bump*

---

### Post by Z_o-s-o on 2008-05-26
Update:

glxgears is only giving me 300 frames per second...if that helps anyone?

---

### Post by Living2007 on 2008-05-26
> **Z_o-s-o said:**
> I'm still having some issues with this Inspiron 1100 I was given.

Its got a Celeron M 2.3 ghz....256mb ram....20 gig HDD....and intel 845G graphics.

The thing is, it's totally slow in Gutsy / Hardy. In windows XP this thing is snappy, but in ubuntu, even with the clock speed loked at 2.3 ghz, it crawls.

One thing of note, is that the onboard USB ports are burned out (known issues with the southbridge?), but Im thinking tthat because XP runs so well on it, thats not hindering performance.

Compiz will enable just fine (only 8mb gfx memory) but even with desktop effects turned off, its slow.

The one thing I noticed is that it appears to be using Mesa when I type "glxinfo | grep OpenGL".....

Any help is great,

Z_o-s-o
These spec are compatible with Xubuntu, a lihgt-weight version of Ubuntu.

512mb of RAM is required for Ubuntu.

---

### Post by Z_o-s-o on 2008-05-26
I did manage to get 256 megs MORE ram for it...so it has 512mb now...and its still slower than hell.

glx gears is only giving me 300 fps..therefore I think my issue with slow performance must be graphics related?

---

### Post by Z_o-s-o on 2008-05-26
Bump

---

### Post by Living2007 on 2008-05-26
> **Z_o-s-o said:**
> I did manage to get 256 megs MORE ram for it...so it has 512mb now...and its still slower than hell.

glx gears is only giving me 300 fps..therefore I think my issue with slow performance must be graphics related?
Has the driver been updated yet?

---

### Post by Z_o-s-o on 2008-05-26
Its using the i810 or intel driver that came with Hardy...

I dont know how to install another one...maybe you can help?

---

### Post by Living2007 on 2008-05-26
> **Z_o-s-o said:**
> Its using the i810 or intel driver that came with Hardy...

I dont know how to install another one...maybe you can help?
Go to google and type```
i810 or 845G
```then```
site:packages.ubuntu.com
```
It should be able to find it

---

### Post by Z_o-s-o on 2008-05-27
I'm really not sure what I need to do here.

In the driver section in xorg I can put "i810" or "intel" and the system is still slow.

When I type glxinfo, I am getting direct rendering, but Its saying its using Mesa....

I need to know, is the i810 driver supposed to use mesa, and if not how can I get it straightened out.

---

### Post by Living2007 on 2008-05-27
> **Z_o-s-o said:**
> I'm really not sure what I need to do here.

In the driver section in xorg I can put "i810" or "intel" and the system is still slow.

When I type glxinfo, I am getting direct rendering, but Its saying its using Mesa....

I need to know, is the i810 driver supposed to use mesa, and if not how can I get it straightened out.
I don't what to say I can't help, but that above is something I'm not quite sure about. Sorry (](*,) me)

---

### Post by Fredo on 2008-05-28
Hi!

I have a Dell Dimension 2400, with the same graphics card. I can confirm the really poor performance with Hardy. With Gutsy, the card performed quite well, so it seems to be only a Hardy issue.

I'd appreciate any help on this topic.

Cheers,
Fredo

---

