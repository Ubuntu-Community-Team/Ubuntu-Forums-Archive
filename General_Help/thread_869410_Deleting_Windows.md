---
title: "Deleting Windows"
date: 2008-07-24
forum: General Help
---

### Post by COLiNx86 on 2008-07-24
So I think it's time for me to finally completely remove windows vista, but first I gotta ask a few things. If I remove it it's not gonna mess up anything in Linux right? I don't think it will but I wanna make sure. And how can i tell which partition is my windows one? I don't remember :lolflag:.

---

### Post by iaculallad on 2008-07-24
> **COLiNx86 said:**
> So I think it's time for me to finally completely remove windows vista, but first I gotta ask a few things. If I remove it it's not gonna mess up anything in Linux right? I don't think it will but I wanna make sure. And how can i tell which partition is my windows one? I don't remember :lolflag:.

It won't mess with Ubuntu if you're using GRUB to boot onto windoze. Just boot in your Ubuntu system, edit your /boot/grub/menu.lst file and delete the  boot option for vista and use Gparted to format that drive/partition where vista resides.

EDIT: To know which partition resides, use the command below:

```
sudo fdisk -l
```

or simply view your /etc/fstab file.

```
cat /etc/fstab
```

---

### Post by COLiNx86 on 2008-07-24
Sorry, I'm kinda new to linux.
[IMG]http://img237.imageshack.us/img237/2146/screenshotpk5.png[/IMG]
That's the windows partition right?

---

### Post by Oldsoldier2003 on 2008-07-24
Yes, thats the one.

---

### Post by COLiNx86 on 2008-07-24
Now it just says unallocated how do I join that with my linux partition?

---

### Post by COLiNx86 on 2008-07-25
anyone? Sorry for bumping this I just wanted to do this before I went to bed.

---

### Post by iaculallad on 2008-07-25
> **COLiNx86 said:**
> anyone? Sorry for bumping this I just wanted to do this before I went to bed.

You could just create it as another partition for your Multimedia/Data. You can format it using GParted as NTFS or Ext2/Ext3 (of your preference).

---

### Post by EPOX123 on 2008-07-25
Virtual Box is the best bet you can run windows inside of Linux full blown no lag or any thing and use windows only when you need to freak amazing!!!

---

