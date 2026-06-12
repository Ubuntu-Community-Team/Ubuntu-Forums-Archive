---
title: "Does &quot;Side by Side&quot; Kubuntu Installation delete XP data?"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by runningeagle on 2009-06-04
Hello
 
I am back to trying to install linux. After a problem with my CD drive, I put Kubuntu 9.04 64-bit on a flash drive. I boot the live "cd" and click install. I select "Yes" to unmounting sda drive. 
 
Last time I tried to install (but didn't go through) I only had the "Use entire disk" option, which I didn't want because I want to keep my previous XP installation and dual-boot.
Now, I see this new "side by side" installation, that allows me to drag space for Kubuntu.
 
Because I have not seen this before, and cannot find a desription of it online,** will Kubuntu's "Side by Side" drag installation delete any XP data?** I assume it will not because the similar feature in Ubuntu won't, but I don't see any of the partitions in the graphic titled XP. XP is on sda1 (C : )
I see
 
I--------I----------------------------I------------I
sda1_____________ sda5_______ kubuntu dragger

---

### Post by .nedberg on 2009-06-04
No, it doesn't remove anything. But still, remember to backup everything before you install!

You could also try a Wubi install. That will be like installing a program under Windows, and it can be removed from Windows again if you don't like it. This is "safer", no need to backup anything. You will still have to select Kubuntu or Windows when you start your computer.

To use the Wubi install you need the Live CD or dl it from [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by runningeagle on 2009-06-04
Thanks!

---

### Post by .nedberg on 2009-06-04
No problem!

Post here at the forums if you get any more questions/problems!

---

