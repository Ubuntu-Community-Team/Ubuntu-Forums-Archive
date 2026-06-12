---
title: "Compiz/Emerald dont work, composite extension not loading?"
date: 2008-07-15
forum: General Help
---

### Post by fizban9 on 2008-07-15
I've been struggling with Compiz, Xinerma and the Composite Extension. Now I'm not.  I'm not sure how my fix worked, but it did.  Here's the lowdown.

Compiz will NOT work with Xinerma BECAUSE Xinerma will NOT work with the Composite Extension (which in turn is needed by Compiz.)  To use Compiz you have to use Twinview.

The trick, if you dislike how twinview turns your two screens into one big desktop, is to make Twinview act like xinerma.  A post I found suggested the following, and I know it will sound really simple, but it worked for me.

You can do all of the following by running "sudo nvidia-settings" and poking around.

Turn off dual monitors and reboot. Switch your computer to Xinerma and reboot.  Switch it to Twinview and reboot.

Tada!  If your system acted like my system, you know have Twinview running with a Xinerma-esque dual desktop.

Why it only work it wou go in that order, I don't know.  Hope this helps some people out there.

---

