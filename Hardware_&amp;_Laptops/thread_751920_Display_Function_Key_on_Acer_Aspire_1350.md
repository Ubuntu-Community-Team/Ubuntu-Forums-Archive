---
title: "Display Function Key on Acer Aspire 1350"
date: 2008-04-11
forum: Hardware &amp; Laptops
---

### Post by banoncom on 2008-04-11
Hi.

I have just installed Ubuntu 7.10 on my acer aspire 1350
Most things work well and I am slowly but surely getting to a stage where it will be fully functional.

I am currently trying to get the Fn+F5 (Display toggle) to work so I can switch between an external monitor and the built in display without having to reboot.

I have installed the latest non beta version of keytouch (2.3) and it has all the function keys working bar the Fn+F5. I know the key combo works under windoze, but can't get it to work with ubuntu.

Any suggestions or advice would be much appreciated.

Cheers.

---

### Post by rjmoerland on 2008-04-12
Hah! Thanks for mentioning keytouch. Just improved my laptop life :D

---

### Post by fizzybrain on 2008-06-29
Sorry I can't help you with your problem, but maybe you can help with mine - I'm trying to use a 1280x1024 TFT external monitor with my acer 1350, but can't get anything better than 1024x768. Have you managed it? Could you maybe post your /etc/X11/xorg.conf for me? Ta.

EDIT:
Sorry, my first post wasn't relevant to the original question - I think I must have been panicking. In case anyone stumbles across it, I will answer my own question, and maybe that of the original poster:
xorg.conf is on the sidelines now - let xrandr handle everything:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)
You can use it to switch internal and external monitors off individually using simple commands/scripts - these could probably be linked to function keys (with keytouch?)
However I found (on a different machine) that xrandr didn't like the proprietary ATI drivers, so I'm back to using fglrx.
I *didn't* get two monitors working properly (i.e. with individual control over each one) on my acer 1350 using xrandr, but I didn't try disabling the proprietary driver, which is likely to have been the problem.
And now the 1350 is dead so I can't go back and try (g0dd@mn cheap Poundshop USB hub!!!^&%"$!&^%!!).

Share and Enjoy

p.s. I can't believe that g0dd@mn got auto-edited! lol

---

