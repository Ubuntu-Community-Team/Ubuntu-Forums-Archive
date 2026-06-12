---
title: "Why does playing a DVD cause my CPU usage to jump to 100%?"
date: 2005-11-13
forum: General Help
---

### Post by magomago on 2005-11-13
Hi, 

Whnever I try to play a DVD, the CPU usage skyrockets to 100%, and thus creates a very skippy, jerky movie.  

Any ideas?  I do have DMA turned on my drives.....
/dev/cdrom {
       dma = on
}

/dev/cdrom1 {
       dma = on
}
/dev/cdrw {
       dma = on
}


I actually only have 2 drives but in my /dev directory it lists 3....so I just do all three and figure one is a copy of the other

Anyways...whenver I play the DVD with Totem it always skips...does anyone know how to fix this?

---

### Post by tomski on 2005-11-13
what processor and how much ram do you have?

---

### Post by dtfinch on 2005-11-13
It can run very slow if video acceleration isn't working. It has to scale the video in software, which is slow no matter how fast your machine is. A quick check would be to run glxinfo and see if "direct rendering" is available. On a system that didn't have working acceleration, where ubuntu was falling back to using the vesa video driver, I used an xine based player and configured it to use xshm for output and disabled scaling. That allowed it to play at full speed without skips, but not full screen.

---

### Post by magomago on 2005-11-13
Yes I have direct rendering, I have a 2200+ with 1 Gig of Ram and G4ti4800(I beleive that is an 8x ti4200).  Video Acceleration works perfectly, as I have played WOW many a time ;)

---

### Post by trigg on 2005-11-13
/dev/cdrom and /dev/cdrom1 might be symlinks,  try listing the actual device - /dev/hdc, /dev/hdd, etc. . . .  you should be able to tell by using ls -alF in the /dev directory.

---

### Post by dtfinch on 2005-11-13
So running "hdparm /dev/cdrom" confirms that it succeeded in enabling DMA?

---

### Post by poptones on 2005-11-14
*Video Acceleration works perfectly, as I have played WOW many a time*

Is there a WoW for linux NoW? 

Do you have installed accelerated linux drivers for your video card?

---

