---
title: "Swap File/Partition Forensics"
date: 2008-11-08
forum: General Help
---

### Post by CoolZone on 2008-11-08
Hi,

I'm currently undertaking a project for my degree that involves analysing the Swap Partition on an Ubuntu desktop.

I am looking to see if anyone can point me in the right direction to get some technical information on how the swap partition works.
Books, web links, journals would all be appreciated.

If any one has any experience on this subject, not necessarily from the forensic point of view but any point of view that would deepen the understaing of the subject that i have.

Thanks

---

### Post by cariboo on 2008-11-08
Have a look here:

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/ch-swapspace.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/ch-swapspace.html)

and here:

[http://www.linux.com/feature/121916](http://www.linux.com/feature/121916)

and here:

[http://www.cyberciti.biz/tips/performance-tuning-for-linux-swap-partition.html](http://www.cyberciti.biz/tips/performance-tuning-for-linux-swap-partition.html)

Jim

---

### Post by CoolZone on 2008-11-08
Hi,

Thanks for your response.  There is some useful information there, but what I am looking for is more to do with information about the file structure of the Swap Partition.  For example, is it just a random dump of data as it is in a Windows pagefile.sys or is there a file structure to reduce the build up of fragmentation?

---

### Post by unutbu on 2008-11-08
See Chapter 11 of 
[http://www.informit.com/content/images/0131453483/downloads/gorman_book.pdf](http://www.informit.com/content/images/0131453483/downloads/gorman_book.pdf)

You can find additional information by googling "Linux virtual memory".

You can also download the latest linux kernel ([http://www.kernel.org/](http://www.kernel.org/)) and look at pieces of the source code such as /usr/src/linux/mm/swap.c

---

### Post by CoolZone on 2008-11-10
Thanks,

great help

---

