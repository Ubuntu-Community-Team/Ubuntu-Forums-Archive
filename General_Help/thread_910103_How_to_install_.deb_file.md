---
title: "How to install .deb file"
date: 2008-09-04
forum: General Help
---

### Post by nislamce on 2008-09-04
Hi
After compilation a code I got 3 file as follows,
>yade-svn1294_1_i386.deb
>yade-svn1294-dbg_1_i386.deb
>yade-svn1294-dev_1_all.deb

I want to install them, what will be the terminal command?I have tried by several ways but didnot get success.

Any idea will be appreaciable.

Regards,
MNI

---

### Post by aqui_c on 2008-09-04
Hi!
I think 

dpkg --install file.deb

Should work, have you tried this?

---

### Post by nislamce on 2008-09-04
Hi,
Thank you very much for your reply.

Yes I have tried by following way

cd yade-svn1294_1_i386.deb
[COLOR="Blue"] yade-svn1294_1_i386.deb: Not a directory[/COLOR]


sudo dpkg -i ../yade-svn1294_1_i386.deb

[COLOR="Blue"]dpkg: error processing ../yade-svn1294_1_i386.deb (--install):
 cannot access archive: No such file or directory[/COLOR]

but still there are the file.

any idea?

Regards,
MNI

---

### Post by nislamce on 2008-09-04
Hi,
One more information

Source: yade-svn1498
Binary: yade-svn1498, yade-svn1498-dbg, yade-svn1498-dev

I wanted to installed binary file.

Regards,
MNI

---

### Post by panayk on 2008-09-04
Is it yade-svn1294 or yade-svn1498?

Anyway, why are you cd-ing to yade-svn1294_1_i386.deb? Just do:

sudo dpkg -i yade-svn1294_1_i386.deb from the dir the .debs are in.

---

### Post by rossjman1 on 2008-09-04
You could also just double click the file in gnome.

---

### Post by ronnielsen1 on 2008-09-04
> You could also just double click the file in gnome.
wondering why no one posted that possibility

---

### Post by pmlxuser on 2008-09-04
only one problem some .deb file have dependencies which are not fulfilled and then you have a problem using this method.

however i prefer using
```

$sudo apt-get install application

```
this method make sure that all dependencies are fulfilled. the draw back sometimes you have to manually add deb source to the repository which is not always easy (to me sometimes ;)

---

