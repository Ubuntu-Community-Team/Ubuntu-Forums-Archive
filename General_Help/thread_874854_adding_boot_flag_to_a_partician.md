---
title: "adding boot flag to a partician"
date: 2008-07-30
forum: General Help
---

### Post by tejaka on 2008-07-30
Hello,

I installed linux on my pc, and then installed windows after that. So now I can not log in to linux. When boot from ubuntu live CD Linux patricians are fine and even there is grub file. I remember red hat fdisk had a option adding boot flag to a patrician that has installed an Os. So what is the solution ubuntu gives to get the ubuntu back?  

Thanks,

---

### Post by Potatoj316 on 2008-07-30
you can use fdisk to enable the boot flag.  I forgot how to do it though.  Its probably the same as red hat.

---

### Post by justleen on 2008-07-30
you can use fdisk, cfdisk, parted and gparted for that..

with fdisk its option "a" to toggle bootable

---

### Post by bodhi.zazen on 2008-07-30
> **tejaka said:**
> Hello,

I installed linux on my pc, and then installed windows after that. So now I can not log in to linux. When boot from ubuntu live CD Linux patricians are fine and even there is grub file. I remember red hat fdisk had a option adding boot flag to a patrician that has installed an Os. So what is the solution ubuntu gives to get the ubuntu back?  

Thanks,

Well, you need to restore grub after installing Windows. You do not need to flag a linux partition as bootable ;)

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

