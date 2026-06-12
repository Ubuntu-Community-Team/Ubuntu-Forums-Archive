---
title: "Cant access my NTFS hard drives"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by Woland2009 on 2009-05-24
Hello everyone,

I am having quite a strange problem on my fresh install of xubuntu. Basically I have three hard drives: a 20gb one which will contain xubuntu, and two large NTFS ones for data storage. Everything was working fine, until I swapped out one hard drive and replaced it with one that has windows on it. Now Im not planning to dual boot, just want to recover some files. The windows part, however, screwed everything up. I now cant access my hard rives, and they are no where to be seen in the /dev folder. 

So basically, I think I got confused with all the different partitions. 

I now have a fresh install of xubuntu, which does not see any of the NTFS hard drives. What do I need to do to get rid of the windows influence, and access my files. 

Please let me know if you require more info.

Thank you.

---

### Post by taurus on 2009-05-24
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Woland2009 on 2009-05-24
Nothing, its blank.

---

### Post by miegiel on 2009-05-24
> **Woland2009 said:**
> Hello everyone,

I am having quite a strange problem on my fresh install of xubuntu. Basically I have three hard drives: a 20gb one which will contain xubuntu, and two large NTFS ones for data storage. Everything was working fine, until I swapped out one hard drive and replaced it with one that has windows on it. Now Im not planning to dual boot, just want to recover some files. The windows part, however, screwed everything up. I now cant access my hard rives, and they are no where to be seen in the /dev folder. 

So basically, I think I got confused with all the different partitions. 

I now have a fresh install of xubuntu, which does not see any of the NTFS hard drives. What do I need to do to get rid of the windows influence, and access my files. 

Please let me know if you require more info.

Thank you.

Try booting windows and checking the disks for errors. Impropperly dismounted disks in windows can give issues when mounting them in linux.

```
chkdsk c: /f /x
chkdsk d: /f /x
```(windows command line) should do the trick.

---

### Post by miegiel on 2009-05-24
> **Woland2009 said:**
> Nothing, its blank.

don't forget the *sudo* infront of *fdisk -l* ;)

---

