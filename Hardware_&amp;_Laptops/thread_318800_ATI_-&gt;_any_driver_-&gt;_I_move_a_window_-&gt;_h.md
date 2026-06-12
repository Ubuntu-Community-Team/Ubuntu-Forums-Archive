---
title: "ATI -&gt; any driver -&gt; I move a window -&gt; high cpu utilization"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by gribelu on 2006-12-14
So..
I'm using Ubuntu 6.10 Edgy with the latest kernel update (i think it was out a few days ago).
Also, i'm using KDE (kde-core) because on my system gnome seems to be using much more memory, and especialy swap, compared to kde with the same apps.. native or not.

Graphics card: Radeon 9800 Pro
CPU: Sempron64 3000+
I tried the following drivers: ati, radeon, fglrx 8.31.5 and fglrx 8.32.5

If i grab a window and start moving it around the desktop (or with another window in the background) the CPU utilization varies from 20 to 70% depending on the size/content of the window and the background.
I also tried this under Windows and it only varies between 5 and 20%. Mostly 5 :)

So i don't think 2D acceleration is very good considering the cpu utilization..

What i ask of you is to tell me if this also happends to you... and if it would be a smart decision to move to an Nvidia GPU.

I only recently moved to Linux... I don't use 3D under Linux.. only 2D and overlay (movies)... Games run under windows since linux games are quite rare. So i don't care about GL performance. Just tell me how to get the 2D part right...

Thank You!

---

### Post by markeaton on 2006-12-15
I'm not sure but this sounds like a problem I had. In the end it was actually unrelated to the video card. I fixed it by doing

echo 1 > /sys/module/processor/parameters/max_cstate

If that works for you too setup an init.d script that runs on bootup.

---

### Post by gribelu on 2006-12-16
that didn't seem to work. but i looked it up and it looks like a good tweak anyway.. so thanks :D

Oh.. i tested some more.. 2D performance with the X.org/ATI driver is much better than FGLRX
But it still doesn't compare to Windows.

I think i'll get an nvidia card.. do you think that would be a good idea?

---

### Post by drstrangenorm on 2007-01-15
> **gribelu said:**
> that didn't seem to work. but i looked it up and it looks like a good tweak anyway.. so thanks :D

Oh.. i tested some more.. 2D performance with the X.org/ATI driver is much better than FGLRX
But it still doesn't compare to Windows.

I think i'll get an nvidia card.. do you think that would be a good idea?


Have you found a fix for this problem yet?  I am having a very similar one.

---

