---
title: "newbie install"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by shaggy2dope0001 on 2007-08-30
hi

i am trying to convert my xp pro desktop over to ubuntu feisty fawn 7.04  but i am having problems with hdd permissions i dont know exactly what i am doing but just to give some help this is what i have:

asus p4s800d-e deluxe mother board
intel p4 3.0 c processor
nvidia gforce fx5600xt vid card
soundblaster audigy 2 xt
linksys gigabit ethernet
2 x maxtor sata hdd 
40 gig ide
60 gig ide
dvd-rw dual layer burner
wintv card



my main question is "will i have any issues with drivers and how can i change the permissions for the hdd so that multiple users have access to them and have their own partitions for private use?"

if youcould give some help then i would greatly appreciate it. 

Thanx again

---

### Post by ddrichardson on 2007-08-31
I cannot see any major problems for your hardware but that's why we do a live cd - so c=you can check for problems before installation.

Permissions on partitions aren't a problem. I don't know if you are familiar with how disks are mounted, however unlike Windows all devices are viewed as files. This means you mount seperate partitions for users directories (created automatically) which would normally be /home/username. However this is strictly speaking unneccessary as users folders are protected by default.

Bear in mind that you are restricted by BIOS as to how many partitions can be configured, so perhaps the best solution is a /home partition where all users home folders are stored.

---

### Post by shaggy2dope0001 on 2007-08-31
what i am looking for is a way to mount 2 partitions, 1 for each user, and the rest as shared access. but i am unfamiliar with ubuntu commands to accomplish this task. also i wondering if there was a way to access dual screen in ubuntu?  i know my vid card is able to accomplish this task but i dont know how to make ubuntu do the same.

---

### Post by ddrichardson on 2007-09-01
Partition mounting is controlled by a file called```
/etc/fstab
```

There is much more information in the terminal if you type```
man mount
man fstab
```But the general format already there will guide you.

Essentially in this case you will have two partitions, which Linux names sequential dependant on the interface they are attached to. So say you want the second  and third SATA partitions for user1 and user2:```
mount /dev/sda2 /home/user1
mount /dev/sd3 /home/user2
```

With respect to dual monitors, this is indeed possible, but we would need to know what monitors and graphics card to point you in the right direction.

---

### Post by shaggy2dope0001 on 2007-09-01
the graphics card i am using is the nvidia geforce fx 5600 xt with a KDS crt and i was wanting to use my s-video for my tv so i could watch movies.
also i am using the NVIDIA accelerated graphics driver and i am using Ubuntu fiesty 7.04

---

### Post by ddrichardson on 2007-09-02
Try ```

sudo nvidia-settings
```From the terminal and enable it.

---

