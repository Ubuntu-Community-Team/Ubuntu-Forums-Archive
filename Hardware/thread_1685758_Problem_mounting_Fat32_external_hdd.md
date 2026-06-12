---
title: "Problem mounting Fat32 external hdd"
date: 2011-02-11
forum: Hardware
---

### Post by Lash009 on 2011-02-11
Alright, before you read this please realize that I'm an absolute lunix noob; so sorry in advance if I get some terminology wrong.
So yesterday I installed Ubuntu 10.10 onto my new 16Gb flash drive everything went smoothly and the only problem I've encountered so far is I can't access my 1TB Western Digital external hard drive. I've read online that ubuntu can read/write to a fat32 but whenever I go to the disk Utility and try to mount it I get a message that there was an error when trying to mount Partition 1 (the 995GB partition with all my music/videos on). So I'm wondering if I'm doing somthing wrong, or maybe I need to install a driver of some sort? Any help would be appreciated. Thanks.
-Matt
p.s. I won't be able to reply to this thread until 4:30 pm Central (I'll be at school)

---

### Post by ajgreeny on 2011-02-11
Assuming this is a USB external drive, it should mount automatically when plugged in.  With the disk attached run ```
sudo fdisk -l
```(lower case L at end)  in terminal and see if it is detected.  If it is it should be possible to mount it manually if needed, though the question remains as to why it is not mounting itself.  Also run the simple command ```
mount
``` to see if it is already mounted but just not showing in either Places, or on your Desktop.

If it is normally attached when you boot up, try booting with it un-attached then plug it in and see if the system mounts it for you; it should do and if not we must start looking for reasons why not.

---

### Post by Lash009 on 2011-02-11
waiting to plug it in after Ubuntu started worked- I now can read/write to it. Thanks ajgreeny[!]("http://ubuntuforums.org/member.php?u=27747")
Do you have any idea why it didn't work before?

---

### Post by ajgreeny on 2011-02-12
Not in detail, but I think it may be related to the timing of startup of various bits of the OS software at boot time, and the lack of the needed utility at the moment that the system sees the USB disk is attached.  Waiting until the OS is fully up and running means everything is available to mount the disk without a problem.

---

