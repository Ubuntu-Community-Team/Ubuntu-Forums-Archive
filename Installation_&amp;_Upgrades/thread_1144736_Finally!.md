---
title: "Finally!"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by dakota_oneill on 2009-05-01
Okay I finally got Kubuntu installed. But now I have a problem, because I didn't know what I was doing it partitioned my hard drive, into three drives. So my 120GB external hard drive is now

[IMG]http://sixpop.com/files/152/errr.jpg[/IMG]


[IMG]http://sixpop.com/files/152/errr1.jpg[/IMG]

I thought i when I set that number to 40.5 was going to be the install not the only room I have. So my 38.2 GB of stuff on my hard drive is there and I can't have anything else! And as you see in the first image there is a second partition on it that is 68.30 GB but I can not access that. So how can I fix it so I have as much room in my "F" drive as possible which I think (it said when I was setting the numbers) 110 GB?

---

### Post by dakota_oneill on 2009-05-01
Help?

---

### Post by SuperSonic4 on 2009-05-01
You could try deleting the 68.30GB one and extending the leftmost partition to the right to fill the space - this will delete anything on the middle partitionq

---

### Post by cariboo on 2009-05-01
I would suggest doing what you need in Kubuntu, as Windows can not read ext2-3-4 formtted partition with out a little help from 3rd party drivers. You can resize your kubuntu partition by booting from the LivCD and using qtparted to adjust the size of your partition.

If you try to do the adjustments in Windows, you will end up with nothing but a mess.

---

