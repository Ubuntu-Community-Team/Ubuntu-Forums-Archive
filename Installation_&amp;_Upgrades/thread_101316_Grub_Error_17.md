---
title: "Grub Error 17"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by ninocass on 2005-12-09
Hi all i had Ubuntu installed on my Dell Inspiron 6000.

the 40GM hard drive was split into:

1: Windows XP - NTFS   - 30GB
2: Ubuntu - Lnx2 (cant remember what it was called) -  5GB
3: Storage - FAT32 - 5GB

I started to get the hang of linux and decided id split the HDD 50/50  so i did the following:

* Reduced the XP partition to 20GB
* Increased the Ubuntu Partiton to around 10GB
* Increased the Fat32 to around 10GB

When i start the laptop upt i get the folloing error:
```

GRUB Loading Stage 1.5
Grub Loading, please Wait.....
Error 17

```

The question is how the hell do i fix this?

I have installed a lot of things on linux/windows and id like to be able to keep the setups that i have so is there a way to fix this problem without formatting the whole thing?

Thanks

Nino

---

### Post by amohanty on 2005-12-09
From the GRUB manual @ [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

So I would venture that something went wrong with your re-partitioning effort. What did you use to do it?

The easiest way to fix it would be to regenerate the partition tables. So pop in the install CD and proceed till you are presented with the partitioning options. There choose the manual partitioning option and reassign the mount points to the existing partitions. However _do not_ check the format partition option. 

Better yet follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=76652&highlight=grub+restore+howto](http://ubuntuforums.org/showthread.php?t=76652&highlight=grub+restore+howto)

HTH

---

### Post by ninocass on 2005-12-09
Hi many thakns for your reply, ive managed to get Ubuntu + windows XP working

*wipes sweat from brow!!!!!*  There was a university project in there that ive been working on for a few weeks!!!!!!!

I am partitioning using Partition magic, it got an error part of the way through im assuming it was this that messed GRUB, is there any specific way i should go about increaing the Linux partition size?

Thanks

Nino

---

### Post by amohanty on 2005-12-09
The ubuntu installer can also do it for you, unfortunately I have had mixed results playing around with it. Partition magic should have done it properly, if you get an error there, the best approach is to figure out what the problem is, fix it and redo it.

HTH

---

### Post by ninocass on 2005-12-09
there were 2 main parts to the partition fun, editing the windows and editing the linux.

it seemed when the partition magic was doing its errrr magic, it managed the windows part ok but stumbled on the linux once i was able to boot on XP i was able to finish the linux changes without the need for a reboot and all was well :)

---

### Post by redgilda on 2005-12-10
[QUOTE=amohanty]The easiest way to fix it would be to regenerate the partition tables. So pop in the install CD and proceed till you are presented with the partitioning options. There choose the manual partitioning option and reassign the mount points to the existing partitions. However _do not_ check the format partition option. 

Better yet follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=76652&highlight=grub+restore+howto](http://ubuntuforums.org/showthread.php?t=76652&highlight=grub+restore+howto)
[/QUOTE]

hey there, unfortunately I still get stuck at the error 17 screen... :/ its my first time trying Linux and I'm not even good with computers so have patience with me pls :)

this I can do:

[i]1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition[/i]

however here: 

[i]4. Mount your appropriate linux partions

/
/boot
swap
..... [/i]

is where I apparently have problems.. I understand the only bootable device needs to be the linux partition right? right. 

the linux partition must be set to "/" right?
what about the windows one? can it stay at whatever path there is by default? or does it need to be set to "/" too?
and should I set one of the partitions to "/boot"?

I do get errors in the end, I was managed to finish the installation but the error remained.. tried reinstalling the GRUB, also with same result.. now I'm thinking of reinstalling linux again, as this way I can't get neither linux nor win xp to load :/

if anyone has any suggestions, im open :)

---

### Post by redgilda on 2005-12-10
if anyone wants to help, heres the mess i have in my partitions:

#1 primary 10 GB ntfs /media/hda1   ---- thats my windows
#6 logical 11 GB fat32 /media/hda6  ---- thats what got created on the way:p
#5 logical 116 GB ntfs /media/hda5  --- this id like to keep intact :)
#7 logical 13 GB fat32 /media/hda7  --- this also got created, was free space before for some reason; never used it before
#8 logical 575 MB swap swap
#3 primary 12 GB ext3 /   --- my linux

could this be that i have too many partitions? or it should work either way? any suggestions appreciated... i cant find my win xp cd so i cant even just go back to windows... ill keep looking though, but my flat is a mess :/

---

### Post by redgilda on 2005-12-10
ok as usual, i found a solution right after posting about my problems...  *grin* it always happens 
/random/ im stuck at sth, i read, i google, i try, i give up and decided to post/email for help and boom, right after that I find the solution myself:D /random/

anyway, this additional 20 sth MB of space was disabled for a reason apparently :) just after I disabled the additional partitions, reinstalled linux again clean and poof, no more error 17 anymore.. so now i was able to load up Ubuntu and it's installing some other things :) 

hope my beginner's luck will stay with me ;) how could I have been so dumb grr, i wasted so many hours because I created that additional partition.. *slaps self*

---

### Post by Ptero-4 on 2005-12-10
you should delete partition number 6 and 7, if the partition number 5 is between them move it to join the two chunks of free space, then resize your partition number 5 to use that newly made free space. and mark the partition number 3 as bootable. As for your windoze partition and the partition number 5, assign them mount points like /media/Windoze and /media/Extra but DON'T assign "/" to any one of those. "/" is reserved for the partition containing your linux system (the linux equivalent of the "Windows" folder), and using it in another partition will render your system unbootable.

---

### Post by Falchion on 2005-12-12
[QUOTE=amohanty]From the GRUB manual @ 
Better yet follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=76652&highlight=grub+restore+howto](http://ubuntuforums.org/showthread.php?t=76652&highlight=grub+restore+howto)

HTH[/QUOTE]

I would just like to say thanks for the link above. It helped solve my error 17 problem. Stupid how I was staring at the partitioner for a few minutes, knowning that the problem can be fixed there. But then giving up and heading for the forums. After reading that thread, I got back to the partitioner and Blam!, I spot that somehow the partition that I have Ubuntu installed on was changed from "/" to "/home".Just a quick change back. Reinstall grub and was good to go. Many thanks again.

In case anybody would like to know, my error 17 problem came about after I deleted a logical extended partition in WinXP and then re-created it again to make use of some unused free space left on that drive. Of course this partition is on the same drive that I got WinXp, Ubuntu and "/swap" installed on as well.

However in my hase, I formatted that partition in NTFS and then moved all my old files back on there, when actually I wanted it to be in FAT32 so that both WinXp and Ubuntu and read/write to it. So now I got to copy everything off it again, delete partition, re-partition, move files back again and most likely fix the grub error 17 that is sure to reapear again. 
Joy.

---

