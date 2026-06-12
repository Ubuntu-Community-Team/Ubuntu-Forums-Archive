---
title: "8BG CF + swraid (mirror for system partition) =&gt; speedup?"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by butonic on 2007-08-18
I was looking at solid state disks when this idea popped into my mind:

Use a sizeable and fast compact flash card with a fast cardbus adapter to create a software raid / mirror for system files.

Delkin produces 8GB/CF-cards capable of 45MB/s with correcsonding 45MB/s cardbus adapters. The memory is quite pricy, though ... 299$ for the cf card + 59$ for the adapter. I was thinking of SanDisk Extreme IV 8GB as they are around 160$. However there seems to be no fast cardbus reader for them:
[http://www.robgalbraith.com/bins/multi_page.asp?cid=6007-8462]("http://www.robgalbraith.com/bins/multi_page.asp?cid=6007-8462")

So, first lets make some assumptions:
0. we'll leave out the cost and make this fun ;)
1. /boot, /home and /var reside on their own partitions (what else?)
2. / will be a mirror of the hardisk with 2/4/8GB flash
3. the flash will be fast ~40MB/sec 
4. well use the noatime mount option for / to keep the flash from running out of write cycles
5. there is no performance bottleneck hidden in any adapter

What kind of performance boost could be expected?
I would think that ~35MB (HD 5400rpm) + ~40MB (flash) should be noticable. Will the latency benefit too?

If you agree, my idea is not totally off ...

Now let's look at our assumptions again. Maybe the other extreme:
I'll buy the next best 8GB SDcard and use my laptops internal multi card reader slot. Might result in ~2-5MB/s. Still worth it?

Any other ideas? Maybe splitting the filesystem so more files can be read simultaneously via HD, CF-card, SD-card. Maybe use a ~40MB/s 8GB flash as the only root partition? The HD would only store logfiles, some var + run stuff and /home.

I know of 32 GB ExpressCards ... but my UMTS modem resides in that slot. Might be another option though (read ~20MB/s, write 11MB/s).

Any opinions? What about SD-cards as /home/<myuser>? Too slow?

What other fast non-volatile memory extensions do you know?

It somehow reminds me of that ReadyBoost thing ...

so long

butonic

---

