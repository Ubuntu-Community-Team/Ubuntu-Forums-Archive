---
title: "Technotrend TT-budget C-1501 DVB-C PCI Tuner"
date: 2008-05-13
forum: Hardware
---

### Post by k33l0r on 2008-05-13
Hi,


Does anybody have any info or experience on getting a **Technotrend TT-budget C-1501** tuner to work in Ubuntu, or indeed any Linux distro?

The best specs I can find for it in English are from an [eBay listing]("http://cgi.ebay.co.uk/RARE-Technotrend-DVB-C-1501-card-inc-remote-%27B%27_W0QQitemZ260239020777QQcmdZViewItem?IMSfp=TL0805111023a6750") and this [PDF brochure]("http://www.technotrend.tv/product_specs_pdf/TechSpec%20TT-budget%20C-1501.pdf") (also attached).


Thanks,
Matt

---

### Post by trojanfoe on 2008-05-20
I am in the same boat, using the latest v4l-dvb driver tree compiled from source.  There was some mention of experimentation on the linux-dvb mailing list, and some progress has been made I think, but nothing official has been placed in the source tree and I cannot find any patches, official or otherwise.

I have seen some opinion that the new 1501 model is simply a hardware optimisation of the 1500, but I don't think that's true, else it would be working by now, so I guess we'll just have to wait.

Please let me know if you find anything to get it working.

Cheers,
Andy

---

### Post by DutchLoki on 2008-06-05
Yah same problem here. The 1501 seems not supported yet but it looks like there is a workaround using a dvb-t driver. Read it, solution does not look so good.

i'm afraid we have to practice our patience ;)

---

### Post by DutchLoki on 2008-06-09
> **DutchLoki said:**
> Yah same problem here. The 1501 seems not supported yet but it looks like there is a workaround using a dvb-t driver. Read it, solution does not look so good.

i'm afraid we have to practice our patience ;)

A new version will be added to the DVB tree: 
[http://marc.info/?l=linux-dvb&w=2&r=1&s=c-1501&q=b](http://marc.info/?l=linux-dvb&w=2&r=1&s=c-1501&q=b)

---

### Post by DutchLoki on 2008-06-12
see [http://marc.info/?l=linux-dvb&w=2&r=1&s=c-1501&q=b](http://marc.info/?l=linux-dvb&w=2&r=1&s=c-1501&q=b) for more info.

You can help testing it and submit any problems to the mailinglist.

---

