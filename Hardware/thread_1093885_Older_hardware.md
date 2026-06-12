---
title: "Older hardware"
date: 2009-03-12
forum: Hardware
---

### Post by deamon_knight on 2009-03-12
Well, as a longtime PC user I've accumulated alot of cast off parts over the years. Looking at the junk-pile, I realized I have enough bits to throw together and make something. Don't laugh, its a P2 400mz, but with 512 RAM it runs. I have 8.10 installed and it works well enough, but I'm having some trouble getting all the hardware working. 

I have a nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) vidcard I'm trying to install drivers for.

I followed the instructions here
[http://ubuntuforums.org/showthread.php?t=971103](http://ubuntuforums.org/showthread.php?t=971103)

but no luck. I can still boot into 8.10 normally, however the progress bar stops, reports (among other things) nvidia 71.76.09 [fail]. so I don't think it is being loaded. Am I stuck, or is there some whay to get this to work?

Also, on this 10yr old board is another 10 yr old ISA FM Radio tuner, I was wondering if I could get this running too. However, I think I have forgotten the little I knew about ISA, and I don't know at all how it would be added in Ubuntu.

-Thanks in advance.

---

### Post by deamon_knight on 2009-03-15
Well, I gave up on the video card. I had another on lying around that is more modern so that works. I'd really like to know how to get this radio card to work. I believe it is the AMS Labs RadioTrack ISA controler. Some of the Googling leads me to believe that I have to load the Kernel Module: radio-aimslabs and then specify the memory address (0x20f). After that I'm trying to load Gnomeradio but it says there is no /dev/radio . I find there is a /dev/radio0 , but only root has access. RUnning gomeradio as root doesn't work, the program just sits and I have no Radio.

Any advice?

---

### Post by deamon_knight on 2009-03-15
Well, I'm gradually making progress. Running GnomeRadio as Root DOES work, however, its very slow the first time its run while is scans the channels. The first hurdle is how do I access /dev/radio0 as not root? should I chroot /dev/radio0 to something? It looks like it is part of group "video" but I'm not sure how to make my user account a part of that group.

---

