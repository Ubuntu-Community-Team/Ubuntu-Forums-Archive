---
title: "Overclocking old Hardware"
date: 2014-07-03
forum: Hardware
---

### Post by AmbiguousOutlier on 2014-07-03
I'm new to overclocking and have an old machine which I thought I would try to use as a steam gaming machine to see how viable gaming in linux is before I spend any money.

I got Civilization V, which can handle the default graphics, although calculations and loading are very slow. So far I managed to OC my 2.5Ghz to 2.875Ghz which runs fairly stable with graphics on average and is still a little slow but very playable.

The hardware I have is a [GA-MA780G-UD3H]("http://www.gigabyte.com/products/product-page.aspx?pid=3004#ov") mobo, which has Gigabyte's MB Intelligent Tweaker in the BIOS. With these options (from google not my system);

[IMG]http://www.legitreviews.com/images/reviews/676/gigabyte_bios_3.jpg[/IMG]
[IMG]http://www.3dnews.ru/_imgdata/img/2008/03/21/images/bios_memory.jpg[/IMG]

I'm using [AMD Athlon X2]("http://www.cpu-world.com/CPUs/K8/AMD-Athlon%20X2%204850e%20-%20ADH4850IAA5DO%20%28ADH4850DOBOX%29.html") which is the energy efficient one, running 2 cores at 2.5Ghz and 45w TDP. Apprarently it can operate up to 78c, it's currently hanging around the 30c to 40c. 

I've got this [heatsink]("http://www.quietpc.com/ninja-mini") which should be sufficient for any overclocking.

I've also got a GT630 with 1GB DDR3 which requires a 300w PSU. I've also got 4GB of RAM in there, and the PSU is a fairly efficient 400w.

The steps I've taken so far to OC are;

I've dropped my memory clock down to 400. I've kept my CPU clock ratio to Auto, it goes from x5 to x12.5 default I believe is 12.5. I've then managed to increase my CPU freq to 230. 

When I try to increase the frequency anymore it becomes unstable and wont boot if I up vcore by one step. 

Any tips on trying to get a bit more out of my system?

---

### Post by Yellow Pasque on 2014-07-03
Remember to drop the HyperTransport to 4x (or 3x if you want base clock > 250)
[http://www.hardwaresecrets.com/printpage/Athlon-64-Overclocking/102](http://www.hardwaresecrets.com/printpage/Athlon-64-Overclocking/102)

---

### Post by tgalati4 on 2014-07-03
Memory timing tweaks will give 5 to 10% increase in memory transfer speed from my experience with that vintage hardware.  CPU speed increase is limited by voltage and current supplied by the motherboard and how much power the CPU can tolerate.  So monitoring the CPU die temperature is important.  You will need a much larger heat sink and fan.  Simply overclocking with the stock configuration means your system's life will be greatly shortened.

You can really only overclock until you reach instability and then you will need to back off some, otherwise your machine will constantly lock up.  The instability point may or may not be at the maximum tolerated die temperature.  Understand that overclocking can cause degradation of the motherboard under the processor.  So the processor may survive a 5GHz overclock, but he motherboard underneath it often can't take the heat.

---

### Post by AmbiguousOutlier on 2014-07-07
> **Temüjin said:**
> Remember to drop the HyperTransport to 4x (or 3x if you want base clock > 250)
[http://www.hardwaresecrets.com/printpage/Athlon-64-Overclocking/102](http://www.hardwaresecrets.com/printpage/Athlon-64-Overclocking/102)

Excellent guide, thanks that helped a lot.

I've now got my 2500Mhz up to 3025Mhz, and it idles around 35c, under [stress]("http://manpages.ubuntu.com/manpages/lucid/man1/stress.1.html") it hangs around 50c and it doesn't go above 60c. 

I've got 0.025v increments on my mobo so I think I could geta little more out of it if I'm willing to push the cpu to 65c. Then it's time to overclock the GPU. 

Civ5 plays brilliantly at about 80% of max graphics, slow load time still, so could probably do with a SSD. Can I just install the game on the SSD and still get better load times or does the whole OS need to be on the SSD to see proper increase in loading times?

---

