---
title: "misc help"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by Wuu on 2007-07-10
Hi! I am new hear and hear is my first questions.

i haw dir  **/home/edgars/.wine/** and i want to set access **rwx** to my user "edgar" 
to /.wine/ and all sub folders... how? 

#-o

---

### Post by FreeFull on 2007-07-10
How does this have to do with Hardware or Laptops? And you dont need x on .wine and subfolders. Press Alt+F2 and type xterm in the box. In the xterm window type in
```
sudo chmod u+rw -rf /home/edgars/.wine/
```
It will work assuming the owner of .wine is the user edgar. Don't worry when you will type in your password and you won't see any stars, just ignore that fact.

---

### Post by Wuu on 2007-07-10
senx its works :popcorn:

---

