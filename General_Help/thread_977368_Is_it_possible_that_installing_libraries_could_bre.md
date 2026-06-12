---
title: "Is it possible that installing libraries could break graphics?"
date: 2008-11-10
forum: General Help
---

### Post by mattgaunt on 2008-11-10
Hey everyone

I've managed to re-create a problem I'm having on intrepid ibex on my MacBook.

Basically when I first install intrepid compiz fusion works out of the box, no need to install anything. I have disabled this to then run OGRE and to do this I have had to install various libraries.

However after a restart, OGRE doesn't work, then when trying to start compiz, this fails to work.

The one library I'm slightly concerned about is nvidia-173-dev - does anyone have any knowledge of this? or any ideas

Gaunt

---

### Post by sdennie on 2008-11-10
Installing libraries can break OpenGL, yes.  This is usually only the case if you've manually installed the nvidia drivers though (so, if you've downloaded the drivers directly from the nvidia website).  If that happens to be your case, the only real recourse is to re-install the drivers.  If that's not the case, I'm not sure what the problem might be.

---

### Post by mattgaunt on 2008-11-10
Well that is good news, no I installed the nvidia-173-dev file from the repo.

The main issue is that I require nvidia-173-dev to get the OGRE demo's running, but this seems to stop openGL from working.

So Im not sure what to do and I dont think this was a problem with hardy heron so I might  revert back.

Thanks for your help

Gaunt

---

