---
title: "Swap Question"
date: 2008-11-30
forum: General Help
---

### Post by stoneage on 2008-11-30
I do some 3D rendering, and if I render a very complex file some swap is enabled. If a significant amount of swap is used the system lags even when the render is finished.

Is there a way to clear swap without restarting ?
I use Blender - is it hogging the available memory?

---

### Post by drs305 on 2008-11-30
I can't verify that it will help but you can turn swap off and back on again with the following commands:
```

sudo swapoff -a
sudo swapon -a

```

---

### Post by binbash on 2008-11-30
1- You need more RAM
2- You can resize swap partition and make it bigger with gparted live cd.
3- I never try to empty the swap file but read at the end of this page (linux part) : [http://www.iusmentis.com/security/filewiping/wipeswap/](http://www.iusmentis.com/security/filewiping/wipeswap/)

---

### Post by The Cog on 2008-11-30
I would have thought that the system only lags for a while, until the things that have been swapped out have been needed and reloaded once. I would be surprised if the lag was permanent.

The only way to flush the swap I could think of is to do this:
sudo swapoff -a
sudo swapon -a

---

### Post by stoneage on 2008-11-30
> **drs305 said:**
> I can't verify that it will help but you can turn swap off and back on again with the following commands:
```

sudo swapoff -a
sudo swapon -a

```
Thanks I'll try it.

> **binbash said:**
> 1- You need more RAM
2- You can resize swap partition and make it bigger with gparted live cd.
3- I never try to empty the swap file but read at the end of this page (linux part) : [http://www.iusmentis.com/security/filewiping/wipeswap/](http://www.iusmentis.com/security/filewiping/wipeswap/)
I know, I know. I have 2Gb but to add more I need to replace the motherboard and if I'm going to do that I may as well buy a new processor, so I'm kind of stuck with it for now. Swap is currently 5.7 Gb but it's not really the size so much as the fact it is enabled. Thanks for the link - I didn't know that.


> I would have thought that the system only lags for a while, until the things that have been swapped out have been needed and reloaded once. I would be surprised if the lag was permanent.

The only way to flush the swap I could think of is to do this:
sudo swapoff -a
sudo swapon -a

I thought so too. I'm wondering if Blender is failing to release memory once the render has finished. Making any changes to a file is painfully slow, and restarting is the only way I know to clear swap. (Restarting Blender or logging out helps too but it would be more convenient to be able to just carry on working).

Thanks, I wasn't expecting such a swift response.

---

### Post by stoneage on 2008-12-01
Hey. It works just fine except for one thing. The system can't reallocate the residual swap while Blender is open as it is still using nearly all the RAM. Other than that everything is fine.
Thanks again.

---

