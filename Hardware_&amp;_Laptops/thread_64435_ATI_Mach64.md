---
title: "ATI Mach64"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by msti on 2005-09-11
First time linux user. Just tried to install Hoary and  on startx get a fatal error

(EE) ATI(0): Driver can't support depth 24
(EE) Screen(s) found, but none have a useable configuration

I tried to find man atimisc both locally and at wiki.x.org and there is apprently no manual page.

How do I fix this? The mach64 video card onlysupports 24 bits for me at 800 x 600 or less, 16 bits at 1024 x 768 

Clear simple instructions would be appreciated.

Mark

---

### Post by glug101 on 2005-09-16
> **msti]First time linux user. Just tried to install Hoary and  on startx get a fatal error

(EE) ATI(0): Driver can't support depth 24
(EE) Screen(s) found, but none have a useable configuration

I tried to find man atimisc both locally and at wiki.x.org and there is apprently no manual page.

How do I fix this? The mach64 video card onlysupports 24 bits for me at 800 x 600 or less, 16 bits at 1024 x 768 

Clear simple instructions would be appreciated.

Mark[/QUOTE]
 Hey Mark,
    A quick fix would involve starting X with the following command:
> startx -- -depth 16

However, that could get pretty old fast (although I once used it for months said:**
> man XF86Config 

Please note that the command is case sensitive.  Blanking out all the definitions for 24bit color should do the trick.  If you would like more personalized instructions, pop me up here or wherever and I'll help you out.

Cheers!

---

