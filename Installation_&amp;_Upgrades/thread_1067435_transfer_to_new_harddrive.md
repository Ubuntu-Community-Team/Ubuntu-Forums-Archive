---
title: "transfer to new harddrive"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by ayu on 2009-02-11
Hi,

I would like to transfer my existing installation to a new larger harddrive. Initially, I installed ubuntu to exist with windows and dell recovery/media direct. So, according to gparted, my harddrive currently looks like:

/dev/sda1 - not sure, 70 MB
/dev/sda2 - Dell recovery
/dev/sda3 - Windows, flags: boot
/dev/sda4 - extended, flags: lba
__/dev/sda6 - swap
__/dev/sda7 - /
__/dev/sda8 - /home
__/dev/sda5 - Mediadirect

1. If I just do dd, would there just be some unallocated space at the end, and I could format and use it? Would the MBR be maintained, or do I have to rerun grub?

2. Is my MBR currently in sda3? What is the "boot" flag? Is sda1 important?

3. If I have to run grub, would I still be able to boot into windows, mediadirect, and the recovery partitions if necessary?

4. Ideally, I would like to use gparted to move / to the beginning of the new harddrive, extend /home to fill up the rest of the additional space, and leave the rest of the partitions at the end. Would there be any trouble copying partitions since the last 4 are "extended" partitions? Is it easy to extend /home to fill the rest?

5. Can I use this chance to reduce the file fragmentation? Would I do that by simply copying files instead of copying the partition?

Thank you very much,
Ayu

---

### Post by logos34 on 2009-02-12
1. 
This will copy the entire disk *including* the MBR:
> 
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD)

Cloning an entire hard disk:

dd if=/dev/sda of=/dev/sdb conv=notrunc,noerror

In this example, sda is the source. sdb is the target. Do not reverse the intended source and target. Surprisingly many people do. notrunc means to not truncate. noerror means to keep going if there is an error. Normally dd stops at any error. if you have a question about a hard drive on whether or not it works, you can try to use it as the source drive for the dd command. You should get an error if it is not working. target drives need to be really messed up to give an error in dd.

This will leave you with unallocated space.  Since you have the max number of primary partitions, you will have to use Gparted on the ubuntu live cd to grow sda4 (extended) partition to the end of the disk.  Then make new logical partitions inside.

2. Part of grub (stage1) is on the the mbr of sda, the other part (menu.lst) is on sda7, your / partition). The boot flag is really only needed for windows (i.e. windows bootloader looks for active primary partiton...It's not really necessary if using grub, as long as the windows boot entry in menu.lst has the default 'makeactive' option).  

3. N/A

4. The problem is that you can only have at most 3 primary partitions + 1 extended partition. Either you put / at the front of the disk *inside* the extended, or else eliminate one of the primary partitions.  Frankly, if you want to give the extra space on the larger disk to /home, I'd stay with the current layout, just reorder sda8 last, expand the extended partition to the end of the disk, and grow /home to take up the remaining space.

5.  Run defrag on windows a few times.  No need to worry about linux

---

### Post by ayu on 2009-02-13
Hi,

Thanks, that helped a bit. I'm still a little confused about the last two points. 

First, I hear there is "no need" to defrag in ext3, but of course there would be *some* fragmentation over time. If I'm moving to a new drive, wouldn't copying solid files be better than copying fragmented files? This is a minor issue though, so if there are too many cons then I do not need to do this.

More importantly, is it possible to make /, /home, and swap the primary partitions, and have everything else in the extended partitions? Would windows and the other partitions freak out when I try to boot them and they suddenly see they aren't a primary partition? If I move them around that much, would grub be able to reconstruct everything? (I hope I'm using the right terminology; running grub recreates the boot menu, correct?)

I would like to move / and /home to the beginning of the disk since it will be faster there. I rarely use the windows partition but it is occupying the best part of the harddrive right now.

Thank you very much,
Ayu

---

### Post by tommcd on 2009-02-13
You might want to try the Clonezilla live CD:
[http://clonezilla.org/](http://clonezilla.org/)
[http://clonezilla.org/related-live-cd/001_gparted-clonezilla/more_info.php](http://clonezilla.org/related-live-cd/001_gparted-clonezilla/more_info.php)
Clonezilla was made for this purpose. I have never actually used Clonezilla. I have just read a bit about it. So you will have to read the documentation on how to use it.

---

### Post by ayu on 2009-02-18
> **tommcd said:**
> You might want to try the Clonezilla live CD:
[http://clonezilla.org/](http://clonezilla.org/)
[http://clonezilla.org/related-live-cd/001_gparted-clonezilla/more_info.php](http://clonezilla.org/related-live-cd/001_gparted-clonezilla/more_info.php)
Clonezilla was made for this purpose. I have never actually used Clonezilla. I have just read a bit about it. So you will have to read the documentation on how to use it.

Hm thanks for the suggestion but I think I will stick with gparted. I just hope I am able to change the extended partition to a primary partition. 

Thanks!
Ayu

---

### Post by logos34 on 2009-02-19
> **ayu said:**
> I just hope I am able to change the extended partition to a primary partition. 

If you mean what you described here:

> More importantly, is it possible to make /, /home, and swap the primary partitions, and have everything else in the extended partitions? Would windows and the other partitions freak out when I try to boot them and they suddenly see they aren't a primary partition? If I move them around that much, would grub be able to reconstruct everything? (I hope I'm using the right terminology; running grub recreates the boot menu, correct?)

I would like to move / and /home to the beginning of the disk since it will be faster there. I rarely use the windows partition but it is occupying the best part of the harddrive right now.

I wouldn't--it's a lot of extra work for negligible performance gains.  Besides, windows normally won't boot from a logical partition without additional modifications, so you really should leave your C: partition as primary.  

good luck

---

### Post by tommcd on 2009-02-21
Ayu,
You may be interested in this. It is a video from the Linux Action Show podcast comparing Clonezilla to FOG, a program I have never heard of before:
[http://www.jupiterbroadcasting.com/?p=581](http://www.jupiterbroadcasting.com/?p=581)
And another one on Clonezilla:
[http://www.jupiterbroadcasting.com/?cat=4&paged=2](http://www.jupiterbroadcasting.com/?cat=4&paged=2)

---

### Post by ayu on 2009-02-22
> **logos34 said:**
> If you mean what you described here:


I wouldn't--it's a lot of extra work for negligible performance gains.  Besides, windows normally won't boot from a logical partition without additional modifications, so you really should leave your C: partition as primary.  

good luck

Really? I thought most harddrives were significantly slower at the end compared to the beginning, for example [http://www.tomshardware.com/reviews/notebook-hard-drive,2006-9.html](http://www.tomshardware.com/reviews/notebook-hard-drive,2006-9.html). But thanks for the warning about Windows not booting from logical.


> **tommcd said:**
> Ayu,
You may be interested in this. It is a video from the Linux Action Show podcast comparing Clonezilla to FOG, a program I have never heard of before:
[http://www.jupiterbroadcasting.com/?p=581](http://www.jupiterbroadcasting.com/?p=581)
And another one on Clonezilla:
[http://www.jupiterbroadcasting.com/?cat=4&paged=2](http://www.jupiterbroadcasting.com/?cat=4&paged=2)

Thanks, I will check it out when I have time.

---

### Post by logos34 on 2009-02-22
> **ayu said:**
> Really? I thought most harddrives were significantly slower at the end compared to the beginning, for example [http://www.tomshardware.com/reviews/notebook-hard-drive,2006-9.html](http://www.tomshardware.com/reviews/notebook-hard-drive,2006-9.html). 


Yes, but those are sustained data throughput rates--in everyday use you'll probably not even notice the difference.  Besides, there are other factors at work (ram, filesystem, i/o scheduling, system timer rate, prefetch, indexing, etc.).  But hey, go for it if you want

---

### Post by Mark Phelps on 2009-02-23
> **ayu said:**
> Hi,

3. If I have to run grub, would I still be able to boot into windows, mediadirect, and the recovery partitions if necessary?


Ayu

Realize that your recovery partition is intended to return the machine to the state it was originally, meaning, that it most likely will not only remove all the other partitions, it will restore the original size of the Windows OS partition.

If you really need a way to backup and restore the MS Windows partition, I would recommend a third-party product like Acronis True Image or Paragon Disk Manager.  That way, you will not wipe out anything else if you need to restore your Windows OS.

---

