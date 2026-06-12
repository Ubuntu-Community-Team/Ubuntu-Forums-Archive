---
title: "ati x1950 pro drivers"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by RkyRaccoon55 on 2007-02-22
I have been to many different forums looking for answers, I have been to the Ubuntu Wiki looking for answers, and I have been to the #ubuntu irc channel and I have had to re-install ubuntu after each install attempt.  All I want to do is install my graphics driver for my ATI radeon x1950 pro on Ubuntu edgy 32-bit.  I have tried in vain several times and each time tried something different.  After each install attempt ubuntu will not launch so I needed to re-install it again.  Please help me.  Im getting frustrated to the point of giving up on Ubuntu.  I have basically no knowledge of Linux so you're going to have to walk me through any explanation.

---

### Post by fresch1 on 2007-02-22
> **RkyRaccoon55 said:**
> I have been to many different forums looking for answers, I have been to the Ubuntu Wiki looking for answers, and I have been to the #ubuntu irc channel and I have had to re-install ubuntu after each install attempt.  All I want to do is install my graphics driver for my ATI radeon x1950 pro on Ubuntu edgy 32-bit.  I have tried in vain several times and each time tried something different.  After each install attempt ubuntu will not launch so I needed to re-install it again.  Please help me.  Im getting frustrated to the point of giving up on Ubuntu.  I have basically no knowledge of Linux so you're going to have to walk me through any explanation.

Im having the EXACT same problem!

Please someone help!

---

### Post by Sewje on 2007-05-28
Try adding

VideoRam     32384

in the 

Section "Device"


This worked for me and i now have direct rendering on my x1950pro, but still cant get xgl to work properly, lots of major screen corruption when i try load gnome on top of xgl.

The VideoRam i put in is just an example you might want to specify more depending on your graphics card. I havent noticed any difference with 16meg -256meg

---

