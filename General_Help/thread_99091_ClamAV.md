---
title: "ClamAV"
date: 2005-12-04
forum: General Help
---

### Post by damnhappy on 2005-12-04
I ran clamav last night before I went to bed, and found I had two viruses when I woke up. 
I've been unable to find exactly what two files are infected. I l;ooked in /var/log/calmav, but there are only freshclam logs there. I am not sure where else to look. Any ideas would be greatly appreciated.
Thanks,

---

### Post by randlieb on 2006-01-01
same here. i ran clamav on breezy ubuntu and found 9 viruses but no indication of what to do with them. or were they deleted by clamav?

---

### Post by cstudent on 2006-01-01
If it finds a virus it will place the world FOUND in the line for that file. Try using cat or grep to find that word.

grep FOUND /var/log/clamav/clam.log

cat FOUND /var/log/clamav/clam.log

---

### Post by anil_robo on 2006-01-01
search your drive for "clamav-testfiles". Clamav reports these "test" files as viruses, to let us know that it's working well. Also see [this.]("http://www.ubuntuforums.org/showthread.php?t=104001#19")

---

### Post by installer on 2006-01-02
**[FONT="Impact"][SIZE="1"]Ignore please.[/SIZE][/FONT]**

---

