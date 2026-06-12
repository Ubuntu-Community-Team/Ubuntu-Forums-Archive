---
title: "VERY LARGE disk, how to format?"
date: 2022-12-13
forum: Hardware
---

### Post by sgodoyc on 2022-12-13
Greetings,

I bought a portable SSD (PSSD) with 16Tb capacity, and connects via USB to the system, but have not been able to create a partition and format.
Aparently the system cannot understand the structure of the disk, maybe because of its size.  

Neither  GParted nor KPartition are able to create and format a single global partition.

I'm using Ubuntu 22.04.1 LTS

Can anyone suggest a course of action?
Do I need some specialized file-system like Lustre?

Thanks in advance.

---

### Post by QIII on 2022-12-13
Who is the manufacturer and what is the model?

Use GPT an see if you can create one partition at 2 Tebibytes first.  I think that is GParted's limit, but I could be mistaken.  That might be for a MBR.

---

### Post by Doug S on 2022-12-13
Earlier this year I did a 8TB internal disk. I only used the fdisk command and [this]("https://www.tecmint.com/fdisk-commands-to-manage-linux-disk-partitions/") reference to create one huge partition. Then I used "mkfs.ext4 /dev/sdb1" to format it. Then I used "/usr/sbin/tune2fs -m 1 /dev/sdb1" to change the default 5% privileged processes reserved space to 1%. If things are different for a USB drive, I do not know.

```
$ df -H
Filesystem      Size  Used Avail Use% Mounted on
udev            8.3G     0  8.3G   0% /dev
tmpfs           1.7G  4.9M  1.7G   1% /run
/dev/sda1       967G  160G  759G  18% /
tmpfs           8.3G   32M  8.3G   1% /dev/shm
tmpfs           5.3M     0  5.3M   0% /run/lock
tmpfs           1.7G     0  1.7G   0% /run/user/1000
[COLOR="#FF0000"]/dev/sdb1       8.0T  4.1T  3.9T  52% /media/tcpdump-drive[/COLOR]
```

---

### Post by sgodoyc on 2022-12-13
> **QIII said:**
> Who is the manufacturer and what is the model?

Use GPT an see if you can create one partition at 2 Tebibytes first.  I think that is GParted's limit, but I could be mistaken.  That might be for a MBR.


That may be so, because I tried a 4 Tb partition and also failed...
I will try 2 Tb...

In case the test succeds Does it mean there is no way to create larger partitions?

---

### Post by sgodoyc on 2022-12-13
> **Doug S said:**
> Earlier this year I did a 8TB internal disk. I only used the fdisk command and [this]("https://www.tecmint.com/fdisk-commands-to-manage-linux-disk-partitions/") reference to create one huge partition. Then I used "mkfs.ext4 /dev/sdb1" to format it. Then I used "/usr/sbin/tune2fs -m 1 /dev/sdb1" to change the default 5% privileged processes reserved space to 1%. If things are different for a USB drive, I do not know.


I am checking the reference you gave.
It seems GParted issues precisely an fdisk command when reporting the error. I will verify its parameters...

---

### Post by TheFu on 2022-12-14
I have a very hard time believing that a non-enterprise user would spend to get 16TB SSD.  If you paid less than US$1000, it is a fake, which would explain the issues.  These fakes were more common last year.  Typically, they'd have 1TB in cheap USB flash storage and a controller that lied about the total storage.  
[https://forums.tomshardware.com/threads/buyer-beware-16tb-or-larger-external-portable-ssd-usb-drives-are-fake.3773032/](https://forums.tomshardware.com/threads/buyer-beware-16tb-or-larger-external-portable-ssd-usb-drives-are-fake.3773032/)
[https://www.techradar.com/news/this-fake-16tb-external-ssd-is-amazons-best-selling-new-storage-release-just-dont-buy-it](https://www.techradar.com/news/this-fake-16tb-external-ssd-is-amazons-best-selling-new-storage-release-just-dont-buy-it)

The cheapest 16TB HDD, not SSD, is $270. [https://edwardbetts.com/price_per_tb/](https://edwardbetts.com/price_per_tb/)  It is from Toshiba.

A cheap 4TB SSD is $250 (Crucial).  Corsair is $500 and WD 4TB SSDs are even more. These are NVMe.

---

### Post by QIII on 2022-12-14
Holy cow!  I completely glossed over "SSD".

Definitely.  What TheFu said.

---

### Post by sgodoyc on 2022-12-14
Ok, I get it.  It is possible that my PSSD is really a fake.

Does that mean there is no way to make it work with maybe less capacity?

:(

---

### Post by TheFu on 2022-12-14
> **sgodoyc said:**
> Ok, I get it.  It is possible that my PSSD is really a fake.

Does that mean there is no way to make it work with maybe less capacity?

:(

How would we know?  You haven't provided any detailed information.  Where you got it?  What is the brand?  There are just a few reputable SSD chip makers in the world.  Anything else is a fake.  You might be able to return the device quickly and get your money back, assuming you bought it from a reputable location.  It isn't like you bought it on a street corner, right?  If you can't get your money back, you've learned a valuable lesson for the rest of your life, probably pretty cheap as far as life lessons go.  Open up the box, look inside, see what is really there. I bet is a few flash devices, probably really cheap, no-name. They probably used hot-glue to prevent rattling inside the case, so you can't get to the flash storage and use it like a $10 USB flash drive either.

How much is your data worth?  If it doesn't matter at all, go for it.  If it does, it is probably worth the honest cost of a 16TB HDD and you don't want just 1 device like that - you'd need at least 2 (2nd for backups).

---

### Post by sgodoyc on 2022-12-14
:frown:  ](*,)

---

### Post by Doug S on 2022-12-14
> **QIII said:**
> Holy cow!  I completely glossed over "SSD".

Definitely.  What TheFu said.So did I. My example 8TB drive was a HDD.

---

### Post by Doug S on 2022-12-14
> **TheFu said:**
> How much is your data worth?  If it doesn't matter at all, go for it.  If it does, it is probably worth the honest cost of a 16TB HDD and you don't want just 1 device like that - you'd need at least 2 (2nd for backups).Agree. In my case, the data on the 8TB drive is disposable and outside of my backup routine.

---

### Post by Tadaen_Sylvermane on 2022-12-14
Found this. May help if it's accurate. I don't know.

[https://uefi.org/sites/default/files/resources/UEFI_Drive_Partition_Limits_Fact_Sheet.pdf](https://uefi.org/sites/default/files/resources/UEFI_Drive_Partition_Limits_Fact_Sheet.pdf)

---

### Post by TheFu on 2022-12-15
> **sgodoyc said:**
> :frown:  ](*,)

Search youtube for "fake pssd" and you'll see why you don't want to put any data on it.

If you paid $26 for the device, you should know that at least 1 of the YT people opened their device and found about $2 worth of stuff inside.  The metal case and USB3 cable was worth more than the microSD and USB converter inside it.

In short, you've been taken, had, ripped off.  I'd be surprised if the microSD inside has more than 4MB (not GB) of storage. Regardless, don't trust it.

If $26 is all it takes to learn this lesson, you've gotten off cheap.  Some people have to lose $5000+ to learn the same lesson.

---

### Post by mIk3_08 on 2022-12-16
> **sgodoyc said:**
> Greetings,

I bought a portable SSD (PSSD) with 16Tb capacity, and connects via USB to the system, but have not been able to create a partition and format.
Aparently the system cannot understand the structure of the disk, maybe because of its size.  

Neither  GParted nor KPartition are able to create and format a single global partition.

I'm using Ubuntu 22.04.1 LTS

Can anyone suggest a course of action?
Do I need some specialized file-system like Lustre?

Thanks in advance.
For me I simply use Disks App. It actually help me. I haven't encounter any problem using this app. Regards and cheers.

---

### Post by mikewhatever on 2022-12-16
It probably looks something like this: [https://arstechnica.com/gadgets/2022/08/walmart-lists-a-30tb-portable-ssd-for-39-it-is-naturally-a-scam/](https://arstechnica.com/gadgets/2022/08/walmart-lists-a-30tb-portable-ssd-for-39-it-is-naturally-a-scam/)

---

### Post by mIk3_08 on 2022-12-16
> **sgodoyc said:**
> That may be so, because I tried a 4 Tb partition and also failed...
I will try 2 Tb...
In case the test succeds Does it mean there is no way to create larger partitions?

> **sgodoyc said:**
> Ok, I get it.  It is possible that my PSSD is really a fake.
Does that mean there is no way to make it work with maybe less capacity?
[IMG]https://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]

> **mikewhatever said:**
> It probably looks something like this: [https://arstechnica.com/gadgets/2022/08/walmart-lists-a-30tb-portable-ssd-for-39-it-is-naturally-a-scam/](https://arstechnica.com/gadgets/2022/08/walmart-lists-a-30tb-portable-ssd-for-39-it-is-naturally-a-scam/) 
oh. poor disks. sgodoyc, you might be a victim of this scammers. I prefer to choose a store where I can guarantee for a return when I encounter inconvenience of using their products to prevent from this scammers.

---

