---
title: "Deleted a Windows partition"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by mavuashire on 2009-07-14
I was trying to reserve some space for installing ubuntu. During the partitioning stage,i accidentally deleted and and formated windows partition to ext3 and left free space at the end.

I want to know if it is possible to recover the data on the deleted partion

---

### Post by imperium2335 on 2009-07-14
Look up ext2ifs, that will let you see the drive in windows. But if you formatted it then you might need to use ext2ifs in conjuction with some kind of undelete software.

I had this fun yesterday except i didnt format it, just couldnt see a ton of my important data after installing ubuntu to test it, at no point was i told it would change the partition type and i wouldnt be able to use my old data.

Now im stuck with a drive full of stuff i cant use because for some reason its read only. mysteries...;)

also you can try some thing called find and mount i think its called, you will need the full version tho so prob a visit to piratebay, or you will stuck with half a mb read/write speed.

---

### Post by aesis05401 on 2009-07-14
I'm sorry that this happened to you.  

To make a long story very short here are your options:

If you performed only a high level format on the drive then the essential information from your NTFS partition is still there.  NTFS backs up data address information at the end of the boot partition, and this information can be recovered and restored.

If you performed a low level format then you are probably out of luck. 

Unfortunately, I have a license to a proprietary product for doing NTFS recovery, and I have never done one manually.  I can tell you that there is a lot of info out there on the open nets about recovering NTFS partitions. 

If you decide it is worth the effort I think 'findntfs' is a freeware program that runs in a DOS shell that will attempt to locate the backup files, but I can't vouch for the effectiveness of the program.

---

### Post by mavuashire on 2009-07-14
I have not gone on with ubuntu installation. And as it stands I have lost windows OS. So will ext2ifs and findntfs require me to have an OS installed and if so which.

How can I also make sure that in installing the OS I don't destroy the files I want to recover.

---

### Post by aesis05401 on 2009-07-14
> **mavuashire said:**
> I have not gone on with ubuntu installation. And as it stands I have lost windows OS. So will ext2ifs and findntfs require me to have an OS installed and if so which.

How can I also make sure that in installing the OS I don't destroy the files I want to recover.

You don't want to write anything to the disk at all.  

If you are going to try findntfs you should download a freedos live cd and boot off that.  This might take some research, though, to make sure that findntfs will operate under freedos.  

Again, I don't have any experience using freedos or findntfs because I receive licenses to other products through my business partner. 

Hope this helps in some manner.

---

### Post by merlinus on 2009-07-15
testdisk and photorec are excellent at recovering deleted partitions and files.

---

### Post by mavuashire on 2009-07-15
How do I run testdisk from a live cd

---

