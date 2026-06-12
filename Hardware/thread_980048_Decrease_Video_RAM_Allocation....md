---
title: "Decrease Video RAM Allocation...?"
date: 2008-11-12
forum: Hardware
---

### Post by icanfly0307 on 2008-11-12
Hi,
      I have an old Sony Vaio Laptop that has an ANCIENT (and I mean ANCIENT) graphics card (Intel 82815). I've read on the Intel website that it can use up to 32 MB of RAM from the system RAM. 32 MB of RAM is a waste considering the fact that I have only 256 MB of total RAM. So... Is there anyway to decrease the amount of RAM that my graphics card uses? Even a few tens of MBs would really boost my performance...

Thanks.

PS. I am not using any type of graphical eye candy like Compiz. My graphics card is WAY to slow for    those

---

### Post by logos34 on 2008-11-12
you have to go into the Bios at startup to change it.  Look for video/graphics frame buffer setting...turn it down to 8 MB.

---

### Post by cariboo on 2008-11-12
You probably have to decrease the amount of ram that the video card uses in the BIOS. With my onboard graphics adapter, I have the vidoe ram set in bios to 32Mb, but Nvidia X server settings says it has 256Mb ram. Free -m says I have 1.9Gb usable of 2Gb.

Jim

---

### Post by icanfly0307 on 2008-11-12
Hey Guys,
         Thanks for your replies. Here's my issue. I don't have an option to set my video RAM in my BIOS. I read somewhere that there's a way to configure it in xorg.conf. Would it work if I added that section to my xorg.conf and set it to 8000 kb?

Thanks again...

---

### Post by logos34 on 2008-11-12
no, you have to set it in the Bios.  You have integrated graphics, so the memory is shared...you must be overlooking it.  What model Vaio? I can help you google the manual

---

### Post by icanfly0307 on 2008-11-12
My laptop's model is PCG FX370. Again it's very old (bought in 2001). I'm not sure if I can set the video RAM. I've looked pretty much everywhere in the BIOS but maybe I'm overlooking it... :confused:

---

### Post by logos34 on 2008-11-12
I just checked the manuals here:

[http://esupport.sony.com/US/perl/model-documents.pl?mdl=PCGFX370](http://esupport.sony.com/US/perl/model-documents.pl?mdl=PCGFX370)

both quick start and main manual.  Couldn't find any mention of it.  Strange.  So maybe you're right--you can't change the shared video memory.

---

### Post by icanfly0307 on 2008-11-13
Yeah, I couldn't find it either. I'll think of something else to boost my system performance. Thanks for your help, anyway... :)

---

