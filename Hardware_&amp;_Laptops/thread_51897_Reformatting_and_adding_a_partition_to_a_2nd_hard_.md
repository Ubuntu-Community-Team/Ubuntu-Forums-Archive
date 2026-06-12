---
title: "Reformatting and adding a partition to a 2nd hard drive"
date: 2005-07-25
forum: Hardware &amp; Laptops
---

### Post by kybishop on 2005-07-25
I have an old hard drive which has an ntfs parition on it.

How do I reformat and use the hard drive with ext3.

Is it possible to also add more swap parition to the second hd?
If not, how do I edit my swap partition on my first hd to make it bigger.

Sorry for all the questions, just getting used to linux.

---

### Post by songochain on 2005-07-25
U can format with cfdisk or [qtparted](http://qtparted.sourceforge.net/screenshots.en.html) 
To add a swap partition u can use swapon and swapoff to del it

---

### Post by kybishop on 2005-07-25
i downloaded qtparted and made a ext3 partion, and extended partition with more swap partition in it.

Now im a little confused how i can add that space to root, or if i can't, where the folder is that i use to access the second hard drive.

---

### Post by kybishop on 2005-07-26
could you explain how to use swapon, and any other commands i'd need to get my computer using the new swap area.

---

### Post by songochain on 2005-07-26
If u want to use your new swap partition every u boot your linux box, edit /etc/fstab and add a new line for your new swap partition. If u want to probe without edit fstab, use swapon /dev/hdXX to add a new swap partition

---

