---
title: "Retrieving data from XFS disk"
date: 2009-08-11
forum: Hardware
---

### Post by luiscardoso on 2009-08-11
Hello


I'm trying, for quite some time, to retrieve data from one of two 250 Gb units that were part of an Iomega **[COLOR=#ff0000]NAS[/COLOR]** (RAID 1).
Professional data retrieval is out of the question.

I checked the drives using western digital software and they appear to be OK.
I suspect that only the **[COLOR=#ff0000]NAS[/COLOR]** motherboard went dead.

I disassemble the **[COLOR=#ff0000]NAS[/COLOR]** and plug one of drives to my pc (using EIDE).
I started my PC using a ubuntu boot cd.
The drive is recognized and, of the 4 partitions inside, I can read the first 2 directly (without having to do anything or mounting them)

In one of the other 2 partitions that I do not have access, there is one XFS partition with 232 Gb.
That's were all the data is.
I also have a partition with 125 Mb with and unknown file system (don't have a clue what's that for).

Attached you will see a print screen.

After booting, how do I gain acess to XFS partition that as all the data in?
Do I need to mount it?
If so how?
 
The intention is to broswe the content and to copy parts of it to my hard drive.
 
Please be specific since I'm not an expert at this.
 
Regards
 
LC

---

### Post by cariboo on 2009-08-11
You should just be able to mount the partition like you would any normal partition, and then have access to your data. Tod do this, open an Applications-->Accessories-->Terminal and type:

```
sudo mkdir /media/test
```

This will create a directory called test in /media. Next in the same terminal type:

```
sudo mount /dev/sda4 /media/test
```

the above command will mount your xfs partion to /media/test.

You may have to install the xfsprogs package, it is in the repositories, or just click the link:

[apt://xfsprogs](apt://xfsprogs)

---

