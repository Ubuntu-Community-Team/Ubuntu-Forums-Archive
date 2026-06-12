---
title: "commands"
date: 2008-08-20
forum: General Help
---

### Post by chazn85 on 2008-08-20
Hey all,

Can anyone tell me the correct command to delete a file thats over x amount of days old automatically? 

Thanks in advance

---

### Post by firsttimeuser on 2008-08-20
easy, you can use "find" to do this

find ./ -ctime +3 | xargs rm

find anything older than 3 days under current dir and delete it

---

### Post by chazn85 on 2008-08-20
exactly what i needed thanks

---

