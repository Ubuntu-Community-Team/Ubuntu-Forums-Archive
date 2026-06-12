---
title: "Uninstall Windows XP from Ubuntu?"
date: 2008-08-29
forum: General Help
---

### Post by TreadLight on 2008-08-29
How do I uninstall Windows XP with Ubuntu? They are both on the same partition, and I just want to get rid of Windows XP altogether, Any help?

---

### Post by Bliepo32 on 2008-08-29
Well, just gparted. You can install it by entering this in the terminal:
```
sudo apt-get install gparted
```

Then just format the windows partiton.

NOTE: This might cause GRUB to stop working, so download supergrub just in case.

---

### Post by Oldsoldier2003 on 2008-08-29
> **TreadLight said:**
> How do I uninstall Windows XP with Ubuntu? They are both on the same partition, and I just want to get rid of Windows XP altogether, Any help?

if they are on the same partition that would suggest you did a wubi install of Ubuntu. What you need to do is install Ubuntu into its own partition using the live cd or alternate cd. If you want to completely forgo windows then just allow Ubuntu to use the whole disk.

---

### Post by TreadLight on 2008-08-29
How do I let it take up the whole disc? I installed it with 30GB thing when you use Wubi.

---

### Post by Oldsoldier2003 on 2008-08-29
> **TreadLight said:**
> I am using one partition. I know I can delete the partition to delete Windows XP, but what about Ubuntu? It'd be gone too.

That is correct. I think he misunderstood your position. 

In any event if you are wanting to go straight Ubuntu its better to do a "real" installation rather than the wubi. Unfortunately its not a seamless transition. I always counsel folks to go with dual booting from a normal install of Ubuntu. It takes more work from the beginning, but saves work and aggravation in the end.

---

### Post by Oldsoldier2003 on 2008-08-29
> **TreadLight said:**
> How do I let it take up the whole disc? I installed it with 30GB thing when you use Wubi.

Download either the live cd or alternate installer cd from [www.ubuntu.com/getubuntu](www.ubuntu.com/getubuntu)

installation instructions are available here: [https://help.ubuntu.com/community/Installation/](https://help.ubuntu.com/community/Installation/)

if you have any issues folks here will be happy to help get you sorted.

---

### Post by thndrbd2 on 2008-08-29
I am new to this but need help.  I have a system with Ubuntu 7.04 on it but the "Home" file was deleted.  I cannot get into the system nor can I get it to read a Windows Disc to try to install a new operating system.

I tried recovery ... the "C" to get to command line and types ls /home and received error "File not found"  Is there a way to get into the system with the home file deleted?

Please help

804-864-7822

---

