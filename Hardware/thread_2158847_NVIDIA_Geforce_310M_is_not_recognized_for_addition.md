---
title: "NVIDIA Geforce 310M is not recognized for additional drivers"
date: 2013-06-30
forum: Hardware
---

### Post by mhom on 2013-06-30
My laptop (Samsung QX 410) ha[SIZE=2]s[/SIZE] an NVIDIA 310M mobile GPU and an Intel Ironlake Mobile integrated GPU. Ubuntu only recognizes the Intel GPU when I type ```
[FONT=Ubuntu Mono]lspci| grep VGA[/FONT]
```[FONT=Ubuntu Mono] into the console. The add[SIZE=2]i[/SIZE]tional Drivers tab is completely empty as well. I'm running the 64 bit version of 13.04 [/FONT]

---

### Post by Bashing-om on 2013-06-30
mhom; Hi Welcome to the forum.

What you have there is hybrid graphics.
Nvidia does not offer support and consequently ubuntu does not cope well with it.
There is the option to disable one of the graphics hardware in bios OR remove the Nvidia card ...Seems like I recall the Nvidia is the high end graphics and that may not be a good thing to do at all, and running on the Intel chips will not provide a good experience, if that is the low end. //

There is another option... the BumbleBee project. BumbleBee can control your graphics ... takes a bit of learning .. I have heard good report and many have had success ... I do not have any direct experience with BB so others can advise better. There are Lots of threads on this forum in respect to BB and tons of info by Google search to aid you in your decision making.

[INDENT][INDENT]no help, but a nudge in the right direction[/INDENT][/INDENT]

---

### Post by mhom on 2013-06-30
Thank you for the advice. I'll look into BumbleBee.

---

### Post by hansdown on 2013-06-30
Hi, mhom.

Please see this thread.

[http://ubuntuforums.org/showthread.php?t=2158852](http://ubuntuforums.org/showthread.php?t=2158852)

---

