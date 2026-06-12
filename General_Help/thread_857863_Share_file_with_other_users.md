---
title: "Share file with other users"
date: 2008-07-12
forum: General Help
---

### Post by jeffreyldavidson on 2008-07-12
Hello, I use Moneydance on Ubuntu, thinks it is great. How can I allow the use of the data file with other users on the same laptop that has their own logon on? I want to allow access of the file.

Thanks

---

### Post by boblemur on 2008-07-12
im not sure what money dance is... but if the file is in your home folder you could either move it and use sudo... or if its in a locked location you can ( ie the program looks for it in .moneydance) then you will need to setup permissions (chmod) on the file so that others can read(possibly write to) and then make a symbolic link using ln -s

---

