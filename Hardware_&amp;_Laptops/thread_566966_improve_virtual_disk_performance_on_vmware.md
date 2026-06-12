---
title: "improve virtual disk performance on vmware"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by brazzmonkey on 2007-10-04
hello everyone,
i often use vmware at work because one of my tools relies on heavy spreadsheets that OOo calc fails to handle properly.
excel performance in vmware is sometimes poor because of slow disk acces. my virtual disk is a pseudo 10 gb ntfs partition stored as a file (image) on my linux ext3 file system.

i wonder if there's a way to improve this virtual disk performance, be it by using a dedicated partition to store the virtual disk image, using a real dedicated ntfs partition (on which my excel files would be stored), using some exotic file system (xfs ?) to store my virtual disk image, whatever.

any clue/comment/suggestion is welcome.

thx

---

### Post by brazzmonkey on 2007-10-04
no hints ?

---

### Post by Discov3ry on 2007-10-04
If you have a way of re-using a spare hard drive, you could attach it to your system, and use it with vmware as a real physical device.

Virtual Machine Settings -> Add Hard Disk -> Use a physical disk (for advanced users).

This way you won't be taxing your host system, and slowing down the vmware.

If you can't do that, I can't think of any other way to unload the disk I/O since the vmware will always access the host hard drive no matter of the number/type of file systems you use in it.

Only a separate dedicated hard drive will give you some performance gains. 

How much memory (RAM) did you allocate for the vmware windows installation?

---

### Post by Linicks on 2007-10-04
> **brazzmonkey said:**
> hello everyone,
i often use vmware at work because one of my tools relies on heavy spreadsheets that OOo calc fails to handle properly.

Maybe you are using a hammer as the only tool.  I find that spreadsheets OOo can't handle, Gnumeric can (and vice versa, of course).

So install Gnumeric to test.

Other than that, I don't think much can be achieved using a vitual machine with Excel - Excel crashes MS machines often at work when the finance people do EOM runs etc... I think it is too bloatware to run properly anyway, let alone in a VM environment.

Nick

---

### Post by brazzmonkey on 2007-10-05
thanks both of you.
@Discov3ry
i have 2 hard drive on my laptop, one is used for system (sda), the other is used for data (/home, sdb). you suggest using a spare physical HD, could that be a dedicated ntfs partition instead ? if so, in your opinion would it be better to put it on sda or sdb ?
i allocated 768 Mb out of 2 Gb to my virtual windows.

@Linicks
actually you're right, gnumeric opens them (very quickly if you ask me), but fails to handle them properly. OOo opens them (veeeeery slowly) and seems functional, except for one file it cannot convert (i already tried to convert it on OOo on windows, but this failed as well).
These files consist of many interconnected spreadsheets (about 15), each one weights 15-18 Mb.

so :
- OOo fails to open a critical file ;
- gnumeric doesn't seem to handle interconnections and macro properly ;
- virtual excel is the only way for me. i'm open to any other suggestions, though.

cheers

---

### Post by Discov3ry on 2007-10-05
768 MB of RAM is decent (I'm running a Win 2003 Server with 384 in vmware and it's fine). 

As far as the dedicated NTFS partition, as long as it's on the same physical drive as your host (Linux) operating system then you won't see too much performance improvement. I assumed you were using a workstation but in this case when you can't use another drive (3rd) just for vmware then your best friends are defragmenting the image often and maybe turning up the memory to 1GB.

---

### Post by brazzmonkey on 2007-10-06
alright then, many thanks or your precious advices Discov3ry. i'll try that.
thanks again !

---

### Post by lynrees on 2008-02-12
Have a look at this, may be useful:

[http://www.virtualization.info/2005/11/how-to-improve-disk-io-performances.html](http://www.virtualization.info/2005/11/how-to-improve-disk-io-performances.html)

I'd suggest giving the VM 1GB of RAM, you can afford to do it if you don't intend running any more VM's.

You'd probably be better off putting the VM files on sdb as I imagine that it gets used less (less background activity). You can check disk I/O using iostat (from the sysstat package).

For example, to look at all your disks every 20 seconds (until you quit) do:

$ iostat -d -x 20

Some ideas for you...

---

### Post by nirudha on 2008-04-18
Shouldn't you be using wine or crossover office to run MS Excel in this case? It will probably server your use case much much better.

---

### Post by AlanRogers on 2008-04-18
Rather than addressing a non-existant breakage in your computer, how about addressing the apparent breakage in the business process? If that one file references up to 10 others, it's never going to be fast regardless of the environment. Updating the links on opening the file will slow it down to a crawl.
 
Can you not copy the dependent spreadsheets into the same file, so that the updates occur in memory as the file opens, rather than requiring additional disc reads. Alternatively, this sounds like it's ripe for upscaling to a database, either an MS Access or OOo Base application or a web-based one with an MS SQL or MySQL backend.
 
Those are my thoughts; you're fixing the wrong problem.

---

### Post by brazzmonkey on 2008-04-18
@nirudha
windows emulation is just not stable enough for  this kind of purpose.

@AlanRogers
indeed, a database backend would be much more efficient in terms of speed, but it would be a hell of a work to port the whole tool. and i'd need to keep a spreadsheet frontend for flexibility. i guess OOo could handle that just fine, but i don't have enough time atm, and probably ever won't.
maybe that would be a task for a few month internship...

talking about short-term workaround, maybe i should just try to rewrite the critical file i mentionned in my earlier posts, so that this could be functional on OOo.

---

