---
title: "[SOLVED] retrieve files from online folder"
date: 2008-10-06
forum: General Help
---

### Post by afbase on 2008-10-06
1) I want to make a cron job that downloads pdf documents my professor posts on his website: [http://www.csun.edu/~vakilian/math350/lecture_notes/]("http://www.csun.edu/%7Evakilian/math350/lecture_notes/")
2) the downloaded documents are placed in a folder, say /home/user/Documents/school/
3) it downloads only pdf's that are not already in /home/user/Documents/school/


I thought wget would be the right idea:

```

wget -r -np -A pdf http://www.csun.edu/~vakilian/math350/lecture_notes/ 
```This is all that i can think of but this doesn't really seem to do the job when cron only puts the files into the '/home/user' directory.

any help appreciated :)

---

### Post by afbase on 2008-10-06
I thought about SVN but this isn't an SVN server.  Just an online folder.

---

### Post by niteshifter on 2008-10-06
Hi,

I believe this will work:
```
wget -r -np -nc -P /home/user/Documents/school -A pdf http://www.csun.edu/~vakilian/math350/lecture_notes/
```

Same line as yours with these switches:
-nc The no clobber switch. Already present files from site won't be downloaded.

-P /Path/To/Where/You/Want/Them  As it says.

---

