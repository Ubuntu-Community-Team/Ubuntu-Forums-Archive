---
title: "ERROR 18, need help desperaely."
date: 2008-07-19
forum: General Help
---

### Post by Thyssenkrupp on 2008-07-19
Ok, so 2 days ago, i bought a BIOSTAR GF7050-M7 Motherboard, complete with 2 GB DDR2 RAM + an Intel 4.0 GHz Dual core pentium 4 CPU.

Anyways, i can boot from disc, and ubuntu runs fine, ive even stooped as low as to use XP, but that doesnt work.

So, ive installed Ubuntu 8.04 but whenever i boot from my Harddrive i get this message:

GRUB loading, please wait...

ERROR 18

Does anyone know how to resolve this??

Thanks,

Jak

---

### Post by AgentZ86 on 2008-07-19
> **Thyssenkrupp said:**
> Ok, so 2 days ago, i bought a BIOSTAR GF7050-M7 Motherboard, complete with 2 GB DDR2 RAM + an Intel 4.0 GHz Dual core pentium 4 CPU.

Anyways, i can boot from disc, and ubuntu runs fine, ive even stooped as low as to use XP, but that doesnt work.

So, ive installed Ubuntu 8.04 but whenever i boot from my Harddrive i get this message:

GRUB loading, please wait...

ERROR 18

Does anyone know how to resolve this??

Thanks,

Jak

So if you have error loading both Ubuntu and HP, I would suggest this is a memory error or some type or incompatibility of memory.

I'm not sure but I had a few machines act funny like this when loading both ubuntu then trying windows also and got strange blue screen when loading windows that said things like could not copy ??.dll or something so I thought at first it was the CD or the CD drive I've changed all those things and in a long process changed the new memory I had in there and tried some old memory sticks I had laying around and everything worked fine.
I don't know if that is the problem but when strange things happen I start suspecting memory and hard drive.

When you installed Ubuntu did you use guided full hard drive or manually made the partitions etc. ?

I'm not sure it would make a difference to change things around.

Also would be nice to know if you are trying to make a dual boot system or just one OS on one disk ?

Please advise
Thanks

---

### Post by Thyssenkrupp on 2008-07-19
Thanks for the reply,

Yeh i am getting my HDD wiped ASAP to see if that is the problem, and the memory was the one upplied with the motherboard so i doubt its that.

Im pretty sure it is the HDD now, and im not dual booting but im running XP inside Ubuntu, using VMWare.

---

### Post by songshu on 2008-07-19
seems it is a limitation in the BIOS looking at the error message.

solution would be to partition with a small separate /boot partition
100MB for /boot would normally be enough in my experience
 
```

 Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot. 
```

---

### Post by Thyssenkrupp on 2008-07-19
Ahhh, i see!

So can i make that using the live CD partitioner??

Thankyou

Jak

---

### Post by songshu on 2008-07-19
yes,

not sure what its called but something like "manual partitioning" or something

i usually do 
10GB for /root
rest for /home (just in case i would need to reinstall)
1GB for SWAP

but in this case you can add 100MB for /boot 
*edit* you would have to place /boot as the first partition i think


you can put every part of the system on its own partition if you would want to do so.

---

### Post by AgentZ86 on 2008-07-19
Once I had this problem and just booted to Gparted live CD and then right click on the partition and check partition and it repaired and fixed the partition file system by itself, then I just booted normally and everything was fixed.

Not sure if that could help anything but it was simple to do if you can access a copy of Gparted live CD

I hope this can help.


> **songshu said:**
> yes,

not sure what its called but something like "manual partitioning" or something

i usually do 
10GB for /root
rest for /home (just in case i would need to reinstall)
1GB for SWAP

but in this case you can add 100MB for /boot 
*edit* you would have to place /boot as the first partition i think


you can put every part of the system on its own partition if you would want to do so.

---

