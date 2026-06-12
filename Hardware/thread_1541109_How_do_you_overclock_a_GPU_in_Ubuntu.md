---
title: "How do you overclock a GPU in Ubuntu"
date: 2010-07-28
forum: Hardware
---

### Post by Lyude on 2010-07-28
Hello, when I used to run windows I would have my graphics card overclocked using rivatuner, I looked on the Ubuntu software center and found rovclock, which does not work with my GPU apparently. Does anyone know a good program to overclock (and adjust fan speeds if possible)? My graphics card is a Sapphire ATi Radeon HD 4850, and I run 64 bit ubuntu 10.4.
EDIT: I apologize, I just realized I put this in the wrong board.

---

### Post by Qwantumz on 2010-07-28
I would suggest you to try overclocking your GPU from the BIOS, not the O/S. Simply enter the BIOS and check at the available settings (you would have to read a bit regarding your motherboard and video card capabilities though). This kind of overclocking would be definitaly more stable and would perform better than any 'software overclocking'.

---

### Post by Lyude on 2010-07-28
> **Qwantumz said:**
> I would suggest you to try overclocking your GPU from the BIOS, not the O/S. Simply enter the BIOS and check at the available settings (you would have to read a bit regarding your motherboard and video card capabilities though). This kind of overclocking would be definitaly more stable and would perform better than any 'software overclocking'.

My BIOS does not support overclocking my GPU sadly

---

### Post by Qwantumz on 2010-07-29
In that case you might want ot look at 
 
[http://www.overclock.net/linux-unix/591785-ati-video-ubuntu.html](http://www.overclock.net/linux-unix/591785-ati-video-ubuntu.html)
 
and 
 
[http://www.phoronix.com/scan.php?page=article&item=675&num=1](http://www.phoronix.com/scan.php?page=article&item=675&num=1)
 
Hope this Helps.

---

### Post by cascade9 on 2010-07-30
> **Qwantumz said:**
> I would suggest you to try overclocking your GPU from the BIOS, not the O/S. Simply enter the BIOS and check at the available settings (you would have to read a bit regarding your motherboard and video card capabilities though). This kind of overclocking would be definitaly more stable and would perform better than any 'software overclocking'.

I've never, ever, seen a video card that you can overclock from the BIOS.

@ Lyuide-  wrong board? Seems to be the best place to put this, where were you thinking suited better?

---

### Post by PresenceofMind on 2010-07-30
I think you have to use a special utility for overclocking GPUs. I typed 'overclock' into the software centre and a bunch of stuff came up there that you might want to have a look at.

---

### Post by j0eb0b on 2010-07-30
If Rivatuner is a Windows program and you have it on CD you might try and run it using Wine. Many games that run on Linux using Wine allow access to video adjustments.  I'd be curious to see if that extends to things like GPU clock speed or fan adjust.

---

### Post by cascade9 on 2010-07-31
> **j0eb0b said:**
> If Rivatuner is a Windows program and you have it on CD you might try and run it using Wine. Many games that run on Linux using Wine allow access to video adjustments.  I'd be curious to see if that extends to things like GPU clock speed or fan adjust.

Rivatuner is very nVidia based (though it does run on ATI 8500 or higher cards). 

If the OP had an nVidia card, nvclock is what to use with linux ;)

---

