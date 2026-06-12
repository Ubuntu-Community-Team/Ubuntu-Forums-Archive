---
title: "Reliable filesystem for usb stick"
date: 2008-11-22
forum: General Help
---

### Post by jgoyvaer on 2008-11-22
Would it be better to use fat32 or ext3 for a usb stick ?

I'm using a stick on different computers for software development. It's formatted with fat32 because the file names should be case sensitive. And if needed I can stick it into a windows computer too.

Alas, once in a while I'm having corruptions. And I have to format the whole thing over. 

Would it make less prone to error to format it in ext3 ?

---

### Post by cmay on 2008-11-22
i switch  all my personal files from all systems with usb formatted in fat16 and fat32 with no problems.  i do not think it should be a problem. i use solaris, linux and now for a small period also windows and it works with out problems. i do not know however if windows can read an ext3 or ext2 file system. i may suspect it cant. but i have not had windows in 3 years so i do not know for sure since i haven tested it. sorry that i cant help any further. 
good luck

---

### Post by philinux on 2008-11-22
If you put this on the windows machines then they can read ext2/3 file systems.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

