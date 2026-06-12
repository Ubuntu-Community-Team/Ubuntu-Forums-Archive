---
title: "Compressing directories"
date: 2008-09-27
forum: General Help
---

### Post by capo1949 on 2008-09-27
Hi Folks
I am using the archive function when right clicking a directory or file to create a compressed archive, using zip or bz2 works but the file generated is the same size as the original?

If I use the command line i have the same problem
$ tar -zcvf bakpictures.tar.gz /home/graham/Pictures

I have checked to see that the gzip and bzip2 program is installed using synaptic

Some help would be appreciated

Many thanks in anticipation
Graham

---

### Post by kpatz on 2008-09-27
What are you trying to compress?  Pictures?  Most picture formats are already compressed (e.g. jpeg, png, gif) and can't be compressed any further.  Same for music formats like mp3, ogg, flac, etc.

---

### Post by _sAm_ on 2008-09-27
Agree with kpatz. 

But try replace z with j(it will make tar use bzip2 witch will give you a better result).

---

### Post by capo1949 on 2008-09-27
Duh, dint think of that, but it is only a binary string? is it different to any other and does the same apply to mp3 files?
Graham

---

### Post by vanadium on 2008-09-27
Most media formats are already designed to be strongly compressed and therefore cannot be compressed much further using a compression utility.

---

