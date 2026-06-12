---
title: "tar.bz2"
date: 2008-10-03
forum: General Help
---

### Post by witblits1970 on 2008-10-03
how do i install a tar.bz2 file that is downloaded from the net?
please be gentle as this is new to me?!
thanks

---

### Post by bodhi.zazen on 2008-10-03
A tar is an archive, like a zip file. You extract the contents and install from there.

Most are source code.

You need to first install the dependencies , then 

```
./configure --prefix=/usr
make
sudo make install
```

What are you trying to install and why are you not using the repositories ? What how-to are you following ?

There should be a README in the archive.

[http://sunsite.ualberta.ca/Documentation/Gnu/tar-1.13/html_chapter/tar_2.html](http://sunsite.ualberta.ca/Documentation/Gnu/tar-1.13/html_chapter/tar_2.html)

---

### Post by Calmatory on 2008-10-03
and to extract the file via CLI:

```
tar -xvf file.tar.gz
```

By default, files are being extracted to the current folder. However, this can be changed with the command line options if necessary.

---

### Post by aysiu on 2008-10-03
What software is it?

I ask this question for two reasons:

1. New users often don't realize that downloading a .tar.bz2 is not easiest or preferred method for installing software on Ubuntu.

2. A file with a .tar.bz2 extension is a compressed file. That's all we know. Some .tar.bz2 files contain source code that needs to be compiled. Some contain precompiled binaries. There is no standard approach to software distributed as a compressed file.

For more information about installing software, check out: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by mindoms on 2008-10-03
> **Calmatory said:**
> and to extract the file via CLI:

```
tar -xvf file.tar.gz
```

By default, files are being extracted to the current folder. However, this can be changed with the command line options if necessary.

he/she needs to inflate a tar.bz2 file. so i guess the -j switch would be fine:

```

tar -xvjf file.tar.bz2
```

for tar.gz you need -xvzf file.tar.gz

but, as aysiu mentioned before, there is almost always a better/easier way to install new software in ubuntu

---

### Post by Calmatory on 2008-10-03
> **mindoms said:**
> he/she needs to inflate a tar.bz2 file. so i guess the -j switch would be fine:

```

tar -xvjf file.tar.bz2
```

for tar.gz you need -xvzf file.tar.gz

but, as aysiu mentioned before, there is almost always a better/easier way to install new software in ubuntu

My bad. Thanks for correction. :)

---

### Post by oldos2er on 2008-10-03
> **witblits1970 said:**
> how do i install a tar.bz2 file that is downloaded from the net?
please be gentle as this is new to me?!
thanks

 Instead of doing that, please read this first: [https://help.ubuntu.com/](https://help.ubuntu.com/)
 Especially the section on adding and removing software.

---

### Post by MunkyJunky on 2008-10-03
As a  quick note of reference, you can also extract archive files by right clicking the folder, right clicking and choosing 'extract here'. 

Useful, if like me, your too lazy to do it through terminal all the time.

---

### Post by witblits1970 on 2008-10-04
the right click and extract here is ok. that i can do but it is what do i do with the folder icon on the desktop. hotmail has changed some stuff and now i need to update my software so i can access the site without any issues. the file comes down as firefox3.0.2.tar.bz2 or something like that. hope this helps, it is the only thing in my linux experience that i cant do so i want to learn how to do this as i have told loads of my friends about linux but i cant help them on this issue!thanks

---

### Post by aysiu on 2008-10-04
> **witblits1970 said:**
> the right click and extract here is ok. that i can do but it is what do i do with the folder icon on the desktop. hotmail has changed some stuff and now i need to update my software so i can access the site without any issues. the file comes down as firefox3.0.2.tar.bz2 or something like that. hope this helps, it is the only thing in my linux experience that i cant do so i want to learn how to do this as i have told loads of my friends about linux but i cant help them on this issue!thanks
There's no need for a manual download.

Firefox 3.0.3 is already in the repositories.

If you don't know what *in the repositories* and *manual download* mean, then you **really** need to read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If you're using an older version of Ubuntu (not 8.04) and want Firefox 3.03, then this will help you with the .tar.bz2 file:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

