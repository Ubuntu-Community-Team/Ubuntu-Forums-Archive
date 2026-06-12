---
title: "User and root rights"
date: 2008-08-25
forum: General Help
---

### Post by someone_yeah on 2008-08-25
Something very weird happened. I don't know how, but now as a root I cannot access,copy,delete,etc. the files that belong to my username. When I am a normal user I can do everything to my files,except copying them to directories like /etc. When I am root I cannot do anything to those files. Why is that? I tried chmod, but still nothing. Any ideas?

---

### Post by ilrudie on 2008-08-25
how are you "becoming root"?  su? sudo?  also run the id command from the terminal when you think you are root to make sure you really are.

---

### Post by someone_yeah on 2008-08-25
I type "sudo su"and then the passwd. When I type ïd", it returns uid=0(root) gid=0(root) groups=0(root),224(imnadm)

---

### Post by ilrudie on 2008-08-25
What commands are you trying to run after you sudo su?  What output are they giving?

---

### Post by raphaelr on 2008-08-25
Enter "ls -l". It gives you the permissions of every file in the current directory. The first four letters should look like "-rwx" or "drwx" or "drw-" or "-rw-". If there is any other result enter "sudo chmod u+rwx file" to fix it.

---

### Post by -Zeus- on 2008-08-25
> **raphaelr said:**
> Enter "ls -l". It gives you the permissions of every file in the current directory. The first four letters should look like "-rwx" or "drwx" or "drw-" or "-rw-". If there is any other result enter "sudo chmod u+rwx file" to fix it.

he said as a normal user he can access it.  his problem is that root cant access it.  obviously the user permissions are set OK.

---

### Post by someone_yeah on 2008-08-26
Zeus, yes you're right. Any ideas?

---

### Post by ilrudie on 2008-08-26
I don't know what to tell you.  Root (id=0) should have totally unimpeded access to everything.  Even if you specifically deny root in the file permissions root should still have access.  Is this a new install or did this just start happening?  If it just started happening what were you trying to do when it broke?

---

### Post by pmlxuser on 2008-08-26
> **someone_yeah said:**
> I type "sudo su"and then the passwd.

what happens if you run the command as 
```

$ sudo command 

```

usually do that and can access everything on my system.

---

