---
title: "shell script  export to file"
date: 2008-08-05
forum: General Help
---

### Post by dapim on 2008-08-05
echo "select id from messa where status not in ('S') " | mysql -h mysql-live -u setj

i want to export the result of this command to a file 

i try this :
echo "select id from messa where status not in ('S') " > file | mysql -h mysql-live -u setj

but got error

---

### Post by geirha on 2008-08-05
Try ```
echo "select id from messa where status not in ('S') " | mysql -h mysql-live -u setj >file
``` You want to redirect the output of the mysql-command, not the echo. The output of echo should be redirected to mysql, which you are doing with the pipe(|)

---

