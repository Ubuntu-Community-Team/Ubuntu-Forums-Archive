---
title: "Unable to mount HD with Kubuntu"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by gitmo on 2005-05-25
I recentely installed Kubuntu ( becuase I know KDE better than Gnome) on a Compaq Presario X6000 laptop and installation was perfect, kubuntu dectected my sound card and my VGA very well, but I can not mount any other partition, I can only mount Kubuntu partition and the CD.  Apparentely it can see them, but can not mount them.  I have windows XP on the other partition.  Can some one help me?  
I also have ubuntu on a DVD that I bought, how can I add more applycations to my Kubuntu?
Thanks in advanced.

---

### Post by Xian on 2005-05-25
[QUOTE=gitmo]I can only mount Kubuntu partition and the CD.  Apparentely it can see them, but can not mount them.  I have windows XP on the other partition.  Can some one help me? [/QUOTE]
So then it is the WinXP you are trying to mount or other partitions as well?
Can you post the output of the terminal command below?
We need to first identify the partition(s) location.

```
$ sudo fdisk -l
```

---

### Post by ::DoGG:: on 2005-05-26
What do You mean by "seeing them but not mount them" what is a filesystem on xp? ntfs ? send the otput of lsmod.

---

