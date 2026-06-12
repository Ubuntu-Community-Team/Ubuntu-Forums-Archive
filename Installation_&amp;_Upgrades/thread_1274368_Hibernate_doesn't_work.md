---
title: "Hibernate doesn't work"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by gigaforce1111 on 2009-09-24
Hi all,
I have an issue I wanted to solve.
The hibernate option doesn't work properly:
After install Ubuntu and try hibernating it says that swap partition is not big enough.
I resized the partition and made it bigger.
Now when I'm trying to hibernate the pc shuts down **but** when I turn the pc on it boots to an empty desktop without loading the opened programs.
Thanks in advance!

---

### Post by gigaforce1111 on 2009-09-25
anyone?

---

### Post by junke1990 on 2009-09-25
an empty desktop? what do you see then? btw you can try suspend in stead of hibernate, I personally prefer that and no swap needed.

There is no clear rule for swap as far as I know but most people advise that the swap should be double the size of your RAM

---

### Post by gigaforce1111 on 2009-09-25
> **junke1990 said:**
> an empty desktop? what do you see then? btw you can try suspend in stead of hibernate, I personally prefer that and no swap needed.

There is no clear rule for swap as far as I know but most people advise that the swap should be double the size of your RAM

Hi junke1990,
I fixed the swap partition issue. Now I have 8GB!!! of swap partition (4GB of RAM).
By saying empty desktop I meant like after restart. 
The thing is that when I go into Hibernate and leave applications running on my desktop, and waking the pc from hibernate the applications don't keep running any more. 
Hope you can help me.

---

### Post by gigaforce1111 on 2009-09-25
sorry double post.

---

### Post by gameguy on 2009-09-25
> **junke1990 said:**
> There is no clear rule for swap as far as I know but most people advise that the swap should be double the size of your RAM
 Actually, I have heard that that is a myth, because if you have person 1 with 1 gb of ram, and person 2 with 4 gb of ram, who is more often going to need swap space because they've run out of actual ram?
Person 1 will obviously need more swap space.

---

### Post by gigaforce1111 on 2009-09-26
> **gameguy said:**
> Actually, I have heard that that is a myth, because if you have person 1 with 1 gb of ram, and person 2 with 4 gb of ram, who is more often going to need swap space because they've run out of actual ram?
Person 1 will obviously need more swap space.
I heard that too.
I set the swap as I did just in case.

Does anyone know how to fix the Hibernate issue?
I looked into the logs files and didn't understand much.
Please help!

---

### Post by gigaforce1111 on 2009-09-27
anyone?

---

### Post by nathan726 on 2009-09-27
Try this...

Gather info:
```

sudo fdisk -l
cat /etc/fstab
blkid

```Ensure resume id = swap partition id:
```
sudo gedit /etc/initramfs-tools/conf.d/resume
```And regenerate your initrd.
```
sudo update-initramfs -u
```Reboot and then test.

---

### Post by gigaforce1111 on 2009-09-27
> **nathan726 said:**
> Try this...

Gather info:
```

sudo fdisk -l
cat /etc/fstab
blkid

```Ensure resume id = swap partition id:
```
sudo gedit /etc/initramfs-tools/conf.d/resume
```And regenerate your initrd.
```
sudo update-initramfs -u
```Reboot and then test.
Yes!!!
You Solved it man!
You are the greatest!
Both Hibernate and Suspend are working now!
I did play with the swap partition and it caused the problem.
Million thanks to you nathan726!

---

### Post by miegiel on 2009-09-27
Thx **nathan726**, those 2 last steps where exactly what I needed to fix my hibernation.

---

### Post by nathan726 on 2009-09-29
I'm happy I could help.

---

