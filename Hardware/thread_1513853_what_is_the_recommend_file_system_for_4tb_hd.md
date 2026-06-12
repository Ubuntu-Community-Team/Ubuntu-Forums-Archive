---
title: "what is the recommend file system for 4tb hd?"
date: 2010-06-20
forum: Hardware
---

### Post by SOME1 on 2010-06-20
Hi, 

I bought external Hard drive (Western Didital my studio book II edition) with 4 tb size. 
I want to format it to linux file system and I am not sure what is the most recommended for this size: ext2, ext3 or ext4? 

thank you.

---

### Post by sxmaxchine on 2010-06-20
for an external drive i would recomend ext2 as i am not sure ext3 or 4 are greatly supported as an external hard drive.

I also would leave it as ntfs because then it will work in windows as well

---

### Post by SOME1 on 2010-06-20
ntfs drive must be defrag manually.

thats one of the reasons I prefer linux filesystem. 
in windows, I know that there is some programs that will allow to read and write to ext2 and ext3.

---

### Post by cascade9 on 2010-06-20
You probably should go into whatever controller there is on that drive and change it from 4TB (2x2TB RAID 0) to 2TB (2x2TB RAID 1). 

RAID 0 isnt really a good idea for a stoage drive, if one drive goes theb 'bang', you've lost all your data. 

As ong as you have no plans to hook up the drive to a windows box, I'd go for EXT3. EXT4 is still a bit to new for me tot totally trust it, and on an external, the minor speed increase wont make a difference.

---

### Post by SOME1 on 2010-06-20
thank you. 
can you reffer me to how can I change the controller? 

usually I use gparted to format the drive. Is There an option there to change the controller too?

---

