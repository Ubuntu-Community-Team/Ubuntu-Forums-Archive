---
title: "cannot init AGP"
date: 2004-11-04
forum: Hardware &amp; Laptops
---

### Post by niroht on 2004-11-04
Hi,

So like many, I'm trying to get 3d accel working. I have an ATI 9500pro. I've installed the drivers, and tried editing the XF86Config-4 file, having fglrxconfig make one for me, and editing the one fglrxconfig made.

The error that seems to be holding me back is this:
> (EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENOMEM"
(EE) fglrx(0): cannot init AGP
 
Is it possible I don't have AGP support in my kernel or something along those lines? If so, what would be the easiest way of going about fixing that? TIA

---

### Post by mercurus on 2004-11-04
This page doesn't seem to answer the question comprehensively, but it does hint in the right direction. It gives one option, and makes a lot more sense than the Russian debian mailing list results I got. I wish my Russian and Cyrillic were up to scratch ! 

[http://www.wlug.org.nz/RadeonNotes](http://www.wlug.org.nz/RadeonNotes)

This page seems to provide some more insight into the source of the problem.

[http://www.happypenguin.org/show?ATI%20Radeon%20Linux%20Display%20Drivers&start=20](http://www.happypenguin.org/show?ATI%20Radeon%20Linux%20Display%20Drivers&start=20)

It looks like it is kernel-based and could get icky, depending on what is compiled into the stock Ubuntu kernel ... If it turns out that something icky IS compiled into Ubuntu's kernel by default, then I'd submit a bug report indicating as much.

Cheers
mercurus

---

### Post by niroht on 2004-11-04
Thanks for that info! I actually got it working (well closer anyway). The one line that helped me was this:
> and **rebooting** - if at any stage the fglrx AGPGART has loaded, you're shit out of luck.I was just killing the X server each time I'd try (ctrl+alt+backspace). Rebooted and bingo.

My only issue now is GDM loads up in the big screen mode (2560x1024), but after logging in, only one screen actually works. The other screen is all white and my mouse wont move to it. But I'm working one it.

Again thanks

---

