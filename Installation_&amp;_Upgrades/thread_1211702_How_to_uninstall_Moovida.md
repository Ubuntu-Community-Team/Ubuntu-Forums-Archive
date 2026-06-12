---
title: "How to uninstall Moovida?"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by BigBig5 on 2009-07-12
I installed Moovida, but now I don´t want it now. I am wondering how to uninstall it. Can ayone help me?

---

### Post by cariboo on 2009-07-13
How did you install it? IF you installed it using synaptic, just search for it and mark it for removal. If you installed from source, cd into the source directory and type:

```
make uninstall
```

If you don't have the source directory any more you will have to remove it manually. Open a terminal and type:

```
locate moovida > moovida.txt
```

the above command will create a text file with the locations of all the files. You should then be able to delete the files listed.

---

### Post by Mark Phelps on 2009-07-13
> **BigBig5 said:**
> I installed Moovida, but now I don´t want it now. I am wondering how to uninstall it. Can ayone help me?

Curious about why you're removing it.  Haven't tried it, but from the little I read, it sounds amazing!

---

### Post by csabo2 on 2009-07-13
> **Mark Phelps said:**
> Curious about why you're removing it.  Haven't tried it, but from the little I read, it sounds amazing!

I found it a little buggy and resource intensive.

---

### Post by axelsvag on 2009-07-17
I have got ubuntu 9.04 amd 64 with compiz enabled and I found it completely useless. The program went outside the desktop so you can not do anything. It is impossible to shut the program down so you have to kill the process. And as you see you have to manually delete more than 40 files to be able to uninstall the program. So it is absolutely not ready for ubuntu 64 bit.

---

### Post by ArtInvent on 2009-07-21
I tried it a few months ago on 9.04 AMD64  when it was still Elisa and it was much the same, buggy, impossible to shut down, the screen took over and couldn't even switch to another app. Ugh. Sounds like it's still much the same. It would be nice if they got their act together. I have MythTV but don't really like that so much.

---

