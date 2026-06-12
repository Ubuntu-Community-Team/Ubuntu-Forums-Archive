---
title: "Server with Raid"
date: 2010-09-22
forum: Hardware
---

### Post by xionhack on 2010-09-22
Hello. I am building a PHP application that will have a lot of sensitive information. I want to use an ubuntu server because I've heard than having a windows 2003. I just want to know what specs should a computer that is going to be accessed through the network by at least 400 employees a day. Also, I would like to have it RAID, is that possible (easy?!!) in an Ubuntu server. Thanks!

---

### Post by xionhack on 2010-09-30
Is it not possible to do RAID with ubuntu?

---

### Post by whoop on 2010-09-30
Yes it is possible.. You have different option though:
software raid
fake raid (not advisable)
raid

---

### Post by xionhack on 2010-09-30
Thank you! Do you think you can answer my original post?! Nobody has been able to answer it! Thank you!

---

### Post by SeijiSensei on 2010-09-30
You have two choices for RAID -- hardware or software.  (Actually in Linux you could have both, but let's leave that for another day.)  Hardware RAID is easier because the drive array appears like a single device to the operating system.  On the other hand, if something goes wrong it's harder to diagnose since it's all happening in the adapter.

Linux enables you to create RAID arrays of any type using software written into the operating system kernel.  Suppose you had a machine with four identical drives.  You could make them all into a RAID5 array, or make three of them into RAID5 and reserve the fourth for operating system images. You'll want to make sure that you use RAIDed partitions for at least /var and /home, if not for the entire operating system itself. 

You also have the option of using something called LVM which essentially creates virtual disk drives that can be restructured on-the-fly in many situations.  LVM also enables you to take snapshots of the virtual disks which can make restoring from backup much easier.  LVM can be run on top of a RAID array giving you a powerful combination of reliability and flexibility.

However if the data are as sensitive as you suggest, you'll probably need some type of encrypted disk partitions as well.  

Before you embark on this project, I'd create a [VirtualBox]("http://www.virtualbox.org/") virtual machine on a Windows or Linux host, install a copy of Ubuntu Server, and develop your application there.  I think you should also consider [CentOS]("http://www.centos.org/") 5.5 as a server platform; it's the free re-spin of Red Hat Enterprise Linux.

As for the hardware, something like the [Dell T310]("http://www.dell.com/us/business/p/poweredge-t310/fs") should have all the horsepower you'd need.  (I have no affilation with Dell other than as a customer.)  Get at least 4GB of memory.  You should also consider whether to invest in "hot-swap" hard drives, which can be replaced without downing the server, but are more expensive compared to cabled drives inside the server box itself.

---

### Post by xionhack on 2010-09-30
Hey! thank you for your response! One question, what would be the advantage of centos in front of ubuntu? I'm very new at all this!

Also, does it make any difference in linux if I get a Xeon or an AMD? Is any of them better for linux? thanks!

---

### Post by whoop on 2010-10-04
CentOS is relatively old technology which tends to have the kinks ironed out (at least that's what they say).

Each processor type has it's own advantages/disadvantages, so that really hard to say if one is better over the other. No matter what one says about this, others will disagree:

[http://www.vaultnetworks.com/dedicated-servers/amd-vs-intel.html](http://www.vaultnetworks.com/dedicated-servers/amd-vs-intel.html)

---

### Post by sanlinhtet on 2010-10-12
Hello
Could you help me plz.
I have 160 GB hard drive and two hard drives of 1 TB. Actually , I want to install Ubuntu server 10.04 on 160 GB and two HDD use for DATA store with Mirror backup.
What kind of RAID shout  I use and how to set it up. Now I am using Intel® Desktop Board DP55WG
Product Guide with i3 CPU and 4 GB of RAM.
Please kindly help me...

---

### Post by whoop on 2010-10-12
Raid is not only useful when dealing with broken hard-disk's, it's also useful for uptime and speed... 
I would ditch the 160 GB (don't use it in the machine), and insert both 1 TB disks, then do a software RAID 1, and make three raid array's:
/
home
swap

In this case if a hard disk breaks, you'll save allot of time...
I did do your proposed concept once, I installed the complete OS to one disk, than added two more disk, and moved home to both disks as a raid 1 array:
[http://ubuntuforums.org/showthread.php?t=1165328](http://ubuntuforums.org/showthread.php?t=1165328)

---

### Post by sanlinhtet on 2010-10-12
Thanks for your quick reply, Sir
I hope it will be helpful for me.I will try it at once. But I would like to know about what I want above that is possible or not. Separate OS disk ( Ubuntu Server ) and separate two HDD ( MIRROR) for DATA only. If possible , please let me know how to set it up , and if it is impossible , please let me know " why". Actually , it can say that I am just beginner on Ubuntu server. please kindly help me . I request all of my brothers and sisters and also uncle. take me to your.....
Thank you so much.

---

### Post by whoop on 2010-10-12
> **sanlinhtet said:**
> Thanks for your quick reply, Sir
I hope it will be helpful for me.I will try it at once. But I would like to know about what I want above that is possible or not. Separate OS disk ( Ubuntu Server ) and separate two HDD ( MIRROR) for DATA only. If possible , please let me know how to set it up , and if it is impossible , please let me know " why". Actually , it can say that I am just beginner on Ubuntu server. please kindly help me . I request all of my brothers and sisters and also uncle. take me to your.....
Thank you so much.

Yes, like I said it is possible... It is more like my second example ([http://ubuntuforums.org/showthread.php?t=1165328](http://ubuntuforums.org/showthread.php?t=1165328) ):
/ and swap etc.. on one disk, /home as raid 1 array on the two other disks.

But I still think 3 raid 1 arrays (/, /home and swap) on the two 1 TB disks is a better and safer solution...

---

### Post by sanlinhtet on 2010-10-13
aww,

I would like to say my special thanks to you , sir.

I will follow as your guided me above.

:)

---

### Post by sanlinhtet on 2010-10-16
Dear sir,
I followed as your suggestion as shown above.
After I install ubuntu server 10.04 with that 2 HDD of 1 TB using RAID 1, I tested it that I unplug one of than and boot it up only one HDD and also that rest of one. After that I plugged both of my HDD of 1 TB but  I found the STATE of HDD is like this...

Level : Mirror (RAID-1)
Name : -
State: DEGRADED
Action: Recovering

What's happen it and what the state of HDD is DEGRADED? Is it default or not.
If it is not normal of RAID-1 how can I resolved it. Let me know what does mean of DEGRADED.

Thank you sir,
please help me...

---

### Post by whoop on 2010-10-20
> **sanlinhtet said:**
> Dear sir,
I followed as your suggestion as shown above.
After I install ubuntu server 10.04 with that 2 HDD of 1 TB using RAID 1, I tested it that I unplug one of than and boot it up only one HDD and also that rest of one. After that I plugged both of my HDD of 1 TB but  I found the STATE of HDD is like this...

Level : Mirror (RAID-1)
Name : -
State: DEGRADED
Action: Recovering

What's happen it and what the state of HDD is DEGRADED? Is it default or not.
If it is not normal of RAID-1 how can I resolved it. Let me know what does mean of DEGRADED.

Thank you sir,
please help me...

Well, I don't see that too often but it is probably to be expected when you disable a raid member... degraded basically means the raid array currently is not as it should be. It doesn't mean your data is lost it means you are currently as safe as having a single disk...
Did the problem resolve itself? If not could you post the output of
```

cat /proc/mdstat

```

Maybe we need to do some mdadm add command to add the raid member back to the array, but maybe it is not needed because you stated:"Action: Recovering"

---

