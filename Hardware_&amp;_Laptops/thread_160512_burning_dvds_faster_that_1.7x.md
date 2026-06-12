---
title: "burning dvds faster that 1.7x"
date: 2006-04-15
forum: Hardware &amp; Laptops
---

### Post by discord on 2006-04-15
Hello,

I just purchased this drive from newegg.com . On the customer reviews it said it had good linux suport. I am not having much luck burning dvds though. I am getting at most 2X speed and it takes 40 minutes to burn a dvd. I've used both gnome baker and the option in nautilus to burn a dvd. In gnome baker I tried 8x speed and in nautilus it says it burns at the maximum speed possible. Anyone know how to get the full speed of the drive? do i need to make sure its using dma? hdparm?

the model of the drive... 
DVD+/-RW DUAL LG  GSA-4167B

---

### Post by Perfect Storm on 2006-04-15
Would be a good idea.
More info : [http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

---

### Post by discord on 2006-04-15
yeah i turned on dma haven't burnt a cd yet but it still seems slow to read (2,983 KB/s) . Anything else I need to do other than turn dma on?

---

### Post by Perfect Storm on 2006-04-15
Go into System Tools ---> Gconf (configuration editor/tools).
Under apps you'll see Gnomebaker and nautilus. Make your changes there to your likening.

---

### Post by discord on 2006-04-15
ok so it works. it will be nice the day that dma is automagically set when we hook up a dvd or any ide device, considering most devices today are dma compatible i find it strange ubuntu does not do this already...

---

### Post by Perfect Storm on 2006-04-16
It does it on Dapper. Well on my machine anyway. :)

---

