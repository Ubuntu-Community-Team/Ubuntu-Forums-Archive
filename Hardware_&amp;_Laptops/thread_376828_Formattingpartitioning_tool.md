---
title: "Formatting/partitioning tool?"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by bradford72 on 2007-03-05
Is there an easy to use (GUI) application available to partition and upgrade the format of my external USB HDD?  I mounted my /home directory to my external USB HDD when I was setting up my system, and was only able to chose to format it as ext2.  I believed (perhaps mistakenly) that it would be no big deal to later update it to ext3.  I would now also like to cut it in half and use the first half as an ext3 partition, and partition the second half ntfs for use by my windows machine.  I think if I can get this done, I should be able to mount the ntfs partition for read access by ubuntu as well?  thanks in advance!

---

### Post by ukbob on 2007-03-05
gparted in synaptic

---

### Post by aysiu on 2007-03-05
ukbob is right. GParted is your friend.
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

To install and use it, paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo aptitude update
sudo aptitude install gksu gparted ntfsprogs
gksudo gparted &
```

---

### Post by newlinux on 2007-03-05
as stated, gparted should do what you want, and by default NTFS will be able to be mounted readonly in ubuntu. Alternatively, you could install ntfs-3g to make your NTFS partition writeable in linux (search forums for opinions on this before doing it) or you could format the whole partition ext3 and install fs-driver in windows ([http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)) and that would allow you read and write access of your ext3 partitions in windows. You can search the forum for opinions on this is well - I consider the latter option safer, and it is what I do.

---

### Post by bradford72 on 2007-03-05
OOOoh...gparted and fsdriver...looks like I can do more than I thought...umm...what is the atvantage to getting gparted through aptitude as compared to synaptic...?
 
> 
[LEFT]sudo aptitude update
sudo aptitude install gksu gparted ntfsprogs
gksudo gparted &
 
does this install things differently? or is it just something that I should get used to if I want to grow into a "real boss hacker" (which for the record, I do)[/LEFT]

---

### Post by aysiu on 2007-03-05
> **bradford72 said:**
> what is the atvantage to getting gparted through aptitude as compared to synaptic...? In Edgy Eft? Not much. For Dapper and before, read [this](http://www.psychocats.net/ubuntu/aptitude).

---

