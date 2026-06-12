---
title: "[SOLVED] Resize linux partition"
date: 2008-10-25
forum: Hardware
---

### Post by mistweaver4 on 2008-10-25
Hello Everyone!

I am running a dual boot system of XP and Ubuntu. I have my harddrive split 75/25% and i want to make this more of a 50/50 split. 

I used gparted to set everything up originally. Its telling me that it cant resize the partion with linux on it because it is mounted. it wont let me unmount the drive because it needs it to run im assuming. 

My question is how can i move the partition without reformatting anything?

any help is of course greatly appreciated!!!

---

### Post by lordadi on 2008-10-25
Hi,

Since you have already mentioned Gparted, I will assume you can use it and so will recommend you try the Gparted Live CD to do the job.

Just download, burn and boot.


Happy resizing, 



Lordadi.

---

### Post by mistweaver4 on 2008-10-25
Thanks lordadi!

I did this and i managed to shrink the linux partition to the correct size. Now i have the windows side, the linux side, and an unallocated side.

how do i merge the windows side with the unallocated side?

---

### Post by logos34 on 2008-10-25
if the windows partition is contiguous to the empty space, you should be able to drag the border over to incorporate it.  

Post output of 

sudo fdisk -l

or a screenshot of Gparted

---

### Post by mistweaver4 on 2008-10-25
the unallocated area is on the other side of the linux location

[IMG]http://i341.photobucket.com/albums/o387/fadingtaillights/Screenshot.png[/IMG]

---

### Post by logos34 on 2008-10-26
Here's what I suggest:

1. Delete sda6 or sda5 (you only need one swap partition) and resize the extended partition to match.   Make sure /etc/fstab lists the correct one.

2. Grow / (sda3) to the end of the disk to reclaim the unallocated space.  Then shrink it **on the left boundary** ( what you should have done in the first place).  This will take quite a bit longer (maybe ~ 1 hr) than doing it on the right side because gparted has to copy and move all the files over.

3.  Now expand grow sda2 ntfs to the right to incorporate unallocated space

---

### Post by mistweaver4 on 2008-10-26
It works!

Thanks folks!

---

