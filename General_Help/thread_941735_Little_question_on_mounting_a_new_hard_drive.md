---
title: "Little question on mounting a new hard drive"
date: 2008-10-08
forum: General Help
---

### Post by AzizLight on 2008-10-08
Hi everybody,
I just bought a new hard drive for my ubuntu desktop. I found [this really good guide]("https://help.ubuntu.com/community/InstallingANewHardDrive") on how to install and configure the hd. I installed Gparted and the hd is recognized automatically. But before I do anything I would like to know something.
I want to mount the drive in /home/youjiii/ (my home folder is /home/aziz/ - so in the end I would have two folders in /home/ : aziz/ and youjiii/) and I want the drive to be mounted automatically on every boot. But in every guide I've read, the mount point is always /media/[some mount point]/ and the guide recommend to mount under /media/ . I mount all my external hard drives under /media/ but this is an internal hard drive that will get mounted automatically on each boot. So my question is: what is the real difference? Is there a security issue if I mount my hd under /home/ ? What do you suggest I do?

Please keep in my that I will format that hd and use it exclusively with ubuntu, and then I'm going to install a virtual machine and install windows in that (no windows doesn't deserve a capital letter 8) ). So Basically I will only have one partition on that HD.

---

### Post by Titan8990 on 2008-10-08
/media and /mnt are just the standard directory. Essentially, you can mount the drive wherever you please (as long as its not an area used by another partition) and it will not change a thing.

---

### Post by jerome1232 on 2008-10-08
I prefer mounting under /mnt, then creating a symnlink in my home to it, but as Titan8990 said this is purely a standard thing, it's not related to security and mounting elsewhere won't break anything.

Things mounted under /media show up on your desktop while things mounted elswhere don't

---

### Post by AzizLight on 2008-10-08
> **jerome1232 said:**
> 
Things mounted under /media show up on your desktop while things mounted elswhere don't
That's a very good point, I forgot about that...
> **jerome1232 said:**
> I prefer mounting under /mnt, then creating a symnlink in my home to it
...and that's a really good idea. You convinced me :p
Thanks a lot for the help Titan8990 and jerome1232.

---

### Post by WWSmith36 on 2008-10-08
Wherever you decide to mount it.  Just remember that you should update /etc/fstab in order to get it to auto-mount on boot.

---

### Post by AzizLight on 2008-10-08
@WWSmith36: yes I know, thanks for the remark though. I'm following the guide that is in the ubuntu wiki, everything is explained clearly.

...Well almost everything. I am very sorry in advance, I have a very noobish question: I am using Gparted, it's the first time I format the hard drive so there is nothing on it. Gparted asks me to set a disklabel. By default it chose msdos. As I am a noob, msdos sound...will liek MS DOS which is not what I want (right?:confused:). If I click on advanced there is a list of other disklabel. Condidering that I want to extend the space of ubuntu, that I'm going to create one single ext3 partition on that hard disk, which disklabel should I use? Should I use msdos??

(I said I am sorry...)

---

### Post by jerome1232 on 2008-10-08
All of mine are msdos.

---

### Post by Titan8990 on 2008-10-08
The disk label is only for you. It is just one way of distinguishing one drive from another.

---

### Post by AzizLight on 2008-10-08
Ok, thanks a lot for the clarification.

---

