---
title: "Whether Ubuntu (mine is 5.10) enables DMA by default or not."
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by Dislimit on 2007-01-19
[code]
sudo hdparm -d /dev/sda
[\code]
displays nothing meaningful.

So I'm wondering Whether Ubuntu (mine is 5.10) enables DMA by default or not.
My laptop is IBM T43.

Can I just use 
[code]
sudo hdparm -X mdma2 -d1 /dev/sda
[\code]
To make sure DMA is enabled?

---

### Post by disabled_20220313 on 2007-01-19
By default it DMA is turned off.

You can turn it on, I can't remember how, but it was in the Breezy 5.10 Ubuntuguide.org page.

But that websites down at the moment.

I suggest update to Dapper because as everyone says its much more polished, but DMA will be disabled on that too.

---

