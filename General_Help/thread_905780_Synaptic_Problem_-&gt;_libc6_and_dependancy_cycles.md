---
title: "Synaptic Problem -&gt; libc6 and dependancy cycles"
date: 2008-08-30
forum: General Help
---

### Post by kiisu on 2008-08-30
I was working on installing gstreamer plugins in order to get songbird to play my music.

anyway, just when i had it figured out i got this message in synaptic:

> Couldn't configure pre-depend libc6 for findutils, probably a dependency cycle

This now seems to come up when I try doing installing or removing anything, either in synaptic or by commandline.

Anyone encountered this?

---

### Post by kiisu on 2008-08-30
My Bad, it was a conflict (i think) between two repositories, one of which I had just added.

Deleting it fixed, and audio in songbird is now working!!
(if it helps anyone, going into synaptic and installing absolutely everything related to gstreamer seemed to do the trick)

---

