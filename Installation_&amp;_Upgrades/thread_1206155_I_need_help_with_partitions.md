---
title: "I need help with partitions"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by mbux on 2009-07-06
I am trying to install ubuntu 9.04 to dual boot with vista, but I am running into some trouble dealing with hard drive partitions. It is my understanding that you can only have 4 primary partitions, and that I will need at least 2 for ubuntu (swap and "/" or root). The problem is that my computer already has three partitions.

-ntfs C:
-ntfs TOSHIBA SYSTEM VOLUME (I don't know what this is)
-ntfs HDDRECOVERY (recovery stored on hard drive)

Is there any way to combine partitions, or anything like that, so I can make this fit? I have briefly read something about making extended partitions, but nobody went into detail about it.  

Any help is appreciated.

---

### Post by taurus on 2009-07-06
All you need is one primary partition.  You can make that primary partition as an extended partition and then create two logical partitions for Ubuntu, one for / and one for swap.  On the other hand, you don't even have to do that first if you don't want to.  Just tell the installer which primary partition you want to install on and it will take care of creating a two new partitions for you.

---

### Post by overdrank on 2009-07-06
> **mbux said:**
> I am trying to install ubuntu 9.04 to dual boot with vista, but I am running into some trouble dealing with hard drive partitions. It is my understanding that you can only have 4 primary partitions, and that I will need at least 2 for ubuntu (swap and "/" or root). The problem is that my computer already has three partitions.

-ntfs C:
-ntfs TOSHIBA SYSTEM VOLUME (I don't know what this is)
-ntfs HDDRECOVERY (recovery stored on hard drive)

Is there any way to combine partitions, or anything like that, so I can make this fit? I have briefly read something about making extended partitions, but nobody went into detail about it.  

Any help is appreciated.

Hi and when you resize the windows partition then you can select manual partition and create a extended partition then. And this link [Partitioning basics]("http://ubuntuforums.org/showthread.php?t=282018") may help
Edit taurus beat me too it "Run, little guy, run..."

---

### Post by taurus on 2009-07-06
> **overdrank said:**
> 
Edit taurus beat me too it "Run, little guy, run..."

You better run because I am coming after ya, BOOO...

---

### Post by mbux on 2009-07-06
> **taurus said:**
> All you need is one primary partition.  You can make that primary partition as an extended partition and then create two logical partitions for Ubuntu, one for / and one for swap.  On the other hand, you don't even have to do that first if you don't want to.  Just tell the installer which primary partition you want to install on and it will take care of creating a two new partitions for you.

Thanks for quick reply. So if I were to install on the largest unallocated space, a single partition, you are saying it would automatically create swap? Would it let me specify the swap size? Or could I specify its size later?

---

### Post by taurus on 2009-07-06
If you want to specify the swap size, then you need to manually partition your harddrive.

---

### Post by mbux on 2009-07-06
Ok. Well what would it do by default, maybe it would be close enough to what I want.

---

### Post by taurus on 2009-07-06
How much RAM do you have and how much space for swap you have in mind?

---

### Post by mbux on 2009-07-06
I have 4gb RAM and I figured 2gb should be plenty for swap. I have lots of space for it.

---

### Post by taurus on 2009-07-06
With 4GB of RAM, you don't even need 2GB of swap unless you run some big apps.  The default should be more than enough.

---

### Post by mbux on 2009-07-06
Haha, I figured you would say that. I guess I was just being extra cautious. I'll just stick with the defaults. Thanks for the help.

-goes to install-

---

