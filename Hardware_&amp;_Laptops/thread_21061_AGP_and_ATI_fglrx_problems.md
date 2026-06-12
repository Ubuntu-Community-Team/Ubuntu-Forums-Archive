---
title: "AGP and ATI fglrx problems"
date: 2005-03-20
forum: Hardware &amp; Laptops
---

### Post by bluerpk on 2005-03-20
Hello
  I know there has been a lot of discussion about ATI and AGP problems on this post. But none of them seem to provide a solution to the problem I am facing. 

I have a AMD 64 3200+, ATI Radeon 9600 Pro. The motherboard is a Uli 1689 board.
I have installed Hoary and then the xorg-fglrx-8.8.25(?) through Synaptic. 
Then I ran fglrx-config and changed the driver to fglrx instead of ATI.
I get a glxgear score of around 50-60 FPS. Slow by any standards.

When I do make menuconfig, I go to Device Driver->Char. Here i see the agp option as 
-- /dev/agp

does this mean that by default AGP is selected or does it mean that AGP is not enabled?

I tried this in 2.6.10 and 2.6.11.3 kernel and in both I get the same line in menuconfig. 

Please help. I really want to use Ubuntu as my primary OS, but this is stopping me from doing that. 

Thanks for the help.

---

