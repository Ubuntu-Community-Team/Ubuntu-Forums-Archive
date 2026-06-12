---
title: "Cannot get appearance settings to &quot;stick&quot;"
date: 2008-08-25
forum: General Help
---

### Post by seriousproblem on 2008-08-25
Hey there, I'm new to Ubuntu, and Linux for the most part (aside from a recovery drive with damn small linux on it), and I just got my NVIDIA card working. It works great, the driver is installed, etc, etc, etc. and now I want to use compiz and the infamous "cube". So, I set my settings to either "extra" or "custom" (either, the result is the same), and I set up the cube to be working, doing everything [this]("http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion") tells me to do.

Now, I don't get the cube, and I get a very slight change, if any, in graphics. None of the things I set up work. And when I close the window that says "none", "normal", "extra", and "custom" and open it again, it's back to NONE!

what's up with that, and how do I fix it? by the way, it's not the driver or card, because it's a gforce 8800GT and it plays just about everything on windoze but crysis, and the driver checks out and so does compiz on compiz-check.

thanks in advance for your help!:)

---

### Post by Vadi on 2008-08-25
Actually for the latest version of Ubuntu, you should follow the [updated guide]("http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074").

But anyway, first things first, lets see why compiz is disbehaving... go to Applications - Accessories - Terminal, and paste (ctrl+shift+v, or right-click and paste) this command:

> compiz --replace

And then press enter. You'll get some flickering and the look of Ubuntu might change sligtly after that, that's fine. Copy and paste the text it gives here.

---

