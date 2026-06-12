---
title: "No user rights on Vista personal folders in Ubuntu"
date: 2008-07-18
forum: General Help
---

### Post by waltervos on 2008-07-18
Hello,

I tried asking this question on the Dutch Ubuntu forum but it seems nobody could figure it out. I'm hoping the international community may know a solution to my problem. The situation is as follows:

I have both Windows Vista and Ubuntu installed on the same system. The original plan was to make relatively small partitions for both of the OS's as I don't need a lot of space and than have two FAT32 partitions that can be used in both the OS's (there's two because they're over two hard disks). 

What I did was create folders on one of the FAT32 partitions that correspond to the personal folders of Ubuntu and Vista: Documents, Pictures, Video, Downloads, etcetera. I then made symlinks from the corresponding home directories in Ubuntu to these folders (like ln -s /X2/Walter/Documents /home/waltervos) and did basically the same in Windows Vista (change the location of the folder) There's also a TEMP folder on the FAT32 partition that is not linked in Vista because Vista only lets you link personal folders and not just any folder. All of this seemed to be working great but there's one problem. 

The folders that are linked in Vista are read only for users and can only be written to by root. I mounted the FAT32 partitions in fstab with a umask of 000 and some other options that should work. The TEMP folder does have read write access for all users (as it should with a umask of 000). The question now is: 'how do I make the other folder writeable by normal users as well?'.

Here's the section in my fstab file that relates to the FAT32 partitions:

/dev/sda3 /X1 	vfat 	iocharset=utf8,rw,noatime,user,umask=000 0 0
/dev/sdb1 /X2 	vfat 	iocharset=utf8,rw,noatime,user,umask=000 0 0

If any extra info is needed just ask and I'll look it up. Thanks in advance for all your help.

---

### Post by coffeecat on 2008-07-18
I think you need to add 'UID=1000" or whatever your uid is to the list of mount options. I'm doing this from memory so I can't remember whether that's UID= or uid= or whether it matters.

I'll bootup with my laptop later where I've got a shared fat32 partition, check what fstab says in that and post back if necessary.

---

### Post by waltervos on 2008-07-18
Thanks for your response. There's one more user on the system, shouldn't I use gid than (and the id of the users group)? I think I've tried that already but I can give it a go.

---

### Post by coffeecat on 2008-07-18
> **waltervos said:**
> There's one more user on the system

That does complicate things. That UID=1000 is my memory of a long-dismantled machine. On my laptop (with XP, but does that matter?) the Ubuntu installer set up fstab with this line:

```
# /dev/sda5
UUID=6573-109B  /media/Shared_Data vfat    utf8,umask=007,gid=46 0       1
```and that works OK. I can't work out which group 46 is, and the battery is about to run out - I'm posting from the laptop. That might get around the multiple users problem.

By the way, my only experience in multi-booting with Windows is with XP. I know you're using Vista, but this looks to be a Linux issue. Unless I'm missing something.

**Edit:** I *think* group 46 is plugdev. Goodness me, that users and groups 'utility' under System > Administration needs some work. It doesn't even admit the existence of plugdev, but 'groups' from a terminal tells me I'm a member of it. :roll:

---

### Post by waltervos on 2008-07-18
> **coffeecat said:**
> That does complicate things. That UID=1000 is my memory of a long-dismantled machine. On my laptop (with XP, but does that matter?) the Ubuntu installer set up fstab with this line:

```
# /dev/sda5
UUID=6573-109B  /media/Shared_Data vfat    utf8,umask=007,gid=46 0       1
```and that works OK. I can't work out which group 46 is, and the battery is about to run out - I'm posting from the laptop. That might get around the multiple users problem.

By the way, my only experience in multi-booting with Windows is with XP. I know you're using Vista, but this looks to be a Linux issue. Unless I'm missing something.

I'm starting to think this is a Vista issue (or a Vista/Linux compatibility issue) but I'm not sure. I tried the mount options you shared but they don't work. I don't think the problem is in fstab because other folders on the same partition listen to the fstab rules just fine.. Only the folder that are used as personal folders in Vista don't. Can another OS 'lock' folders for other OS's or something?

---

### Post by waltervos on 2008-07-19
*bump* (I hope that's allowed)

If clarification is needed please let me know. I'd like to stress though that this is not simply a fstab problem. Some folders on the FAT32 partition have the rights that I set in the mount options, others (the ones that are used for personal folders in Vista) don't and are only writeable by root.

I'm starting to think I might need to file a bug report for this. Any thoughts?

---

### Post by waltervos on 2008-07-21
The same problem is [described in this topic]("http://ubuntuforums.org/showthread.php?t=617481"). No solution to this date. Is this a bug?

---

### Post by 4Orbs on 2008-07-21
I had a similar problem with a 2nd HDD as FAT32 and used as common storage between Win XP and Xubuntu. I messed with permissions, fstab and other possible fixes found on the forums, but nothing worked. Finally I found a thread suggesting the installation of the Storage Device Manager. I quickly found the app in synaptic, installed it and within a few minutes it solved the problems I had labored over for more than a week.

---

### Post by waltervos on 2008-07-21
> **4Orbs said:**
> I had a similar problem with a 2nd HDD as FAT32 and used as common storage between Win XP and Xubuntu. I messed with permissions, fstab and other possible fixes found on the forums, but nothing worked. Finally I found a thread suggesting the installation of the Storage Device Manager. I quickly found the app in synaptic, installed it and within a few minutes it solved the problems I had labored over for more than a week.

Thanks 40rbs, but how exactly did you use this app to fix your problem? To me it looks like it's simply a gui for fstab (with a few bugs as well).

---

### Post by 4Orbs on 2008-07-21
Hello waltervos. My initial problem was not with permissions so much but rather with auto mounting of the fat32 hdd at boot. I am into Linux only 4 months now, so my advice may not be worth the virtual paper its written on. My first install was with the standard Ubuntu Hardy, and the hdd would auto mount as expected upon boot up. But no matter what I tried I could not change the permissions for anything beyond root access. Then I did a fresh install of Xubuntu to replace the standard Ubuntu install and the vfat hdd would not auto mount anymore. That is when I installed the Storage Device Manager. I created a new folder (as root user) in the system media folder and assigned it as the mount point for the fat32 hdd. After configuring the hdd properties with Storage Device Manager, I was able to change permissions of the new folder (mount point) to allow read and write access for all users (listed as Other in the folder permissions UI and accessed by right clicking the folder as root user and selecting Properties). For what its worth, the Storage Device Manager shows a umask value of 0 for that folder rather than 000. Sorry for my lack of expertise, but I consider the Storage Device Manager to be the element that fixed things for me. I suppose its possible that the different file managers, Nautilus vs. Thunar, might have had some influence on the outcome.

---

### Post by Potatoj316 on 2008-07-21
Could chown be used to change the owner?

---

### Post by Aristocrates on 2008-08-08
I have the same issue.  From the sounds of it, a bug needs to be filed.  I don't see what can be done though.  It's obviously Vista which is locking it and giving it an owner group that doesn't even exist in my linux (plugdev).

I'm only a newbie so I have no idea what to do! Should I reformat the partition as ntfs or does that not work either?

---

### Post by waltervos on 2008-08-12
I´ve written a blog post about this problem with a solution. So go here to read [how to use a FAT32 partition for your personal folders in Vista and Ubuntu]("http://www.waltervos.com/news/shared-personal-folders-vista-ubuntu-permissions/"). I hope this solves the problem for you.

---

