---
title: "Gparted makes a primary partition"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by lunamystry on 2007-07-29
i am trying to create a /home partition on my hard drive and I dont know how, i found this nice tutorial 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

i booted from the live disc, I downloaded Gparted and i c and licked on /dev/sda1 which is 

file system: ext3 
size: 147.64 GiB
used: 55.54
unused: 92.10GiB and 
Flags: boot

i click resize then choose I 10GiB then click resize then click on the 'unallocated" thing and click new, i select ext3 as the file system but I cant select create as logic partition only primary partition can be selected. What have not done or forgot to do when I first installed ubuntu?

Thank you for your time.

---

### Post by dabl on 2007-07-29
Ummm, I'm not sure I'm following you completely.  The normal sequence is (1) partition (2) install. I have the impression that you tried it in reverse order?

If you are running the OS, then you can't be re-partitioning any partition that is mounted and part of your filesystem.  You could unmount and re-partition unmounted partitions, if you wanted.

Is this making any sense?  :confused:

---

### Post by ugm6hr on 2007-07-29
> **lunamystry said:**
> i click resize then choose I 10GiB then click resize then click on the 'unallocated" thing and click new, i select ext3 as the file system but I cant select create as logic partition only primary partition can be selected. What have not done or forgot to do when I first installed ubuntu?


Perhaps post a screenshot of what you want the partitions to look like in order to clarify.  

You should already have at least 2 partitions (/ and swap).  If you want to create extra partitions for a separate /home, then if there are going to be a total of less than 4 partitions - they can all be primary partitions.  If not, you have to create an extended partition to fill the available space, and *then* create logical partitions *within* the extended partition.

I'm doing this from memory - so I hope that's correct!

---

### Post by mikewhatever on 2007-07-29
Logical partitions can only be created inside an extended one. Thus, the choice should be primary/extended, in case you do not have one. To get a better idea, look at the screenshot. sda4 is an extended partition that contains three logical ones, sda5,sda6,sda7.

---

### Post by lunamystry on 2007-07-30
> **dabl said:**
> Ummm, I'm not sure I'm following you completely.  The normal sequence is (1) partition (2) install. I have the impression that you tried it in reverse order?

If you are running the OS, then you can't be re-partitioning any partition that is mounted and part of your filesystem.  You could unmount and re-partition unmounted partitions, if you wanted.

Is this making any sense?  :confused:

I am trying to make a home partition for my files. I unmounted the hard drive by booting from the install disc, it is the live cd i hope. 

tell me if i didnt understand,Thank you

---

### Post by lunamystry on 2007-07-30
> **ugm6hr said:**
> Perhaps post a screenshot of what you want the partitions to look like in order to clarify.  

You should already have at least 2 partitions (/ and swap).  If you want to create extra partitions for a separate /home, then if there are going to be a total of less than 4 partitions - they can all be primary partitions.  If not, you have to create an extended partition to fill the available space, and *then* create logical partitions *within* the extended partition.

I'm doing this from memory - so I hope that's correct!

i'll learn to post a screenshot later, but I think i understand what you mean. Thank you

---

### Post by lunamystry on 2007-07-30
> **mikewhatever said:**
> Logical partitions can only be created inside an extended one. Thus, the choice should be primary/extended, in case you do not have one. To get a better idea, look at the screenshot. sda4 is an extended partition that contains three logical ones, sda5,sda6,sda7.

on the partition i gave above should i be able to make a primary or extended partition then?

---

### Post by mikewhatever on 2007-07-30
If you want your new home partition to be primary, I guess, just go ahead and create one. If you want it to be logical, you have to create and extended partition first, and then a logical one inside the extended.

---

### Post by ugm6hr on 2007-07-30
It depends on how many partitions you have already - as stated previously.  You have given details for sda1 - what about sda2, sda3.... How many partitions does sda have already?  You can have up to 4 in total for (primary+extended partitions), and extended partitions can be further subdivided into logical partitions.

---

### Post by lunamystry on 2007-08-01
Okay sorry for taking so long to reply, I didnt have internet connection for the past two days. I am creating a new partition now and I think the problem was that i didn't unmount the hard drive when i was trying to partition it. I dont know how to upload pictures yet so i cant show you what I am talking about. But i have two partitions /dev/sda1 and /dev/sda2 which is labelled extended and has a logical partition ( i think) /dev/sda5 I dont know why i dont have sda3 & 4. I'll learn to upload the pictures when I can. 

Thank you for your time

---

### Post by ugm6hr on 2007-08-01
> **lunamystry said:**
> Okay sorry for taking so long to reply, I didnt have internet connection for the past two days. I am creating a new partition now and I think the problem was that i didn't unmount the hard drive when i was trying to partition it. I dont know how to upload pictures yet so i cant show you what I am talking about. But i have two partitions /dev/sda1 and /dev/sda2 which is labelled extended and has a logical partition ( i think) /dev/sda5 I dont know why i dont have sda3 & 4. I'll learn to upload the pictures when I can. 

Thank you for your time

Sounds like sda1 is your main Ubuntu partition (/), and sda2 is an extended partition with a single logical partition sda5 (which is presumably your linux-swap).  The reason there is no sda3 or 4 is that only primary or extended partitions can be sda1-4, all logical partitions start at sda5 (on disk sda, obviously).  So that means you're not dual-booting, so less to go wrong!

You haven't told us how big sda is, or how big sda 5 is though.  A screenshot will clear that up - just click on the paperclip above the reply post text box, and it's obvious from there.

In terms of creating a /home partition - I would suggest that you could shrink sda1, then just add an extra primary partition between sda1 and sda2 to become /home.  This should automatically be labelled sda3.

I think that should work.  

Obviously, if sda5 is not linux-swap, and is actually the larger of the partitions, then I've misunderstood - and you should definitely post more details **before** doing anything further.

---

### Post by lunamystry on 2007-08-01
DAMN I FEEL STUPID!!:oops: But heres what i did,

after all the stuff of getting booting from disc and getting Gparted, I clicked on the linux swap partition and I clicked on i think stop swap or end swap i'm not sure, then clicked on the extended partition the clicked unmount. then i followed the instructions to create a new partition as from the psychocats.net/ubuntu site, it seemed to work and now i have what you see on the screenshot. My problems now are:

-how to move my stuff to the home partition and 
-how to use them from the home folder when running ubuntu, 
-how do i dual boot Kubuntu gusty gibbon with my Kubuntu feisty fawn.(i have two hard drives, one(80G) broken one that works up to the day that ubuntu does the file system check and it always fails and my other hard drive(140G) running kubuntu which was not from a clean install.)
-If i dual boot will i be able to use the home folder from gusty or copy stuff to gusty? 
-if not is there a program to copy stuff between hard drives? 

I think i ask too many questions, but you get to show off your knowledge of ubuntu, and show the true spirit of ubuntu. O:):guitar:

---

### Post by ugm6hr on 2007-08-01
I'll stick to the new /home issue - I don't know about dual-booting multiple Ubuntu's, and don't fully understand what you mean about your additional HD.

Foolow the tutorial from psychocats as is - just substitute **/dev/hda1** with **dev/sda1** and **dev/hda7** with **dev/sda3**.

Make sure you use the Ubuntu LiveCD to enter the commands.

PS: You might have been better off making the new /home bigger, with less space on /, but it's up to you, of course.

---

### Post by lunamystry on 2007-08-01
can I increase the partition now that I have already made it? or do i need to delete it then start afresh?

---

### Post by ugm6hr on 2007-08-01
> **lunamystry said:**
> can I increase the partition now that I have already made it? or do i need to delete it then start afresh?

Either is OK.  Just do it from GParted LiveCD again.

---

### Post by lunamystry on 2007-08-01
Thank you very much for your time I really appreciate it

---

