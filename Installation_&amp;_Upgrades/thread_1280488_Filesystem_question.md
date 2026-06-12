---
title: "Filesystem question"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by AmiableAdder on 2009-10-02
The hard drive in my Dell crapped out so I don't have Ubuntu any more, but this time I want to keep Vista until I can get games working in Ubuntu (last time I just deleted Vista completely).

I made a 27Gb partition for it and it says "Unallocated" (which I understand), but when I go to actually create the volume, the only options I have for filesystem types are NTFS and FAT32.

Does it have to be Linux Ext3/2/4 before I install Ubuntu for it to work correctly? Or can I just make the partition an NTFS and Ubuntu will automatically format it when I install Ubuntu? OR can I just leave it Unallocated and Ubuntu will automatically format it when I install it (I don't think that would work because the partition hasn't been created yet. It's just blank space)?

---

### Post by pawhtiobo on 2009-10-02
> **AmiableAdder said:**
> The hard drive in my Dell crapped out so I don't have Ubuntu any more, but this time I want to keep Vista until I can get games working in Ubuntu (last time I just deleted Vista completely).

I made a 27Gb partition for it and it says "Unallocated" (which I understand), but when I go to actually create the volume, the only options I have for filesystem types are NTFS and FAT32.

Does it have to be Linux Ext3/2/4 before I install Ubuntu for it to work correctly? Or can I just make the partition an NTFS and Ubuntu will automatically format it when I install Ubuntu? OR can I just leave it Unallocated and Ubuntu will automatically format it when I install it (I don't think that would work because the partition hasn't been created yet. It's just blank space)?

Hi :)

After the setup of Ubuntu starts, you will be prompt to choose the way to partition your HD, just choose the last option "**Manual**", there you can delete, format, resize  your partitions, it does matter what kind of space you have (NTFS, Unllocated), you can change it as you want, remember that at least you need to have a **swap partition** and one for the OS the **/** mount point. 

See ya...

---

### Post by dvlchd3 on 2009-10-02
If you already have Vista installed, you can just install Ubuntu, and have it use the "Unallocated" space.  It will format that partion as Ext3.  (I believe the option while installing is use largest continous free space, or something like that.)

---

### Post by thomasboleyn on 2009-10-02
> **dvlchd3 said:**
> If you already have Vista installed, you can just install Ubuntu, and have it use the "Unallocated" space.  It will format that partion as Ext3.  (I believe the option while installing is use largest continous free space, or something like that.)

That's correct, I just did that with Karmic beta alongside Jaunty.

---

### Post by AmiableAdder on 2009-10-02
Alright thank you.   :P

---

