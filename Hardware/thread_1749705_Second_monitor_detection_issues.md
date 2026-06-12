---
title: "Second monitor detection issues?"
date: 2011-05-04
forum: Hardware
---

### Post by kai_wanders on 2011-05-04
There's a high chance this issue is just me being an idiot and missing something, but if anyone could point me in the right direction, that'd be great.

So, the problem is that while the nvidia x-server settings finds, and allows me to set up, my second monitor, nothing else can find it. I think. Basically, nvidia and my .xconf file show two monitors, but lshw and similar show only the first one?

I've searched all over, and while I've found plenty of people having problems with dual monitor displays. Right now, I'd be happy with whatever issues that chooses to throw at me, if only I could get my computer to acknowledge that there are two monitors.

So... any advice is better than nothing right now.

Thanks all.

---

### Post by Cerox Rex on 2011-05-05
Having same problems as you do, but got my setup working with nvidia tool. I'm running seperate desktops but i have to do so while running in gnome clasical with compiz deactivated ie ubuntu-classical (no effects) -session chosen at login screen. as compiz breaks dual monitor with my setup.

But you should be able to run twinview fine.

Simply put nvidia-tools lets you setup dual monitor, but nothing else as far as i know are able to see that you have more then one monitor connected.

---

### Post by kai_wanders on 2011-05-05
No dice on that one, I'm afraid - tried all three options I get at login, since that's a solution I've seen around for other issues. No luck with either Twinview or seperate x servers. In fact, seperate x servers screws up my whole display - I just get a cursor and a black screen until I go into the recovery console and replace my xconf file.

I'm starting to think it's an 11.04 issue, because when I re-installed 11.04 (before I figured out that it was the x display settings breaking my OS) the live boot disc display was twinned on both monitors just fine.

Kind of annoying, but I'm not really desperate to use both monitors, it just would have been useful, so I guess it's just live with it until compiz works with dual monitors, or something else figures itself out.

Thanks anyway, though.

---

### Post by souravc83 on 2012-03-04
It might help to try disper. 
[http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

---

