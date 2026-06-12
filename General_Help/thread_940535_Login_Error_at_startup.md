---
title: "Login Error at startup"
date: 2008-10-07
forum: General Help
---

### Post by RJWEcology on 2008-10-07
Sorry to be a bother, but I've recently just got this weird error when I log in. 

[http://i472.photobucket.com/albums/rr83/RJWEcology/DSC01395.jpg](http://i472.photobucket.com/albums/rr83/RJWEcology/DSC01395.jpg)

Does anyone know what it's about or how I could fix this? 

Any help would be much appreciated. 

Cheers, Rich

---

### Post by neilengineer on 2008-10-07
permission problem!

Change the permission of everything in /home/$USER back to 644(maybe)?

---

### Post by justleen on 2008-10-07
to make sure the home dir is owned by te user:
```

chown -R username:username $HOME

```
to change the attributes to 644 on the file:
```

chmod 644 $HOME/.dmrc

```

according to the error, that hsould fix it

---

### Post by justleen on 2008-10-07
> **neilengineer said:**
> permission problem!

Change the permission of everything in /home/$USER back to 644(maybe)?

DONT change the persmission of everything to 644! just of the .dmrc files! (as it says in the error msg)

---

### Post by RJWEcology on 2008-10-07
Thanks. I'll igve that a try. Much appreciated :)

---

### Post by RJWEcology on 2008-10-07
I get this when I try the second code:

> cannot access `/root/.dmrc': No such file or directory

Edit: I managed both codes but I still get that error at startup.

---

### Post by justleen on 2008-10-07
erm, when you are root, $HOME is something different offcourse..

can you check that /home/youruser/.dmrc is actually owned by youruser and is rw by only that user?

-rw------- 1 youruser youruser   28 2008-10-07 09:19 .dmrc

and check  the directory /home/youruser

drwxr-xr-x 58 youruser youruser 4096 2008-10-07 14:39 youruser

---

### Post by RJWEcology on 2008-10-07
In my home folder, logged in a me (rich) it's properties are: 

Owner: Rich (Read and Write)
Group: Root
Access: Read only 
Others: Read only

---

### Post by RJWEcology on 2008-10-08
bump*

---

### Post by RJWEcology on 2008-10-09
Bump... for the last time :( Then I'll give up.

---

