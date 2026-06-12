---
title: "Using GPartEd on internal SATA disk via eSATA port"
date: 2012-03-24
forum: Hardware
---

### Post by GwibberFooey on 2012-03-24
This may be more of a hardware question than an Ubuntu question...

Is it possible to use GPartEd to format an internal hard disk by connecting it to an eSATA port if I have the right kind of cable? Does such a cable exist? 

The reason for asking is because I need a bios_grub partition and/or an efi partition to be able to install Ubuntu but obviously I can't use an application such as GPartEd without first installing the Ubuntu operating system.  So I want to take the internal SATA harddisk and plug it into the eSATA port on my laptop computer and then use GPartEd to format it.  

Am I living in some sort of dreamland ?

---

### Post by recluce on 2012-03-24
> **GwibberFooey said:**
> This may be more of a hardware question than an Ubuntu question...

Is it possible to use GPartEd to format an internal hard disk by connecting it to an eSATA port if I have the right kind of cable? Does such a cable exist? 

The reason for asking is because I need a bios_grub partition and/or an efi partition to be able to install Ubuntu but obviously I can't use an application such as GPartEd without first installing the Ubuntu operating system.  So I want to take the internal SATA harddisk and plug it into the eSATA port on my laptop computer and then use GPartEd to format it.  

Am I living in some sort of dreamland ?

1.) You can run GParted from a Live CD without installing Ubuntu.

2.) Yes, you can connect an "internal" drive through an eSATA port and it will be treated just like any other SATA drive. Best is to get a hard disk dock, here is one example of these critters:

[http://www.amazon.com/StarTech-com-External-Docking-3-5-Inch-SATADOCKU2E/dp/B001J8BPYM/ref=sr_1_2?ie=UTF8&qid=1332637305&sr=8-2](http://www.amazon.com/StarTech-com-External-Docking-3-5-Inch-SATADOCKU2E/dp/B001J8BPYM/ref=sr_1_2?ie=UTF8&qid=1332637305&sr=8-2)

Be sure to connect through eSATA (not USB) for optimal performance. I use this on my system all the time, all SATA functions are available, even SMART. Throughput on my machine is about 80 MB/s.

---

### Post by GwibberFooey on 2012-03-25
Thanks for taking the time to answer my question.

---

