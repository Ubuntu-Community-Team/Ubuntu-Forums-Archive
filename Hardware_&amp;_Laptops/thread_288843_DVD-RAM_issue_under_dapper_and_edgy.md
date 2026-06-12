---
title: "DVD-RAM issue under dapper and edgy"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by razahel on 2006-10-30
Hi,

I have an asus m67 laptop and since some time i only can mount dvd-rams as root. I have a adjusted the fstab several times but nothing changes it.
When i try to write to the ram as root problems occure by files larger then 1GB.
Then the system does not write or unmount or read the ram until restart and the files on the ram(the large ones) are broken.

I had this problem under dapper and now tried edgy but the problem still exists.

I hope someone can help.

regards razahel

---

### Post by _obelix_ on 2006-11-05
Hi,

the same here. :confused: 

regards 

obelix

---

### Post by razahel on 2006-11-06
Are you using udf formated disks 
and do you encounter the same problem with files larger than 1GB?
which kernel are you using?
A friend of mine told me that it should work with a self made kernel from kernel.org

---

### Post by razahel on 2006-11-07
Hmm,

this might help.
In a forum I found a clue. It was mentioned that if you write to DVD-RAM the file will completely put  into your swap space before closing the operation.
The interesting part is the problem occurs if I copy a file larger than 1GB which is also my actual swap size.
@obelix: how is it at your computer how big was the file and how big is your swap?

---

