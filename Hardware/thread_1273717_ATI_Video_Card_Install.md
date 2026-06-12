---
title: "ATI Video Card Install"
date: 2009-09-23
forum: Hardware
---

### Post by kc5hwb on 2009-09-23
Hi,
I've been running 9.04 for some time now and what I want to do is upgrade the video card for various reasons.  My previous card was an onboard Nvidia card.  I have 2 new video cards that I could put in this box, and I want to know which one to go with, or if I just need to find something else.

The first card is ATI Radeon X300.  I read a few posts on this site and it appears that this card isn't supported anymore.  If this is truly the case, I will not use it.

The second card is a ATI Radeon x1950 Pro.  I have read various threads on this site about this card and I can't decide whether it is worth jacking with or not.

Right now, I just put the X300 card into my Ubuntu desktop, and it does boot into the xServer but the res is a bit off and when I run LSPCI I get several lines about the nVidia drivers that are still there.  How do I get rid of those?  And where can I get proper drivers for either of these cards?

---

### Post by ROY.G.BIV on 2009-09-23
Well, yes, you can get rid of the old drivers... but those ATI cards don't mix well with linux. The driver support is rather dodgy, I've been there so I know. if you still want to remove the Nvidia drivers: ```
 sudo rm /usr/src/nvidia-driver /usr/src/<driver-name.run> /etc/kernel/postinit.d/update-nvidia
```Be sure to replace the <driver-name> with the name of the driver, with no <>.

But again... I would suggest that you look at nvidia cards, as they are more more stable and functional. My 9600GT installed trouble free, once I figured out the proper commands.

---

### Post by kc5hwb on 2009-09-23
Someone at work told me that ATI cards worked better with Linux because ATI made Linux drivers for their cards.  I have never actually used ATI, all my cards have been Nvidia and those always take a little work to get installed and updated.  But once I had them, they always ran fine.

What I really need is a card that will play World of Warcraft and the Nvidia card I have now doesn't seem to like it, it constantly crashes and gets a very low frame rate when playing on this Ubuntu box.  Can anyone make a suggestion for something other than this onboard card?

---

### Post by ROY.G.BIV on 2009-09-24
Built in cards generally don't have enough power ot run games like that.

 Nvidia is the one that makes the drivers for their cards. ATI doesn't release hardware specs to open-source linux, leaving linux guys to revese engineer the hardware, which is why the drivers are so unreliable. You're welcome to try... but I crashed Ubuntu five different ways before giving up on the ATI drivers. I am dual-booting XP Pro, and I wanted a card that worked with both, so I switched to Nvidia.The nvidia even works better on windows than the ATI, and the ATI specs were nothing to snort at.

But... go for it, if you want to! I have learned more from messing with my ststem(and breajking it) than anything else. If you're going to do this, I highy recommend you make a copy of you're xorg.conf, in case of graphics failure. 

And as far as graphics cards... I don't do much with laptops... You should be looking foro ne based on your needs. Seeing as you're looking to play games like WoW, I'd say 1GB minimum of GDD3. But go for GDDR5 if you can find it.The more memory and speed, the higher frame rates you will get. 

Also, be sure your computer itself has al least two gigs of memory otherwise you'll still have lag. A dual-core or better cpu doesn't hurt either, but I'm assuming you have one.

---

