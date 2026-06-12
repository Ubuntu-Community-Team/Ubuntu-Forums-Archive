---
title: "SATA drive stuck in 16-bit (?)"
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by WakkiTabakki on 2005-03-05
Hello 
I'm running Hoary (manically updated) on a AMD64 comp using an Abit Kv8-Max3 motherboard (via82cxxx is loaded as a module).

When I run hdparm I get this:
> 
Large@Linux> sudo hdparm /dev/sda

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 24321/255/63, sectors = 200049647616, start = 0


I still have a fairly good tranfer rate:
> 
Bucket@Linux:~ $ sudo hdparm -t /dev/sda

/dev/sda:
 Timing cached reads:   1668 MB in  2.00 seconds = 833.29 MB/sec
 Timing buffered disk reads:  152 MB in  3.03 seconds =  50.22 MB/sec


Ok, so now I want to kick it up in 32-bit mode (it has been around since the early 90's, so it's about time right?)
> 
oLard@Linux:~ $ sudo hdparm -c 1 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 IO_support   =  0 (default 16-bit)


I've tried with different params with the c-option, but the only one that works is 0, i.e 16-bit... (I've also tried most other options, e.g dma, read_ahead and none seems to work)

So, whats up? I read somewhere that SATA drives can't use hdparm, and we're supposed to wait for a tool that works... Is that right?

Thankful for any input

/N

---

