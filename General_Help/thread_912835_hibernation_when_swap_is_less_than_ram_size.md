---
title: "hibernation when swap is less than ram size"
date: 2008-09-07
forum: General Help
---

### Post by dexter.deepak on 2008-09-07
i always thought that we cant hibernate on a machine with swap less than ram size. but one of my friends told me that he has done hibernation on a machine with 512 mb swap , and 1.5 gb ram...and i still cant trust him..is that really possible ? 
i would like to add that he hs not used any mechanism such as swap file (although i dont feel that having a swap file helps in hibernating)

i would also like to know the hibernation mechanism...where does the ram content go, when we hibernate, i.e, on which partition ?
and is it only the ram content which is saved on harddisk or anything else too ?

---

### Post by F W Adams on 2009-02-15
I'd also like to know the answer to the above questions.

Using SWAP for storage of ram for hibernation would hardly seem a normal use of SWAP space, or a necessary one when it could equally be put elsewhere on the disk?

Also a couple of other questions a bit relevant before I make a new thread.

On a 32 bit system it would seem that only a maximum 2^32 bytes ( 4GB ) can be addressed using a 32 bit bus so is there any point in allowing SWAP + physical ram to be over 4 GB? If hibernation uses SWAP then it's different, then SWAP needs to be as big as physical?

Anyone know more about this?



For those that know less than me remember that you can watch memory usage using system/administration/system monitor, to see if memory is a problem.

---

### Post by donnykurnia on 2010-09-16
Well, today I experience this by myself. I just buy a 2GB RAM for my laptop to upgrade the RAM from 2GB become 3GB. When I install ubuntu, I just prepare 2GB for swap.

I successfully install the new RAM, boot the laptop, and ready to resize swap partition. Before do that, I try to test the hibernation feature. Surprisingly it worked.

My guess is that this is because the swap partition needed for hibernate is determined from the data stored in RAM before hibernation. So by closing applications that takes RAM spaces until it below 2GB, then you can safely hibernate.

---

### Post by dcstar on 2010-09-16
> **donnykurnia said:**
> 
.........
My guess is that this is because the swap partition needed for hibernate is determined from the data stored in RAM before hibernation. So by closing applications that takes RAM spaces until it below 2GB, then you can safely hibernate.

Yes, hard disks are SO small these days that it just isn't worth allocating sufficient swap space to not have to stuff around closing things to hibernate.....

Gimme a break.....

---

