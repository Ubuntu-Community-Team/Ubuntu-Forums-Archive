---
title: "Help finding server location"
date: 2008-08-11
forum: General Help
---

### Post by Adeang on 2008-08-11
I have a problem, I have installed LAMPP I think, and when I type [http://localhost](http://localhost) in firefox it has a page that says It WORKS!  but i want to know where that file is located so I can use the server.  I dont really know what I am asking I just want to know where or how to find the location of that file.  Im pretty good with computers, but i dont know how to trace [http://localhost](http://localhost) back to a folder so could someone please help me.

---

### Post by jonabyte on 2008-08-12
it is located in:

```
/var/www
```

you can find the conf file here:

```
/etc/apache2
```

which will also tell you where the files are located, and you can change the location as well to suit your needs.

---

### Post by Adeang on 2008-08-12
thanks you very much, but on the second code what do i look for to change to change the location?

---

### Post by Adeang on 2008-08-12
Okay I have a problem though, it says i dont have permission to save a file in that location. What do i Do:?

---

### Post by jonabyte on 2008-08-12
> **Adeang said:**
> Okay I have a problem though, it says i dont have permission to save a file in that location. What do i Do:?

use:
```
sudo cp /location/of/file /var/www
```

---

### Post by Adeang on 2008-08-12
i used to code above not sure what it is but I change /location/of/file to /home/myname/webfolder and it did something but I know for fact I still can't put a file in the folder /var/www so please help.

---

### Post by colobix on 2008-08-12
Here you go for full access to add/remove files:

gksudo nautilus

---

### Post by Adeang on 2008-08-12
thank you very much it worked!

---

