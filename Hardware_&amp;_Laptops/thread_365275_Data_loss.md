---
title: "Data loss"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by Clythos on 2007-02-19
Hello,

I ran e2fsck on an ext2 partition which gave me a lot of errors and now all the data is gone, but the lost+found folder is full of about 70000 96,6 KB big files, some of them are mp3s who play about a second of sound. Is there any way I can put it together and regain the data (please let there be a way). Any help or idea is apprechiated.

Thanks in advance

---

### Post by petri on 2007-02-19
Yes, manually.

This link talks about reiserfs but i think it's the same to ext3 [http://www.linuxquestions.org/linux/answers/Hardware/ReiserFS_Data_Recovery_Tips](http://www.linuxquestions.org/linux/answers/Hardware/ReiserFS_Data_Recovery_Tips) (and search for lost+found). It does not look good.

I had the same situation in Windows and I never could use those files, I do hope Linux has some smarter way to deal with this than opening those 70 000 files manually. And maybe you shouldn't trust on that harddrive any more.


EDIT: Here's another quite useful link: [http://www.linuxjournal.com/article/193](http://www.linuxjournal.com/article/193)

---

