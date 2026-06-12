---
title: "swap file inlargement"
date: 2008-09-27
forum: General Help
---

### Post by Len Tyree on 2008-09-27
i recently added more RAM to my system, and ow i need to increase my swap file size.
but how?  i loaded gpartion, but it will not allow me to update my swap file.
i looked at cfdisk, but it seems like i could easily ruin my system if i tried to update with it.
so i need a little help, please.
my system is a desk computer, 2,66 ghtz, 80 gb hard drive, and now 2 gb ram, with a swap file of only 755 mb??

thanks much, for any help.  len tyree.

---

### Post by _sAm_ on 2008-09-27
755mb is more then enough for you, in fact you could be fine with less. To check yourself run htop in the terminal and run the programs that you normally do and you will see that all your ram is not used.

Using the swap file when you have free ram will decrease the performance - so I would changed the swappiness on your system(witch means tell the system to not use swap until all ram is used). Howto here; [http://www.my10sen.com/2007/10/05/ubuntu-a-speedup-guide/](http://www.my10sen.com/2007/10/05/ubuntu-a-speedup-guide/)

If you still want more space for swap I would made a new partition and turned it in to a swap file with the same priority as the old one.

---

### Post by Len Tyree on 2008-09-29
thanks sAm:
i looked at the my1Osen.com site and will return to it for more later.  but until then, a further question.  you state that 755mb is enough for 2gb of ram as a swap file, however, i have read/seen many places that the swap file should be at least twice the size of the ram??  i refer to Keir Thomas book beginning Ubuntu Linux, and a few more books.  so which is right?
thanks, len.

---

### Post by Ryadt on 2008-09-29
Swap is needed to be twice the size of ram when ram is less than 1gb or for hibernation process. If you don't intend to do hibernation, then with a 2gb ram, the swap partition is pretty much useless.

---

### Post by kpkeerthi on 2008-09-29
If you ever have a need to suspend to RAM or hibernate, your swap should be atleast as big as your RAM so ubuntu can dump contents from RAM to SWAP space. Otherwise, your swap size is more than sufficient.

To resize swap, you need to first make room for expanding it using gparted. Shrink the partition that is in front of your SWAP and than resize SWAP fill the empty space you just created. 

**Warning:** This might change the UUID of the partitions. You may want to update your /etc/fstab with the new UUID of your swap and the partition you shrank. Use **sudo blkid** command to find out the new UUIDs.

---

### Post by TVC15 on 2008-09-29
Hello,

Recently I also added more memory to my system and increased the swap space accordingly.  
Make sure you set the swap file to "active" after making the changes.  You can do this in Partition Editor -> right click on the Swap partition and select activeon.

BTW: I used Acronis disk director to resize my EXT3 partition and swap partition.  I find it safer to perform operations like this an filesystem that is not "active" or in use.
Of course, Acronis is not opensource. But is does the job.

Hope this helps anyone.


Greetings

---

### Post by bodhi.zazen on 2008-09-29
> **Len Tyree said:**
> thanks sAm:
i looked at the my1Osen.com site and will return to it for more later.  but until then, a further question.  you state that 755mb is enough for 2gb of ram as a swap file, however, i have read/seen many places that the swap file should be at least twice the size of the ram??  i refer to Keir Thomas book beginning Ubuntu Linux, and a few more books.  so which is right?
thanks, len.

That advice is outdated. You can check it for yourself if you wish.

Lest start with an understanding of what swap is. Swap is space allocated on your hard drive for use when you run out of RAM.

So if you have LOW RAM you need MORE SWAP.

But, If you have HIGH RAM you need LESS SWAP.

So , on desktops with RAM > 1 Gb you may never use swap.


To see you memory usage :

```
free -m
```

Nowadays people are advising either swap = 512 Kb of no swap. You can turn swap off with swapiness.

[http://ubuntuforums.org/showthread.php?&t=327496](http://ubuntuforums.org/showthread.php?&t=327496)

[http://www.linux.com/guides/sag/swap-allocation.shtml](http://www.linux.com/guides/sag/swap-allocation.shtml)

[http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html](http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html)

To turn it off see : [http://marutosan.blogspot.com/2007/05/tweaking-linux-for-speed.html](http://marutosan.blogspot.com/2007/05/tweaking-linux-for-speed.html) (See #9 and 10).

=========

The only "exception" to all this is on Laptops. When you use suspend (sleep) or hibernate your current memory (RAM) is dumped to hard drive (swap). When restoring your laptop the process is reversed swap => RAM, viola

Thus if you have a laptop and use these features swap = RAM.

---

### Post by Len Tyree on 2008-10-01
SOLVED --- thanks to all.  i think i get the picture, more swap is unnecessary!!!
so I will leave things as they are.

thanks again, len. [http://ubuntuforums.org/images/icons/icon7.gif](http://ubuntuforums.org/images/icons/icon7.gif)

---

