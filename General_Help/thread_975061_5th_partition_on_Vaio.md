---
title: "5th partition on Vaio"
date: 2008-11-08
forum: General Help
---

### Post by Kosmi4 on 2008-11-08
I have a Sony Vaio VGN-AR21M and i 'm using dual boot (XP & Ubuntu 8.10).. The problem is that i 've already have 4 primary partitions (1.Vaio's recovery partition, 2.XP's local disk, 3.Linux local disk, 4. linux swap) and i can't use my 5th partition as it's unullocated. 
Can you please tell me who to use this 5th partition, as i want to use it as a common disk for XP & Linux to share files... 
I know that the better way is to reformat and setup Ubuntu again but i have done this twice cause i had problems with NVIDIA drivers.. and now everything works perfect (programs,extra effects etc). so i don't want to start again from the beginning  .. 
I took a snapshot from XP using partition magic 8 (believed it would do the job for me but..) to show you my problem
Can you tell me what to do? 
Thanks in advance

---

### Post by PatrickVogeli on 2008-11-08
the problem you are having is a limit in primary partition. On a PC you can only have 4 primary partitions, and if you want more, you will have to make an extended partition, and every extended partition can have 4 partition inside.

I believe you are lucky, since you can just delete the swap, make and extended partition and there make another swap and the 5th partition you wanted.

---

### Post by louieb on 2008-11-08
> **PatrickVogeli said:**
> ...I believe you are lucky, since you can just delete the swap, make and extended partition and there make another swap and the 5th partition you wanted.

+1 could not have said it better. 
Might want to learn about the 3 partition types: [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by plucky on 2008-11-08
> and every extended partition can have 4 partition inside.


Lot more than 4.

---

### Post by Kosmi4 on 2008-11-09
Thanks for the reply.. i will try it later.. but somewhere in the forums i have read that i might have problems with the swap partition if i change the setup.. do you think that it will work easy or i 'll need extra help?

---

### Post by louieb on 2008-11-09
> **Kosmi4 said:**
> ... i might have problems with the swap partition if i change the setup.. 
Deleting swap and recreating it will change its UUID.   
files **/etc/fstab and /etc/initramfs-tools/conf.d/resume **will need updating with the new UUID.  
Pretty easy you use the **sudo blkid** to find the  new UUID. Edit the files and your good to go.

If you hibernate the laptop  you will need to rebuild i**nitramfs-tools** thatw easy too.

```
sudo dpkg-reconfigure  initramfs-tools
```

---

### Post by Kosmi4 on 2008-11-12
Thank you..i did as you said and it was too easy indeed..

---

