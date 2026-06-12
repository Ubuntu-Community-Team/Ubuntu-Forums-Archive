---
title: "Help to create swap file"
date: 2006-01-06
forum: Installation &amp; Upgrades
---

### Post by raul99 on 2006-01-06
I am new to Linux and am midway into an Ubuntu installation. I have partitioned my second IDE HD and get the following configuration:

IDE 2 slave (hdd)  - 60 GB WDC
#1 primary 20.0 GB  ext3
pri /log 40.0 GB     Free Space

When if click finishing partitioning and write changes to disk, I get a reminder to create a swap file ( which I intend to do ,500mb ) but it take me no futher.

How do I create swap file? 
What does skull and crossbones following line 2 above mean?
thanks

---

### Post by adwait on 2006-01-06
It is reminding you to create a swap PARTITION. You need to do that while partioning. Just make a 500 MB partition and select the file system to be "swap". 

The sign you are talking about indicated destructive partitioning, meaning all data will be lost on that partition.

---

### Post by Derspankster on 2006-10-24
Any benefit to creating a swap file on a 2nd physical drive? I have an old 2 gig drive sitting here and I've thought of using it for my swap file. Thought it might improve performance over using a partition on the system drive. Can this be done and will there be any benefit to doing so?

---

### Post by bulldog on 2006-10-24
> **raul99 said:**
> I am new to Linux and am midway into an Ubuntu installation. I have partitioned my second IDE HD and get the following configuration:

IDE 2 slave (hdd)  - 60 GB WDC
#1 primary 20.0 GB  ext3
pri /log 40.0 GB     Free Space

When if click finishing partitioning and write changes to disk, I get a reminder to create a swap file ( which I intend to do ,500mb ) but it take me no futher.

How do I create swap file? 
What does skull and crossbones following line 2 above mean?
thanks

Right click the empty space and choose make new partition.
Make your disired properties and mount it  as swap.

Edit:
Hmmmmmmmmmmm..........pretty old topic :D

---

### Post by bulldog on 2006-10-24
> **Derspankster said:**
> Any benefit to creating a swap file on a 2nd physical drive? I have an old 2 gig drive sitting here and I've thought of using it for my swap file. Thought it might improve performance over using a partition on the system drive. Can this be done and will there be any benefit to doing so?

This could be done but don't expect a great boost of it.

Only if you have less then 512MB RAM installed you can expect some improvement.

If you have 1024MB of RAM your swap is hardly used.

---

### Post by Derspankster on 2006-10-24
I have 1024 MB so it sounds like it's not worth it. Thanks for the reply.

---

### Post by Coelocanth on 2006-10-24
I would say it depends on what you use your rig for. If you're doing a lot of graphics intensive/RAM-eating work such as video editing or photo editing, then it would be worth it, as you'll eat up your RAM pretty quick. The swap file on a separate drive will vastly decrease your seek times, and make things faster. Gaming can also benefit from this as well.

---

