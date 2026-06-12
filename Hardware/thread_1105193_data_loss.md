---
title: "data loss"
date: 2009-03-24
forum: Hardware
---

### Post by Aravind_1729 on 2009-03-24
I am having an hp dv6000 having vista and ubuntu 8.10 (hard disk partitioned) . I want to get rid of vista and use only ubuntu since i don't use windows anymore. but i have a memory (120 gb) shared by windows and ubuntu. so if i reinstall ubuntu in my system( as a whole) will i loss my data. please help me since i have some important data in that memory (120 gb).

---

### Post by teaker1s on 2009-03-24
unless you allow new install to create a new partition guided partitioning using free space,you will otherwise delete all data in existing partition

---

### Post by Aravind_1729 on 2009-03-25
Thank You very much for your advice. It was very useful. 
But I didn't understand clearly the meaning of the last link that you provided. I am sorry if my post sounded rude. I am a beginner in linux and linux communities and I am also new to forum. So I apologize if my language was bad .Sorry. Now i will be more careful when when I post in forums. Once again thankyou for your reply.........

---

### Post by teaker1s on 2009-03-25
The links are my signature, they are on every post-in fact you have been very polite welcome:popcorn::popcorn::popcorn:

---

### Post by Aravind_1729 on 2009-03-26
oh ok , I was mistaken. I am new to all these things and my learning curve is not that steep. Sorry. I am learning!!!
Any way thank you for your time.

---

### Post by teaker1s on 2009-03-26
welcome to the forums:popcorn:

---

### Post by Mark Phelps on 2009-03-26
> **Aravind_1729 said:**
> I am having an hp dv6000 having vista and ubuntu 8.10 (hard disk partitioned) . I want to get rid of vista and use only ubuntu since i don't use windows anymore. but i have a memory (120 gb) shared by windows and ubuntu. so if i reinstall ubuntu in my system( as a whole) will i loss my data. please help me since i have some important data in that memory (120 gb).

Don't know what you mean by "memory shared". I'm guessing that what you really mean is that you have a partion (disk space) that is being accessed both in Vista and in Ubuntu.  Right?

If that's true, and what you want to do is retain the files you have now in Vista (you can't keep the programs or settings), there are two ways to do that:
1) Mount the Vista partition in Ubuntu and copy the files into your Ubuntu file system
2) Boot into Vista, attach an external drive (USB stick or hard drive), copy off the files you want to save.  After you convert your PC entirely to Ubuntu, attach the external drive and copy the files into your Ubuntu filesystem.

---

### Post by Aravind_1729 on 2009-03-27
ya that was exactly what i meant. Thank You . I will give you a better idea about my system.
I will give you the output of fdisk -l.
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51575157

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15827   127125188+   7  HPFS/NTFS
/dev/sda2           18377       19457     8683132+   7  HPFS/NTFS
/dev/sda3           15828       16191     2923830   82  Linux swap / Solaris
/dev/sda4           16192       18376    17551012+  83  Linux

Partition table entries are not in disk order


What I want to do is that I want to keep a memory which is shared by two operating systems ie fedora 10 and ubuntu 8.10( around 100gb) of which i am keeping ubuntu as the main one. I haven't put fedora yet.I will be putting fedora in sda4 which previously contained recovery portion of windows vista.

 I have made a recovery disk of windows vista and so I am now ready to remove vista!!!!.
 
but the memory that I want to keep as the memory shared by ubuntu and fedora is to be taken from sda1. I will back up everything so that is not a problem. But can i do it without without removing my already existing ubuntu. (ie can I extend my already existing ubuntu ext3 partition).
So basically what i am asking is that  can i remove windows vista from sda1 , take some gb's from sda1 (20gb) and give it to ext3 in sda4.
Phew!!! that is too much. Sorry for asking too much in such a complicated manner!!!. Can anyone help me. Thank You in advance.....

---

### Post by Mark Phelps on 2009-03-27
> **Aravind_1729 said:**
> So basically what i am asking is that  can i remove windows vista from sda1 , take some gb's from sda1 (20gb) and give it to ext3 in sda4.
Phew!!! that is too much. Sorry for asking too much in such a complicated manner!!!. Can anyone help me. Thank You in advance.....
To do what you want, you have to do the following:
1) Reformat sda1, shrinking it in the process
2) Move sda2 and sda3 to the left
3) Increase the size of sda4

You would do better to download the GParted LiveCD (you can get it from distrowatch.com), burn it to CD, and boot from that.  Also, do each of the steps one at a time.  But be prepared for a long wait.  GPArted is not fast.

---

### Post by Aravind_1729 on 2009-03-27
k , Thank you .
I did as you told and I shrinked ,edited all the partition. now this how my system looks!!!
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51575157

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12523   100590966    5  Extended
/dev/sda2           17022       17046      200812+  83  Linux
/dev/sda3   *       12524       17021    36130185   83  Linux
/dev/sda4           17047       19457    19366357+  8e  Linux LVM
/dev/sda5               1       12158    97659072    b  W95 FAT32
/dev/sda6           12159       12523     2931831   82  Linux swap / Solaris

Partition table entries are not in disk order


So I kept 100gb as shared so that i can use it for any operating system.
37gb for ext3 for ubuntu . 3gb as swap area . 
now the remaining 20gb i used for fedora 10.
but now the problem is that If i install ubuntu i cant see fedora at the boot time and if i install fedora I can't see ubuntu. I tried it many times. but the same result again and again. 
I know i have to edit the boot loader.but i dont know how to do it. 
Thank you in advance.....

and thank you mark you have been very helpful . thank you.:)

---

### Post by Aravind_1729 on 2009-03-29
Thank You everyone . I was not able to go to fedora or see the fedora 10 option while boot loading. I installed as i said ubuntu in 40 gb space. fedora in 20 gb and created an ntfs partition so that every operating system can access that 100 gb partition.
 
to solve this ( to get into fedora and bring the fedora option while booting) what i did was I went into the partition where fedora was installed went to /boot/grub/menu.lst and copied the lines starting from "title" then i pasted it on the /boot/grub/menu.lst file in my ubuntu partition. Now I was able to see and get into all the operating systems while booting. 
Here I installed ubuntu after installing fedora . If it is otherwise do the reverse. I  think that will be helpful . but always back up the data while experimenting with all these things. Just to make sure that no important data is lost!!!

---

