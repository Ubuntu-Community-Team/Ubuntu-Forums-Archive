---
title: "Would using a ramdisk instead of hard disk be faster?"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by Kvark on 2006-04-06
I just heard that with Ubuntu and Linux in general you can use ram memory as hard disk space and I don't know anything about how that works yet but it got me thinking...

I use 2.7GB of hard disk space in total when all programs I want are installed and all my personal files (several thousand files of course but mostly text documents and images, no music, movies or other big things) are on the hard disk.

What if I got myself 4GB ram, set something up to copy all data to a 3GB ramdisk partition before booting and used the last 1GB as memory. Then the the hard disk would never need to be used. The hard disk is often blamed for being the slowest part of a computer so not using it at all would speed things up quite a bit right? And if so how big would the difference be? Would it be a good or bad idea?

The only obvious problem I see is that a system chrash or power outage would kill all the data but so far that happens more rarely then new Ubuntu releases so it is fully acceptable. A daily full auto-backup or maybe hourly for the important files would provide enough safety.

I'm going to buy a new computer this summer and thats when I'm thinking of doing this. Since it isn't an existing computer I could do anything else instead. Like get a 5GB flash drive or a pair of 10k rmp hard disks in raid0. But the other alternatives are not as fast as ram right?

---

### Post by StefanoCole on 2006-04-07
Well, with Ubuntu I have no experience, but I have tried Damn Small Linux. DSL has a boot option to load to ram. Using that option you get better performance. Anyway DSL is a very small (i.e. compact) distribution, so I don't know if the same is feasible for Ubuntu.

Stefano

---

### Post by Ocxic on 2006-04-07
yes loading the entire ubuntu system to a ram disk would technicaly be faster, but you have to look at what kind of space your using, 2.4GB is fine for a base install, but for me to run happily and with all of my programs I'm currently using 3.5GB plus 3.1GB on my home partiton, not to mention anything stored on you harddrive would take the same amount of time to load anyway. 
Your idea is plausable but prolly not realistic. besides, the running system is already loaded into active memory, so anyhting your running is stored in RAM anyway.

---

### Post by Kvark on 2006-04-07
Wow so DSL has that option, I'll go searching for DSL ramdisk benchmarks.

Yeah the running apps and open files are loaded into memory after they have been read from the hard disk but the hard disk is still used quite often during normal desktop work. I've even heard several times that hard disk performernace is irrelevant because Linux caches stuff in memory in a smart way but dunno if I believe that cause in that case there would be no speed difference with live CDs compared to hard disks.

---

### Post by Ocxic on 2006-04-07
well, you can't have everything loaded into memory, orthwise you'd need like 10GB of ram. the system only loads program data from the hard drive into memory when needed, after that the program/data sits in meory until it's no longer needed, or the program is shut down. i don't think there's any getting around it, you'll always need some sort of storage media to keep data on it's just no fesable to load everything into memory. and a waste

---

### Post by ssalman on 2006-04-08
Keep in mind that DSL is a minimalist distro by definition, it's only 50mb in size, and uses kernel 2.2.

I use DSL on an older laptop and it is extreamly fast and responsive, but it does not have all what Ubuntu, Suse and all the other big distributions have to offer, again because of it's minimalist design. but because of it's design you can load the entire distribution into memnory, and still have plenty of ram for other applications.

in DSL all you have to do is to boot the kernel with the "toram" option in the boot loader.

Give it a try. but if you have a system with that much ram, you'l probably won't be satisfied with the limitations of DSL...

---

### Post by ghakko on 2006-04-08
Just about all modern operating systems will cache disk I/O aggressively. The Linux kernel, in particular, tries to use unallocated memory (memory that's not in use by programs) as disk cache.
```
$ free
             total       used       free     shared    buffers     cached
Mem:       2064744    1621876     442868          0        548    1289140
-/+ buffers/cache:     332188    1732556
Swap:      4194296          0    4194296
```
The above is for a system with 2GB of RAM; note how much memory the kernel has squirreled away for the disk cache. 

Thus, it doesn't make much sense to manually set up RAM disks to avoid disk I/O when the kernel does the same thing automatically.

What might make sense, though, is a cache *prefetching* scheme. Prefetching slurps into cache files which are likely to be read soon. This can reduce system boot time and (sometimes) application startup times.

In OS X, prefetching is done with some help from its HFS filesystem, which marks frequently used files as ["hot"](http://www.kernelthread.com/mac/apme/optimizations/#THREE). These get stored and kept defragmented in a special area near the start of the disk and are always kept cached. A special kernel extension will read these files into memory very early in the boot process.

The [URL=http://msdn.microsot.com/library/default.asp?url=/library/en-us/appendix/hh/appendix/enhancements5_0eecebea-e58b-4c95-8520-9b1dc2bc6196.xml.asp]
"Logical Prefetcher"[/URL] in Windows XP and later does roughly the same thing.  Windows Vista is to ship with a adaptive prefetcher called ["SuperFetch"](http://www.windowsitpro.com/Article/ArticleID/48085/48085.html).

In Ubuntu, the "readahead" package (installed by default) provides a pair of scripts which do boot prefetching by reading a list of files into cache just after the root filesystem is mounted. (You'll see it as "reading files needed for boot" in the bootsplash progress box.) To tune "readahead" and rebuild the list, just pass the "profile" boot option to the kernel.

---

### Post by Kvark on 2006-04-08
Ghakko, that was some great information you pointed out, thanks!

I'll go read up on prefetching and specially that readahead profile thingy. It sounds like the right way to make the system read from ram instead of the hard disk.

---

