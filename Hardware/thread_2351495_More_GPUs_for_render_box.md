---
title: "More GPUs for render box"
date: 2017-02-03
forum: Hardware
---

### Post by Paraplegic Racehorse on 2017-02-03
My render box is using my integrated graphics for display (not ideal but sufficient) and four GPU cards for the heavy math of rendering. I want to add more GPUs. I see USB PCIe powered risers available but I don't have spare PCIe slots to plug the x1 card into. Can I use these direct through my USB 3 ports or is there some goofy protocol reason that won't work?

---

### Post by Bucky Ball on 2017-02-04
Sheesh. What are you rendering with 4 GPUs??? I have one GTX 970 in a PCIe slot and it renders 1080p at a hum.  

Can you give further specific details of your setup? Where are these four cards plugged into the machine?

---

### Post by MartyBuntu on 2017-02-04
Just to be sure, we're not talking about a miner here, right?

---

### Post by The Cog on 2017-02-04
> **Bucky Ball said:**
> Sheesh. What are you rendering with 4 GPUs??? I have one GTX 970 in a PCIe slot and it renders 1080p at a hum.  

Ha! My son is doing "Interactive media" at college. He only has 2 GPUs but both top end. His homework can take days to render a 30 second clip. I think it's all 4k or 8k, and each pixel has a list of the separate contributions from each light source, motion blur and maybe other things. This means the lighting brightness and colours can be adjusted by the producers on the fly post-render for best artistic effect, without needing to send the scene back to the render farm for each adjustment. If I understood him right.

I know he has used 20 beefy AWS servers in a farm before now to do his and his friends homework. But since then Amazon has launched EC2 instances with multiple GPUs, which I don't think he's needed yet. 

I don't know about CUDA over usb3, but I found this article: [https://aws.amazon.com/blogs/aws/new-p2-instance-type-for-amazon-ec2-up-to-16-gpus/](https://aws.amazon.com/blogs/aws/new-p2-instance-type-for-amazon-ec2-up-to-16-gpus/)

---

### Post by Bucky Ball on 2017-02-04
> **The Cog said:**
> Ha! My son is doing "Interactive media" at college. He only has 2 GPUs but both top end. His homework can take days to render a 30 second clip. I think it's all 4k or 8k, and each pixel has a list of the separate contributions from each light source, motion blur and maybe other things.

Now that I compute. I don't do animations myself. Strictly camera shot vid with no effects, apart from a fade in and out, synced with separate audio and rendered out so nothing like those resource requirements. ;)

Wonder if OP is doing something similar to your son? Sounds like that may be the case ...

---

### Post by Paraplegic Racehorse on 2017-02-04
Pretty much, yeah. Blender can be my friend at times; lots of power but painful learning curve. It can also be my enemy, producing math my computer can't keep up with. I'm waiting on one of the riser cards, now. I'll plug in an old GPU to see if it's recognized. I imagine it won't be because the kernel won't recognize it if it isn't on the PCI bus (?).

I'm just wondering if anybody's written bridge code to support this.

There was some talk in the AMD dev forums about supporting this directly on the card complete with an built-in USB3.1 port. Nothing new on that since July or August, though. I suspect the thunderbolt external cases available have more-or-less killed that idea.

And, @MartyBuntu, yes, I "mine" when it isn't rendering, if you consider BOINC to be mining. I've got all this math coprocessing power. I may as well help further scientific research when it would otherwise be sitting idle. My cryptocurrency mining is done on a small bank of CHIP single board computers. They can't crunch very fast, but it's an interesting hobby and keeps me from polluting my work machine with all that garbage.

---

### Post by Paraplegic Racehorse on 2017-02-04
Heh. Also, I found these [PCIe 3x8 3 slot riser cards on Amazon.com]("https://www.amazon.com/gp/product/B00PDCZ4C4/ref=ox_sc_sfl_title_1?ie=UTF8&psc=1&smid=A2P5I4NW0QQAX1"). If this USB thing doesn't work, maybe I can further Frankenstein the computer with them.

---

### Post by Paraplegic Racehorse on 2017-02-08
Solved ! [maybe. haven't tested]

I found this [GPU-oriented PCIe Expansion Cluster]("http://amfeltec.com/products/gpu-oriented-cluster/") allowing up to 16 GPUs per each PCIe slot in the motherboard.

---

