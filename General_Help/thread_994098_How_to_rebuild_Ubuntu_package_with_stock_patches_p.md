---
title: "How to rebuild Ubuntu package with stock patches plus extra changes?"
date: 2008-11-26
forum: General Help
---

### Post by Jasman on 2008-11-26
Gee, I couldn't think of how to title this question, and I've searched up and down for an answer. Somehow, I figured out how to do this once before, but now I've forgotten.

If I want to modify a newer version of an Ubuntu package (in this case, the synaptics touchpad driver) and I have a patch for an older version of that package, the only way I know of to apply the patch is by hand (in this case, adding some lines to synaptics.c). But if I use the standard method to download the source and then dpkg-buildpackage, I get an error because synaptics.c doesn't look as it should. The problem, if I remember, is that the Ubuntu patches are applied in an order, defined in a file called "series," and my modification is screwing up the application of one or more of those patches during the rebuild process. Is there a way around this? If I knew how to modify the patch file for the latest version of the driver package, and then edited the "series" file to include the desired extra patch last, I'm guessing that would work. But I have no idea how to do that, particularly since about half of the patches included with the source also modify synaptics.c, meaning that by the time it got around to the final patch, I have no idea where it would need to be inserted (the correct lines).

Anyway, I did this once already on Intrepid, so I know there's a way. Can anyone help me out? Thanks.

---

### Post by Jasman on 2008-11-29
Forget this post and thread. I was making the mistake (?) of following instructions that extract the source using "dpkg-source -x ...dsc" before modifying the source file (synaptics.c). Just using apt-get source after installing build-essential, then modifying synaptics.c by hand, and finally doing dpkg-buildpackage worked, although I didn't use fakeroot anywhere. I also don't know if any of the 7 patches included with the source were applied. Don't know if that's a problem, but the rebuilt deb once again solved my problem (horrible tapping functionality).

---

