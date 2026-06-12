---
title: "How to remove Grub without format ubuntu partition"
date: 2008-07-14
forum: General Help
---

### Post by blacappuccino on 2008-07-14
Hey guys... can u tell me a way to remove the Grub without format the ubuntu partition. I have windows and ubuntu on my PC, the first time i formatted the partition that contain ubuntu but i had to reinstall it cos the windows didn't boot...

So can u tell me how to solve this problem windows destroy windows... i mean i want to boot windows...

Thanks

---

### Post by ghost_ryder35 on 2008-07-14
> **blacappuccino said:**
> Hey guys... can u tell me a way to remove the Grub without format the ubuntu partition. I have windows and ubuntu on my PC, the first time i formatted the partition that contain ubuntu but i had to reinstall it cos the windows didn't boot...

So can u tell me how to solve this problem windows destroy windows... i mean i want to boot windows...

Thanks
follow the link in my sig to reinstall grub and it will auto detect windows and you will be able to boot into it if thats what you want to do.

---

### Post by lisati on 2008-07-14
Am I correct in assuming that you want to keep both Windows and Ubuntu? What you need to do will depend on which you want to keep.

---

### Post by blacappuccino on 2008-07-14
i want to remove Grub only and keep both OS. I will install Acronis OS Selector to allow me to choose...

---

### Post by ghost_ryder35 on 2008-07-14
> **blacappuccino said:**
> i want to remove Grub only and keep both OS. I will install Acronis OS Selector to allow me to choose...
boot into a windows recovery prompt (you will need a windows CD/DVD) and 
```

fix mbr
fix boot (maybe u need this one maybe you dont)

```then u should be able to boot windows and not ubuntu (but ubuntu will still be on the HD)

---

### Post by blacappuccino on 2008-07-15
i booted Windows installation CD but when i click F2 enter to recovery option, it ask for a recovery disc and i don't have a recovery disc, cos i never create partition or disk recovery for windows...

So, there is another way to solve my problem?

---

### Post by cariboo on 2008-07-15
You haven't gone far enough, when it asks you to hit F2 that is only if you have a recovery CD. Let it go past that point and eventually it will ask you if you want to install windows or open the recovery console. Pres **r** for the recovery console. read carefully what it says on screen and choose your operating system in MS speak. For help at the C:\ prompt type help.

Jim

---

### Post by blacappuccino on 2008-07-15
ok i will try this... thanks

---

