---
title: "[SOLVED] Extra Ram Needed For Old Pc!"
date: 2008-10-07
forum: Hardware
---

### Post by Rytron on 2008-10-07
Hi,
I have an old Pc.
It has 256MB of Ram. Attached is the type of Ram it takes.
The Pc is 6 years old.

Does anyone know what other type of Ram will work in it and where extra Ram could be bought?

Thanks.

---

### Post by ronnielsen1 on 2008-10-07
It's DDR 1 Ram - not too old. I use it on my computer but that picture doesn't tell us how much ram your computer is capable of handling (probably 1Gig but maybe only 512M)
DDR1 is unfortunately twice as expensive as the newer DDR2 but it's available at Office Depot, Best Buy etc.

We need a make and model # for your computer to find out how big you can go

---

### Post by hyper_ch on 2008-10-07
run
```

sudo lshw --html > ~/Desktop/hardware.html
``` and upload it to a webpage and give us the link here ;)

---

### Post by Mze on 2008-10-07
your RAM is PC2100

[PC2100]("http://en.wikipedia.org/wiki/PC2100") info on Wikipedia

You may want to run a search on Google to find more info

More memory modules can be added but you need to provide your motherboard info. For sure, you can add additional modules of memory.

the command posted above by hyper_ch should be:

**sudo lshw -html > ~/Desktop/hardware.html**

---

### Post by Rytron on 2008-10-07
The motherboard model is [GA-8SIML]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=1335").

---

### Post by ronnielsen1 on 2008-10-07
That tells you right there.

> 
[LIST=1]
[*]2 x 184-Pin DIMM slot
[*]Supports up to 2GB DDR266 memory
[/LIST]

So you can buy 2 1GB Memory sticks that run at 266 speed

---

### Post by ronnielsen1 on 2008-10-07
[http://www.ec.kingston.com/ecom/configurator_new/PartsInfo.asp?root=us&LinkBack=http://www.kingston.com&ktcpartno=KVR266X64SC25/1G](http://www.ec.kingston.com/ecom/configurator_new/PartsInfo.asp?root=us&LinkBack=http://www.kingston.com&ktcpartno=KVR266X64SC25/1G)

---

