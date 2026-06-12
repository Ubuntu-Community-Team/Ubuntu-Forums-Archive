---
title: "Need a motherboard with lots of sata connectors"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by tuckie on 2007-04-05
I'm working on a storage server, and was initially thinking about purchasing a raid card, but I realized that if I spend a bit more, I can just purchase a motherboard with more sata connectors and not have to worry about spending 200+ on a pci-express controller, and just go with software linux raid. So, the requirements are: greater than or equal to 7 sata connectors, onboard gigabit lan, and works well with ubuntu. I've heard problems about some raid chips that motherboards use and not liking linux, and I would like to avoid any headaches if possible. And, of course, a cheaper board would be nicer than an expensive ($200+) board.  It doesn't matter if it is amd or intel, I just want all of the sata ports to work.

EDIT: If you guys have any other suggestions as to what I should do for starting off with 5, 500GB sata drives in a RAID 5, let me know.  It will be used to backup documents, and store dvd rips, and maybe become my new mythtv backend (at the very least extra storage for my mythtv box)

---

### Post by tuckie on 2007-04-06
well i was this close to ordering [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121053") board, until I found out that the lan chipset didn't support jumbo frames :(  Any other suggestions?

---

### Post by tuckie on 2007-04-07
Anyone?

---

### Post by bb002 on 2007-04-18
Jumbo frames? I'll look that up but could you still explain that one to me?


12 sata ($347): [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131146](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131146)
08 sata ($130): [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131013](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131013)
06 sata ($100): [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131022](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131022)

their were some cheaper MB with 6 and 8 sata connectors but none were more than $30 and that was all from mail in rebates.

I have a Asus MB with a nividia chipset right now (k8n??) and i think the chipset does software raid....

I enable the onboard RAID, then set my drives up in raid 0. After booting my fiesty install cd the drives are still seen seperately they even work independently....I could be doing something wrong or the RAID provided with the nividia chipset requires some OS software >_< Why provide a RAID option if I need OS software to drive the dang thing!? Pointless if you ask me.

I've worked with SCSI before and the individual drives vanish and are replaced with a drive who''s size matches the proper RAID configuration.

---

