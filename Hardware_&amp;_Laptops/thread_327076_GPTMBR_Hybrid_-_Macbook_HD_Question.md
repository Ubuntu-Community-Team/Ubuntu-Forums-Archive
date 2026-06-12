---
title: "GPT/MBR Hybrid - Macbook HD Question"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by pertheusual on 2006-12-28
I was hoping someone would answer a question about Macbook partitions for me. I was hoping to set up more that 3 partitions, but everywhere I've looked makes is sound like 3 is the max.

If I'm wrong, just say so.

I'm hoping to do a triple boot linux, windows and OSX. And then set up a Data partition too. Has anyone done that?

If the limit is 3, I figured that was because the hybrid has to be primary partitions only, and there is one over the GPT data and 3 covering the GPT partitions themselves.

The other thing that comes to mind would be manually moving the protective partition from over the GPT data sectors.

It seems like it would be possible to tell GPT to make 4 partitions, and then manually point 4 MBR primary partitions toward the correct sectors in GPT. Wouldn't both MBR and GPT see 4 partitions then? It would leave the GPT data marked as free space to anything that can't read GPT, but none the less.

Any comments appreciated, my new macbook arrives in a few days.

-Per

---

### Post by noobaholic on 2007-01-05
That sounds fun. I believe the limit of "3" partitions is because a standard MBR is restricted to 4 partitions, but here the first partition is used to hold the GPT. The GPT itself can hold a very large number of partitions. Fortunately, IBM extended the MBR such that it can have up to 8. I don't know much about how the extended MBR works and I'm also a bit unclear as to how Windows deals with the MBR... I think it may be a bit finicky. But I think what you want to do should be possible, if perhaps tricky. The Wikipedia articles on MBR and GPT are pretty descriptive. Let me know if you have further ideas on how to go about this and if you have any success.

---

