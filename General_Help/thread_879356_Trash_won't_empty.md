---
title: "Trash won't empty"
date: 2008-08-03
forum: General Help
---

### Post by supertails on 2008-08-03
There were three folder that I have put in trash and I can't delete them and when I try moving them out of trash and then putting them back they just multiply. How can I remove them?

---

### Post by jonian_g on 2008-08-03
Open a terminal and type:

```
sudo nautilus /home/[your username]/.local/share/Trash/files
```

Right click on the files you want to delete and delete them.

---

### Post by mdsharp24 on 2008-08-03
I installed secure-delete and added a /etc/crontab to run srm -rl /home/[your username]/.local/share/Trash/files/* everyday at 3am

works great :)

---

### Post by supertails on 2008-08-04
I don't know what that is but it looks like you just copied jonian_g post and just added your own words to it.

---

### Post by mdsharp24 on 2008-08-04
Nope, jonian's post runs the file managaer Nautilus on the Trash location so the OP could delete his Trash.

My post installed the Ubuntu program secure-delete and recommended adding the executable srm to crontab so that a users trash would be securely deleted at a specified time.

Pats you on the head.

---

