---
title: "HP DV6 3020EP ATi 5470M Hybrid Graphics"
date: 2012-09-09
forum: Hardware
---

### Post by wilson99 on 2012-09-09
Hello!

I've installed Ubuntu 12.10 Beta 1.
A great OS, however with many bugs!

Well, I've never could get my ATi working properly. I've used Ubuntu 12.04 LTS, and had the exact same problem.

I've followed many tutorials and guides, none of them work for me!
CCC is not yet installed, in previous versions of Ubuntu I got a black screen saying that I need to reconfigure my graphics card and it run in low graphics mode!

I gived up at that time. And installed W7, but I don't like W7! (the 8 is just a piece of...)
I really want Ubuntu working properly!


Can anyone, for God sake, help me?

Right now, I have Full acceleration etc, with Intel i3 Graphics card (GMA HD, I think!)

Thank you! And sorry for the poor English, I'm from Portugal! ):P

Very simple!

First DO NOT INSTALL FGLRX!
Second use VGA_Switcheroo

[TUTORIAL] [http://linux-hybrid-graphics.blogspot.pt/2010/02/howto-install-vgaswitcheroo-for-linux.html](http://linux-hybrid-graphics.blogspot.pt/2010/02/howto-install-vgaswitcheroo-for-linux.html)

It won't work. It seems that doesn't "switch" and IGP stays always on! And DIS won't start!

But there's a fix!
HERE!
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

After running "echo ON > /sys/kernel/debug/vgaswitcheroo/switch" without quotes (use "sudo -i" for root, or it will say you don't have permission)

After that, run "cat /sys/kernel/debug/vgaswitcheroo/switch" (Forget all the other commands, they won't work!)

It will appear like this

"0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Pwr:0000:01:00.0
2:DIS-Audio: :Pwr:0000:01:00.1"

the "+" means Intel Ironlake is still "ON"!

So, the only way I found a "solution to this problem, was using a program from a brazillian! :D (Thank you!)

[http://www.youtube.com/watch?v=zIgVwUiiJ6A](http://www.youtube.com/watch?v=zIgVwUiiJ6A) VIDEO
[http://bgois.blogspot.com.br/p/software.html](http://bgois.blogspot.com.br/p/software.html) BLOG (VGA Switch 0.7)

Choose discrete and voilá! Solução encontrada!

(It will restart your current session, after that, go to details and it should show "Graphics: Gallium 0.4 on AMD CEDAR"

Sorry for all the gramatical erros, etc!

I hope I can help someone!

Thank you!

---

