---
title: "is my mobo bios chip overheating?"
date: 2009-12-11
forum: Hardware
---

### Post by pha3r0 on 2009-12-11
hey extremely off-topic here guys but i find this forum more active and knowledgeable then 99% of the rest of the internet but thats another post.

my problem is this. my system had a fan go out and i woke up toa crashed computer. restarted it not knowing the fan was out and shut it down once i caught it. i have since replaced the fan and now its loading fine at first but shortly (1-5 minutes) it will hang everytime. whatever is happening will keep going i.e. text cursor blinking, memtest86 progress icon keeps flashing etc. im thinking it is the onboard nvidia bios chipset anyone second that or have another idea?

i am trying to figure out if its new mobo time or exactly what all i need to order.

---

### Post by paulisdead on 2009-12-11
Have you checked what the temps actually are?  If you've got lm_sensors setup, you can just check with that.  Otherwise, you could just sit in the bios for a few minutes looking at the temps.  So long as you've discharged the static from your body, you can touch the heatsink to make sure it's not overheating.

I've seen a few cases with nforce motherboards, where the fan dies, and the chipset burns up, and it stops working.  Those things definitely need active cooling.  If you're up to it, you could take the heatsink off the northbridge chip and inspect it for damage.  Look for signs of anything burnt, or that may have bubbled.  Use your nose too, as stupid as it sounds.  If something smells burnt, that's a good indicator you've burned something up, and may help you figure out what it was.  If you've got signs of burning or see that the chip has bubbled up in some spots, there's not much else you can do but RMA it.

If all else fails, it never hurts to unhook everything from the motherboard, and put it back together again, making sure everything fits snugly when you plug it back in.  Also, you can try to run it with the minimal amount of things hooked up to it, ie just ram, psu, cpu, and video card.

Which fan was it that actually died?  If it's the one that sat over the chipset, it very well could be hosed.

---

### Post by pricetech on 2009-12-11
The symptoms sound more like Processor overheating to me, but that's just an educated guess based upon what you said.

Again, which fan stopped working ??

---

