---
title: "Can't load Ubuntu 8.10 64 bit"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by Tony_photoplus on 2009-03-22
I have tried several times and failing to load Ubuntu onto my new machine which is a AMD64bit processor dual core.  It fails to load the guided partition and takes me to manual.  There I am stuck as I don't know which is the  right way to split the 159 GB's?  I know there has to be a swap and two more factors and thats it.  So looking to your help please.  And as its in bytes that confuse me.  GB and MBS fine thats easy (with my morphine brain it is easy to confuse these days).

Hope you can assist

Tony

---

### Post by redenex on 2009-03-22
What you can do is to leave around 4GB for swap and the rest you can make it root. (I hope you dont have any other OS installed?)

---

### Post by Tony_photoplus on 2009-03-22
> **redenex said:**
> What you can do is to leave around 4GB for swap and the rest you can make it root. (I hope you dont have any other OS installed?)

I have WinXP on 50GB's of the first part of the drive.  I have some spare at the end of the drive as well. 

I really want to know what the areas I need are as ROOT does not come up on the list of partitions.  The list is familiar to you, but not to me, its just a list and the only one I know is SWAP.  I think I need 5GB for that?  
The list which is..

EXT3 journaling file system
Reiser FS journaling file system
SFS (may have written that wrong) journaling file system
XFS journaling file system
Fat16
Fat32
NTFS
SWAP

So taking that I have 150GB's and not knowing which is which I would assume wrongly I expect that I should do the following

EXT3 journaling file system 35GB's
SWAP 5GB's
NTFS the rest

Now I know you say I am wrong, but at this stage I Haven't done anything to the comp so shall hopefully await for some experienced instruction.  Also which one do you mount?  I am searching through the mounds of info on the net, but they don't seem to give the information that corresponds to the list.  Just states make a swap file, a root file, a home file.  The only one I see is the 'SWAP'.  

Thank you
Tony

---

### Post by Tony_photoplus on 2009-03-22
I am glad I didn't take the simple road and try and calculate by moving the decimal point along to get my bytes calculated into GB's.  I would be completely wrong!!  So why do it in bytes when partitioning??

[http://www.t1shopper.com/tools/calculate/]("http://www.t1shopper.com/tools/calculate/")

1024 Bytes in 1 KB x 1024 KB in 1 MB = 1,048,576.

I know that the simple way it to get the Ubuntu setup to do the job, but it hasn't!  I am getting very frustrated not getting or finding the dam answers.  All I see is segmenting into root/home and swap!!  It does not give me the answer I am looking for.  I find that the computer speak world is always like this especially when your head is so full of morphine putting 2 and 2 together becomes a disaster.  Frustrated YES.  So really am looking forward to hopefully getting Ubuntu functioning very SOON.  Sorry I am losing it a bit, but just want to get going.  Just sick of reading and reading and not finding the right answers and coming across short explanations that don't really help and jargon.

Thanks

Tony

---

### Post by oldos2er on 2009-03-22
Hard disk manufacturers define 1 GB as one million bytes.

 The root file system is defined as / . You will need to create a root partition and swap partition, any others (e.g. /home, /var /usr) are optional.

---

### Post by Tony_photoplus on 2009-03-22
> **oldos2er said:**
> Hard disk manufacturers define 1 GB as one million bytes.

 The root file system is defined as / . You will need to create a root partition and swap partition, any others (e.g. /home, /var /usr) are optional.

I keep seeing ROOT partition but I don't see it in the choices

I really want to know what the areas I need are as ROOT does not come up on the list of partitions. The list is familiar to you, but not to me, its just a list and the only one I know is SWAP. I think I need 5GB for that?
The list which is..

EXT3 journaling file system
Reiser FS journaling file system
SFS (may have written that wrong) journaling file system
XFS journaling file system
Fat16
Fat32
NTFS

Which is it?

Thanks

Tony

---

### Post by oldos2er on 2009-03-22
> **Tony_photoplus said:**
> I keep seeing ROOT partition but I don't see it in the choices

I really want to know what the areas I need are as ROOT does not come up on the list of partitions. The list is familiar to you, but not to me, its just a list and the only one I know is SWAP. I think I need 5GB for that?
The list which is..

EXT3 journaling file system
Reiser FS journaling file system
SFS (may have written that wrong) journaling file system
XFS journaling file system
Fat16
Fat32
NTFS

Which is it?

Thanks

Tony

 What you listed above are file systems. Pick the one you want (ext3 is probably the best choice), then you set it as / .

---

### Post by redenex on 2009-03-22
:)

In that list, choose EXT3 Journaling File System and below that (as another option) you can see something called MOUNT POINT, here you choose the root (which is **/**)

I hope I made myself clear?

---

### Post by Tony_photoplus on 2009-03-22
Thanks it I will have a go, but I think I did this on my own back earlier and it failed.  We will see

Thanks

Tony

---

### Post by Tony_photoplus on 2009-03-22
TA DAAAA! Yep up and running.  Thanks for the info, its just getting your head around things.  Its been a fraught day believe me and the stress of not being able to get this loaded because it wasn't working really was the last straw.  Maybe I am in for some good luck?

Thanks

Tony

---

### Post by redenex on 2009-03-23
Glad to be of help, I get all help from the wonderful people here.

---

