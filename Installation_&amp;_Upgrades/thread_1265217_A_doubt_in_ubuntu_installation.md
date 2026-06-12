---
title: "A doubt in ubuntu installation"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by krashok1990 on 2009-09-13
I installed ubuntu by "Install inside windows", while installing it asked the size "i selected 6 GB" and ubuntu is installed without any problems,,,,,,,

i installed ubuntu in another computer and this time i selected 4 GB,,,,, this time also ubuntu installed without any problem,,,,,,,,,

i can't find any difference between the two installations,,,,,, both are same other than the size of installation,,,,,,,,

i like to know what is the difference between the two installations ??

---

### Post by ddrichardson on 2009-09-13
The amount of space you've allocated to Ubuntu rather than how much is installed. In other words it didn't take up 6Gb it allowed for up to 6Gb.

---

### Post by newsoft on 2009-09-13
> The amount of space you've allocated to Ubuntu rather than how much is installed. In other words it didn't take up 6Gb it allowed for up to 6Gb.


Are u sure of this????? It doesn't sound logic...did u try yourself?

---

### Post by ddrichardson on 2009-09-13
The 6 or 4 Gb is space allocated for Ubuntu. There needs to be a separate partition or in this case a virtual hard disk and this is what you are creating.

[http://wubi-installer.org/faq.php#internals](http://wubi-installer.org/faq.php#internals)

To confirm it to yourself, if you open a terminal and type:```
sudo fdisk -l
```You'll see a list of partitions. On one system it'll say Ext3 or Ext4 4Gb and on the other 6Gb.

---

### Post by fanglinyong on 2009-09-13
when you upgrade your system,you will found that you didn't have enough space to update your system!

---

### Post by raymondh on 2009-09-13
> **ddrichardson said:**
> The 6 or 4 Gb is space allocated for Ubuntu. There needs to be a separate partition or in this case a virtual hard disk and this is what you are creating.

[http://wubi-installer.org/faq.php#internals](http://wubi-installer.org/faq.php#internals)

To confirm it to yourself, if you open a terminal and type:```
sudo fdisk -l
```You'll see a list of partitions. On one system it'll say Ext3 or Ext4 4Gb and on the other 6Gb.

+1

While you have the terminal, might as well see how it is allocated/used

```
df -h
```

@fanglingyon ...... maybe, maybe not. It will all depend on how OP uses Ubuntu and what OP stores in Ubuntu.   You might be thinking of the 2.3GB install error ;)

---

