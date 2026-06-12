---
title: "Format internal secondary hard drive"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by brad1150 on 2007-04-19
How do I format my secondary internal hard drive? All I can find are guides for formatting external USB drives. I have an 80gb internal drive I wish to use for ftp storage.

---

### Post by volksolwagen57 on 2007-04-19
first do this in the terminal:
**sudo apt-get install gparted**
once you have that installed do this in the terminal:
**sudo lshw -C disk**
look for a line that says *logical name:*
then, open up gparted which should be somewhere in the applications menu, select it.
then go up to the top right and select what the drive is that you are trying to format. it could be something like /dev/hdd or /dev/sdb or something.
then right click on the white bar and select new. for size select all, if you want the whole disk to be used, and (this is crucial, as if nothing else were :-)) choose what type of file system protocol you want. if you've got a windows computer that you share files with you should choose fat32. if you don't just choose ext3.
after you're done, click add and go have a hazelnut mocha. :-D.
hope this helps.

---

### Post by brad1150 on 2007-04-22
Thanks. Now that its formatted do I just have to mount it to a directory like:
sudo mount /dev/hdb /server
?

Nvm, I gotit installed and working. Thank you for telling me how to mount it.

---

