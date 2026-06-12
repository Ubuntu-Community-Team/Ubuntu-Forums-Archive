---
title: "Dual monitors thinks its quad monitors"
date: 2008-11-20
forum: General Help
---

### Post by shiznatix on 2008-11-20
I have been running dual monitors ever since 8.10 came out and have been loving it.

At first I tried using the ATI drivers but that kept crashing to the point that it was unusable so I went back to the open source ones, dual monitors rocking it the whole time.

Now I started to play counter strike so I needed to go back to the ATI drivers which have been working just fine. The problem is that now it thinks there are 4 monitors hooked up instead of just 2. I can keep moving my mouse to the right for forever like there should be another monitor there but there isn't. Also on the multiple-desktop thing it has a look like there are 4 desktops and if I move an app over to what would be the 3rd monitor you can see it move there.

So, how can I make it not be stupid and not think there are 4 monitors hooked up?

---

### Post by asmit21 on 2008-12-06
I am pretty sure it has something to do with your configuration in the **xorg.conf** file. But exactly how to fix this problem I am not sure, but that should give you somewhere to start looking.

~Aaron

---

### Post by easybake on 2008-12-06
Your best be would be to post your xorg.conf. It's located in etc/x11/xorg.conf

---

### Post by Cybie257 on 2009-01-19
I have the same exact problem. Not a big deal for most things, but I want to remote into home from work, which does OK, but takes forever for the screen to refresh compared to what it should because it's refreshing 5760 X 900 instead of 2880 X 900.

Strange thing is, is that I can't seem to get to the other/hidden 2880 visually. I, too, can also slide my mouse over to the imaginary edge, lol, but if I VNC into my Linux machine, then I can access all of it by sliding the bar over and doing so. Or, if I use auto scaling with UltraVMC Viewer, things are realllllly small. :) 

Anyone else have ideas? I looked in my xorg.confg and it's virtual desktop size is set at 2880 X 900, so I don't think it has to do with xorg.conf . :(

-Cybie :guitar:

---

