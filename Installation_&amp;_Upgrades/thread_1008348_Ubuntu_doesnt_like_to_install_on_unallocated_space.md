---
title: "Ubuntu doesnt like to install on unallocated space?"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by Phillyman on 2008-12-11
I wanted to do a dual boot setup with XP and Ubuntu 8.10, I have a 1TB drive that was partitioned the following way.

75GB = XP
272GB = Data1
272GB = Data2
40GB = Unallocated
272 = Data3

So I went to install Ubuntu last night and I could not get it to install on the Unallocated space. So I exited out of the installer which dropped me into the Live CD. I ran the partitioning software and tried to create a new partition out of the Unallocated space, but I was told I could not have more then 3 Primary Partitions....so I had it move Data3 to the left and merge with the 40GB of Unallocated space. That took forever, and I went to bed.

So now what I am hoping will happen is that when I go home today, I can run the installer and have it pull 40GB of free space from Data3 to create Linux partitions and install on. Will I finally be able to install it today, or will I still run into the 3 Primary partition limit?

---

### Post by mikewhatever on 2008-12-11
> **Phillyman said:**
> 
So now what I am hoping will happen is that when I go home today, I can run the installer and have it pull 40GB of free space from Data3 to create Linux partitions and install on. Will I finally be able to install it today, or will I still run into the 3 Primary partition limit?

No, that's not gonna happen, sorry. Just as the day before, the partitioner will tell you that you can't have more then four primary partitions. To get around this, you'd have to delete one of the primary partitions and create an extended one in its place.

---

### Post by Pumalite on 2008-12-11
The rule is 4 primaries per drive. Ubuntu needs 2 though. Make your unallocated space an extended partition and within it install Ubuntu.

---

### Post by Phillyman on 2008-12-11
Ok so what I am doing right now is the following

Deleted Data1
Deleted Data2
Deleted Data3

Which gives me 856GB free unallocated space

Then I am creating a 816GB Extended partition, and then I will create three 272GB Logical drives and then finally creating a 40GB Primary Partition....which will look like this...

75GB = Xp (Pri)
272GB = Data1 (Log)
272GB = Data2 (Log)
272GB = Data3 (Log
40GB = Ubuntu (Pri)

Will that work?

---

### Post by dabl on 2008-12-11
Where are you planning to have the swap partition?  :confused:

---

### Post by Pumalite on 2008-12-11
No. Make your first partition for XP and make it sda1 primary. The rest is up to you, but I'd install Ubuntu within an extended partition. It works fine with logical partitions.

---

### Post by Phillyman on 2008-12-11
> **dabl said:**
> Where are you planning to have the swap partition?  :confused:

Wont Ubuntu just auto create all its needed partitions within the 40GB of free space I give to it. I have installed Linux a few times before (Mandrake, Redhat, Suse) and it always seemed to work out.

Tell me oh wise Ubuntu gurus, I have a 1TB Drive, and I have 40GB to spare to Ubuntu....how should I split it up?

---

### Post by mikewhatever on 2008-12-11
> **Phillyman said:**
> 

75GB = Xp (Pri)
272GB = Data1 (Log)
272GB = Data2 (Log)
272GB = Data3 (Log
40GB = Ubuntu (Pri)


Yes, that is a nearly good setup. Just add another 1 GB logical partition for swap and you are done.

---

### Post by Phillyman on 2008-12-12
Well I got it all straightened out last night, This is how my 1TB drive is set up


75GB = Windows XP (Primary)
Begin Extended Partition
272GB = Data1 (Logical)
272GB = Data2 (Logical)
272GB = Data3 (Logical)
4GB = Swap (Logical)
18GB = Root (Logical) (ext3)
18GB = Home (Logical) (ext3)
End Extended Partition

For some odd reason Grub wasnt loading on the boot, so I kept dropping into windows, I read some files online and reinstalled Grub, then the XP entry was not working, I then edited the Grub information file a few times and got that working also. Wondering what fun I will have when I upgrade to Vista next month....oh the joys! ):P

PS - I have played with Linux a few times in my life, the first was back with Mandrake 7 (2001?) and one of the things I hated about it was how you had to install programs, and also that whenever you reloaded Windows....it messed up Linux. But now with the Live CD I can fix that problem fast, and it seems that the community has come along nicely since those days. 

Thanks for all your help

-Rob

---

