---
title: "Partition Help?!"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by SeanKing on 2009-01-02
Hello Everyone,

So here is my problem. I have a 149 gig hard drive partition like this :

HP Recovery 10.33 gigs (primary)
Vista       56.99 gigs (primary)
Swap         1.91 gigs (primary)
Ubuntu       9.53 gigs (primary)

Unallocated 70.29 gigs

I want to format the unallocated 70gigs but i cant in windows because I have maxed out with the 4 allowed primary partitions. when I try to format the 70.29gigs windows only allows me to do a new simple volume which will erase all OS's. Any suggestions?

---

### Post by khelben1979 on 2009-01-02
Use that free space on one of the existing partitions instead.

---

### Post by SeanKing on 2009-01-02
How can I do that?

---

### Post by khelben1979 on 2009-01-02
You could try to use [Partition Magic]("http://en.wikipedia.org/wiki/Partition_Magic") to resize one of those partitions.

I have never done that with Partition Magic myself, though. So I can't guarantee anything.

---

### Post by Johnny-Cache on 2009-01-02
do you want to format to install an o/s or just use the space?  Partition magic will keep your files intact( I just did it) but you must boot into windows to install it

---

### Post by SeanKing on 2009-01-02
I want to format it so i can use the space. Partition magic will format it for me? i dont want it to mess with my other partitions...

---

### Post by Johnny-Cache on 2009-01-02
I would use partition magic in windows or gparted in ubuntu and delete the partition barrier  and add that 70gb to one of the other drives.  Data will stay in tact and you will still the under the windows allowable so you see that drive.

---

### Post by ajgreeny on 2009-01-02
If the partitions and free space are the order you showed in the list you can easily add the free space  to the ubuntu partition using partition editor (Gparted) in the live ubuntu CD.  You should use the live CD as it will ensure your partitions are not mounted.  If the partition order is not as shown it may be more difficult as you may need to move partitions on the disk, a long and time consuming process, though I have done it successfully, and then add the free space to an adjacent existing partition.

---

### Post by SeanKing on 2009-01-03
So i used gparted to add the unallocated partition to my ubuntu partition. What I really wanted to do was make a share partition so Vista and Ubuntu can share. Since I added that partition to Ubunut my hard disk is looking like this :

79.82 Ubuntu
 1.91 Swap
56.99 Vista
10.33 HP recovery

Is there a way I can erase my swap, add it to the Ubuntu partition, then create a swap within that partition?

---

### Post by ajgreeny on 2009-01-04
Why do you want to do that?  Swap is (nearly) always a separate partition, and there is little reason to change things if they all work OK,  If you let ubuntu install in the default manner it would make a separate swap partition, so my advice is to leave things alone.

---

### Post by SeanKing on 2009-01-05
Oh ok I didnt know that swap was usually a seperate partition. I just thought it would be useful to have a file partition that both OS's could share... Thanks

---

### Post by Ptero-4 on 2009-01-05
> **SeanKing said:**
> Oh ok I didnt know that swap was usually a seperate partition. I just thought it would be useful to have a file partition that both OS's could share... Thanks
It wouldn't work since windoze and linux use a different way of handling the internals of their virtual memory systems.

---

