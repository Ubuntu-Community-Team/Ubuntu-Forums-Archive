---
title: "SUCCESS:  Minimal install on IBM Thinkpad 570e"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by Brunellus on 2007-02-20
This is a much-belated follow-up to a previous post some months ago reporting a successful installation on my IBM Thinkpad 570e.

I had some issues with my wireless card, which uses the orinoco kernel module.  It appears that orinoco support is badly broken in all kernels after 2.6.12, so I was compelled to use the last Breezy kernel with Dapper's repositories.  No big deal, since I'm not installing anything that depends on the kernel, kernel source, or headers.

The complete installation report is on my blog:

[http://ouij.livejournal.com/207594.html](http://ouij.livejournal.com/207594.html)

This is a super-minimal installation.  I haven't gone into much detail with respect to package selection, but I should say that this is far from your default (K|U|Xu|Flux)buntu install.  No office suite, the kazehakase browser instead of firefox (with dillo and lynx), and NO non-free software.  No display manager means no graphical login, but since I don't really spend that much time in X on this computer, it's not that big a deal.  When I do startx, it's with Fluxbox.  

There is a long section at the end devoted to a few minor tweaks I made--default console font and remapping the keys so CapsLock became Escape.  Edgy and Feisty's init might be a bit different with respect to starting /etc/init.d/console-screen.sh --it should no longer be necessary to add the requisite line to /etc/rc.local

---

### Post by regomodo on 2007-05-02
Hi, i've had reasonable success with my Xubuntu Feisty install. Everything works apart from dodgy graphics (i.e laggy) and the undock function.

I noticed you say you get fluxbox (i guess through Fluxbuntu) to install on it. I tried Fluxbox in Vector Linux and it was very snappy. However, i tried to install it and after the login (FLuxbuntu, livecd) i get to a command line. I  had previously installed Fluxbuntu as a VPC and it worked fine on a desktop so i knew what was supposed to happen. Gave up in the end

I'll have to read your blog later for the details but i noticed you say nothing about the laptops RAM. Are you using the stock 64MB?

EDIT: just noticed about the lag issues in your other post. I'll change the bit depth in a mo

---

### Post by Brunellus on 2007-05-02
no, the lappy is pimped.  I've got the RAM maxed out at 320MB.

---

### Post by regomodo on 2007-05-02
> **Brunellus said:**
> no, the lappy is pimped.  I've got the RAM maxed out at 320MB.

lol. Yeah, me too. Boy does that extra 256MB make a  difference

I just tried to edit my xorg in PCLOS for my lappy. Killed it. Just set the defaultdepth to 16 and then after shutting down x it refused to start. Meh, i don't like KDE so i'm installing Xubuntu Feisty as i speak

---

### Post by regomodo on 2007-05-03
Awesome. Setting it 16bit worked a treat. Ubuntu Feisty(Xubuntu kept spitting errors about not being able to partition correctly)works reasonably well although much faster with it plugged in AC.

Did you figure out how to allow the undocking? I see nothing and i couldn't find anything in your blog.

---

### Post by Brunellus on 2007-05-03
> **regomodo said:**
> Awesome. Setting it 16bit worked a treat. Ubuntu Feisty works reasonably well although much faster with it plugged in AC.

Did you figure out how to allow the undocking? I see nothing and i couldn't find anything in your blog.
undocking is not something I've experimented with.  The 570E was not meant to be hot-swappable...and from what I gather even "warm-swapping" (i.e., swapping while the system is suspended) wasn't great under Windows, either.

---

### Post by regomodo on 2007-05-03
> **Brunellus said:**
> undocking is not something I've experimented with.  The 570E was not meant to be hot-swappable...and from what I gather even "warm-swapping" (i.e., swapping while the system is suspended) wasn't great under Windows, either.

OK, not a major issue. I had found that it was alright under windows. The only problems i found was, whilst "warm swapping", XP complained about a "power surge on the usb ports" but worked fine, even though i told it to undock.

Cheers anyways

---

