---
title: "Suspend Issue on Sony Vaio Laptop"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by gwilliam on 2007-02-27
Okay, I'v ebeen searching the forums for days, fixing my desktop, beryl, etc. I am finally exhausted, I just can't find any specifics relating to my problem, partially because it only happens sometimes, and I can't for the LIFE of me figure out what is wrong.

I'm not sure if this started happening before or after I tried to improve the hibernate capabilities of my laptop (doesn't work under winxp because i have 2 gb of ram, but I also have a 2gb swap partition, so i thought ubuntu might be willing to try... i seem to have somehow excluded the hibernate option from the Quit... menu. I could swear it was there a few days ago).

Anyway, I'll suspend to ram, i think, and it'll go down fine. Then, when I start it up again, I get the same little artifacts as usual, but instead of asking for my password, it just appears to try and reload the pre-suspend state over and over again. I thought this was happening because my swap-partition was corrupt, and so I fixed it and changed /etc/fstab to reference the partition and not the UUID, and the problem went away. Several hours later, it is back, even though the swap-file is loading automatically at boot and everything.

I'm sorry if this is obvious to anyone else, I tried to figure it out on my own, but I just need a bit of handholding on this. If you need any specifics, let me know... I'm not sure what I can offer, though...

Thanks in advance,
David

---

