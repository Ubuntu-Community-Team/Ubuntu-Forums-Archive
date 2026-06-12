---
title: "Same Video Card, different symtopms"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by osxjamie on 2005-05-02
Ok so I just bought a new computer after my mac went south, and had to buy a PC for $$$ reasons. I knew I hate windows so installed umpteen different distros of linux before I found unbuntu which to this point I love. There's one problem: I can't seem to configure the refresh rate of my monitor. It is at 85 hz and I think that is too high because my monitor is squealing, not all the time but about half the time. It's a real high pitched noise that drives everyone in the house insane and I know it is not good for the monitor either. I have done massive amount of research online and tried some reconfigure command in the terminal, tried manually altering the xorg.conf file. My monitor specs say it can handle 30-50 and 50-160 but at 85hz i'm having this problem. The odd things is it seems to mostly happen in gnome and not kde. One final thing, I do not belive it is the monitor because on the log in screen sometimes I will move the mouse and the image will actually jump half off the screen, i only have to move the mouse to that edge and the screen will recenter again, but with distortion at the top. Please someone help, it took me forever to find a distro i liked and this seems to be an ubuntu only problem. Maybe of interest I do have the Intel Extreme 845GV video card with shared memory, apparently causes alot of problems, but only caused me problems in Unbuntu.

---

### Post by alastair on 2005-05-02
You could try generating a "modeline" for your monitor using "gtf.c" :

[http://gtf.sourceforge.net/](http://gtf.sourceforge.net/)

You'll have to compile, and then run to generate an "xorg.conf" modeline to use.

---

