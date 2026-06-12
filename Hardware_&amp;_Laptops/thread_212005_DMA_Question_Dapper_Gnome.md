---
title: "DMA Question Dapper Gnome"
date: 2006-07-09
forum: Hardware &amp; Laptops
---

### Post by indytim on 2006-07-09
I've just taken a look at my hdparm.conf and see that dma is not set on.  I've got 2 opticals installed on the box.  Question is, if I uncomment the following line, will this activate dma on both optical drives?

> #/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

Thanks,

IndyTim

---

