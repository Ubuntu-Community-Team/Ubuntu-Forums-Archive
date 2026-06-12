---
title: "hardrive problems"
date: 2008-10-25
forum: General Help
---

### Post by patrickbd on 2008-10-25
Hi I'm a noob.  I just installed ubuntu using wubi to dual boot on my laptop. I only allowed 10 gig for ubuntu installation, and was wondering if i could access more hardrive space.  I already used samba to connect to my desktop, but was wondering if there were any other ways to access folder that are in windows on this laptop. I have 250 gig on my laptop but don't know how much of that ubuntu sees.   Thanks alot

---

### Post by pytheas22 on 2008-10-25
Open up a file browser (you can do that by selecting to Places>Home Folder) and navigate to the location '/host'.  Your Windows file system should appear there if you installed using wubi, and you can read and write to the Windows directories.

---

### Post by patrickbd on 2008-10-25
Thank you.   I've tried that before and it didn't work, but i think i was trying to change the sharing options.  It works now.  


so are there any huge disadvantages of installing ubuntu through wubi?    (I think i have wubi because i didn't manually partition my hardrive).

---

### Post by pytheas22 on 2008-10-26
In principle wubi is a little slower, because the files on your hard drive are more separated than they'd be if they had their own partition.  Also, as far as I know, you can't hibernate or suspend Ubuntu if it's installed using wubi.  But in general, it's pretty much the same thing; there are no enormous disadvantages.

---

