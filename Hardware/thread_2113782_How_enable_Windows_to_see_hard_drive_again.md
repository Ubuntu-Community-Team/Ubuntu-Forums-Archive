---
title: "How enable Windows to see hard drive again?"
date: 2013-02-08
forum: Hardware
---

### Post by Victor Delta on 2013-02-08
I wonder if anyone can help me with this please - even though it involves the W word!?

I had a Windows Vista pc with 2 hard disks - c drive as normal and x drive for data backup etc. Following a crash, Vista would not boot properly (try as I might to repair it) and so I temporarily installed Ubuntu 12.10 to enable me to copy data files etc.

Took the pc to be repaired and, to cut a long story short, repairers disconnected x drive and reloaded Vista onto c drive. Now when x drive is reconnected, you can 'see' it in Windows but not access it in any way (eg via Computer, Manage, Disk Management).

I presume the problem is that the x disk still thinks it's working with ubuntu. So is there any way I can get it to play with Windows again please?

By the way, I must say I like very much what I saw of ubuntu 12.10 - it's changed considerably since I last tried ubuntu. In fact, I'm only returning to Windows because of all the programmes I can currently only run on Windows although am going to investigate Wine further.

Thanks.

---

### Post by cmacia06 on 2013-02-08
I assume you installed ubuntu onto your x drive. When on windows press start key, right click on computer, click manage, there should be a storage section, find your drive, format it to your use. I recomend ntfs for windows.

---

### Post by Victor Delta on 2013-02-08
Thanks but does that mean I won't be able to recover the data there (some was written using Windows and some using ubuntu).

---

### Post by cmacia06 on 2013-02-08
If you installed ubuntu to the x drive then more than likely you had to of formated that hardrive and the data may not be recoverable anymore.

---

### Post by oldfred on 2013-02-08
If you can see your X drive in Windows, was your install really wubi and not a full partitioned install? If so and root.disk is still in your X drive then you may just need to add wubi boot and boot files to Vista.

Windows confuses drives. In LInux a drive is a physical drive, and partitions are subdivisions of the drive. Windows will call a d: drive or x: drive and it can be either another physical drive or just a partition on the same drive.

I do not know wubi, if that is what you have, but some instructions are here:
       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by Victor Delta on 2013-02-10
Thanks. Don't think I'm using Wubi. I just installed ubuntu from an image on a CD.

Wish now that I'd used it in the non-installed mode as I probably would have the problem with the x Drive now!

---

### Post by oldfred on 2013-02-10
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

