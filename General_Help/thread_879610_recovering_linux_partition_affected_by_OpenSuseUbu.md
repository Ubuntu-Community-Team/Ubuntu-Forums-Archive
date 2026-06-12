---
title: "recovering linux partition affected by OpenSuse/Ubuntu conflict"
date: 2008-08-04
forum: General Help
---

### Post by afrodeity on 2008-08-04
Okay, I know this is sign of a troubled mind, but I've been exploring the world of linux thanks to ubuntu. A month ago, my hardrive was 100% Windows XP. Then a friend brought around an ubuntu 64bit disk. I installed it on the 200gig drive. It created a partition sda5 and sda6.

As a result of this I through caution to the wind. I went and partitioned the secondary partition into four pieces. sda7, sda8 and sda9. It all seemed to work. Okay, there was now competition for my bootsector. I installed Linux mint which has a great bootloader and startup screen. It stole the root away from Ubuntu Hardy and gave me grub control of the entire machine. All good and fine.

I installed ubuntu studio onto sda8 and was busy figuring out how to reconcile the video modes (there is no compatability mode or video safe mode as in Ubuntu Hardy and Mint installers).


Then I got sidetracked by the thought of global domination and creating a supercomputer array on my small Celeron. Last night I installed openSuSe into sda9. Yes I know this is bad. It took the root away from Linux Mint, put a plain green start screen in front of the Mint and promised me a better bootloader interface. For a while I actually enjoyed the newness of owning a chameleon.

I played around with the settings, in particular a piece of software called LVM. Merely starting it, it proposed a system. With three clicks I consolidated sda5, sda7 and sda8 into a constellation. No warnings,no explanations of the consequences.

Here is what happened: sda5, sda7 and sda8 are no longer primary partitions, they have become logical volumes (according to testdisk. This has the result that -

the filing system has changed!!!!. I can no longer mount any of the above partitions. The data is unaccessible even via P-Magic. The partitions are still listed as being there, but the filing system is not where its supposed to be.

From trawling the inet it could be something to do with RAID. I have a sata hdd, and there is probably RAID somewhere, although have no idea how this works.

How do I get out of this sticky mess without reformating the partitions? The only partitions that work are of course, the first partion where most of my data is safely tucked behind a Windows XP firewall, and sda9 with an ugly looking chameleon.

It would seem there is a thriving business on the net selling linux recovery tools which I can't afford.

Please help me.

PS: I have also been installing xubuntu/linux onto a friends smaller x86.

---

### Post by ibuclaw on 2008-08-04
Have you tried mounting the devices from within the Ubuntu LiveCD environment?

[EDIT]
I've just looked it up and it appears that LVM partitions come under it's own folder in the /dev directory.

This should list all LVM partitions.
```
sudo lvscan
```
This should list all active LVM partitions.
```
sudo vgscan
```
To mount them, should be no different than a normal mount. You just need to specify a different /dev location.
ie:
```
mount /dev/**lvmgroupname**/sd9 /media/sda9
```
The difference is the LVM sub-directory name, which will be entitled by the name of the LVM group.

Also, to note, you will require lvm2 to do this.

Regards
Iain

---

### Post by afrodeity on 2008-08-04
Believe it or not, I gave the LiveCD away to a unionist who might just put it on his laptop. I'll have to steal it back from him. Isn't there a simple way of recovering the partition? Free tool you could recommend? If I had backed up the MBR would this be an instance in which to install the backup?

---

### Post by afrodeity on 2008-08-04
..and I should then be able to boot off them hopefully? Will give this a go, seems logical. Later. thanks.

---

