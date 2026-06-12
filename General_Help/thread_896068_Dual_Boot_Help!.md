---
title: "Dual Boot Help!"
date: 2008-08-20
forum: General Help
---

### Post by Shiv4m on 2008-08-20
Hey guys I want to use Windows XP with Ubuntu, I'm currently running Ubuntu right now, I just wanted a kind of guideline to follow in order to dual boot with Windows XP.

Thank You

---

### Post by tuxxy on 2008-08-20
I would recommend instaling windows onto the drive first, however if not then backup your files as theres always the risk.

You need to shrink the partition of your current XP and then create the new partition for ubuntu, when you install ubuntu make sure you install to the correct new partition.

Heres a guide that maybe useful 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Shiv4m on 2008-08-20
Theres no way to install Windows XP with Linux already installed?

---

### Post by tuxxy on 2008-08-20
Yes you can but it would be easier if windows was installed first, to install windows you need to partition the drives like I explained

---

### Post by Shiv4m on 2008-08-20
I would lose everything I have on ubuntu then :(

---

### Post by tuxxy on 2008-08-20
No you shouldnt lose anything, you need to resize your current ubuntu partition you can do this by booting the install CD and selecting Live CD mode, run the command **gparted ** from a terminal once your in.

Now once you reduced the size of the ubuntu partition you can create another parititon for XP to be installed on.

---

### Post by tuxxy on 2008-08-20
Heres a full guide on this process, it should explain everything.

[http://ubuntuforums.org/showthread.php?p=4567222](http://ubuntuforums.org/showthread.php?p=4567222)

---

### Post by Phrantik on 2008-08-20
FYI... Your problem is not with ubuntu but with windows. Windows will destroy your master boot record if you install it after ubuntu is already installed.
windows=evil

---

### Post by Shiv4m on 2008-08-20
> **Phrantik said:**
> FYI... Your problem is not with ubuntu but with windows. Windows will destroy your master boot record if you install it after ubuntu is already installed.
windows=evil

What do you mean?

---

### Post by Phrantik on 2008-08-20
Linux plays nice with other operating systems...
You can easily install linux after installing windows but if you try to install windows after installing linux, windows will insist that it is the only operating system and you won't be able to boot back to linux without some command line voodoo and extensive knowledge of your linux operating system.

thats why it's best to install windows first if you are going to dual boot

---

### Post by Shiv4m on 2008-08-20
o Dam that sucks...

---

