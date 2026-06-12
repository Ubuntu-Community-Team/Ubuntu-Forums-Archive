---
title: "Missing install-option"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by Tori1 on 2009-06-17
[COLOR=Black]This is how it looks like for me:

[IMG]http://i39.tinypic.com/2v0da2u.png[/IMG]
[/COLOR] 
I got Vista, but I wanna have Ubuntu too. I have shrinked my hdd with 50GB so I have room for Ubuntu and I followed this tutorial ([http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)). But the "Use the largest countinuous free space"-option is missing. I have burned Ubuntu on two different cd/dvd, but it's still missing.
Btw, I've got two hdd.
[IMG]http://i39.tinypic.com/2eekd5f.jpg[/IMG]

Can anyone help?

---

### Post by Tori1 on 2009-06-17
Does anyone know ?

---

### Post by ptn107 on 2009-06-17
The reason the option is not there is because your disk already has the maximum amount of primary partitions it's allowed to use.

A disk can be divided into a maximum of four (4) primary partitions.  Your drive already uses all four (you can see sda1, sda2, sda3, sda4 on your drive).  The only way to get more than four partitions on a drive is to make one of them an extended partition, and that extended partition can be divided up into as many logical partitions as you want.

What you have:
```

device:    partition type:
sda1       primary
sda2       primary
sda3       primary
free space <cannot be partitioned>
sda4       primary

```

What you want:
```

device:    partition type:
sda1       primary
sda2       primary
sda3       extended
 sda5      logical 
 sda6      logical
 sda7      logical
 ...etc...
sda4       primary

```
Since sda1,2 and 4 on your disk contain windows operating systems that you probably want to keep, the only foreseeable way to do this is to take your sda3 partition and restructure it to contain the needed logical partitions for Ubuntu, but only if sda3 does not contain any data you wish to keep.

---

### Post by Tori1 on 2009-06-18
Thanks :)

---

