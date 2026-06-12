---
title: "Error compiling from source"
date: 2008-09-01
forum: General Help
---

### Post by Charlie708 on 2008-09-01
I am on the path of compiling Linux from Scratch, but am bumping into an error when trying compile binutils-2.17.  The directions are in _[Chapter 5.3](http://www.linuxfromscratch.org/lfs/view/stable/chapter05/binutils-pass1.html)_, but I am bumping into a very annoying error.  Output just before fail:
```
make[2]: Entering directory `/home/lfs/binutils-build/libiberty'
if [ x"" != x ] && [ ! -d pic ]; then \
	  mkdir pic; \
	else true; fi
touch stamp-picdir
make[2]: execvp: touch: Too many levels of symbolic links
make[2]: *** [stamp-picdir] Error 127
make[2]: Leaving directory `/home/lfs/binutils-build/libiberty'
make[1]: *** [all-libiberty] Error 2
make[1]: Leaving directory `/home/lfs/binutils-build'
make: *** [all] Error 2

```

I am assuming this is from Ubuntu lacking all the tools needed for compiling, but I have installed all compilation tools I could find.  I am all out of ideas with this one, anyone bump into this before?

---

### Post by Zill on 2008-09-01
> **Charlie708 said:**
> I am on the path of compiling Linux from Scratch...
I can't quite see why you are asking this question on an Ubuntu forum.  We tend to use deb packages rather than compilation ;-)

---

### Post by Charlie708 on 2008-09-01
I know, I know, but to do it you need a host OS, and Ubuntu seemed ready for the task.  I want to get into the nity-grity stuff, and this is an excellent way of doing it.

---

### Post by cariboo on 2008-09-01
If I remember correctly Linux From Scratch runs in a chrooted environment. so it really shouldn't have anything to do with the host system.

Jim

---

### Post by Charlie708 on 2008-09-01
It does, but not yet.  The host is still needed for the rest of chapter 5.

---

### Post by monkeyking on 2008-09-01
I'm not really sure I understand what you are doing.
But you need build-essential.

And the problem with the "to many symbolic links".
I think the most likely cause is that a link point back to somewhere earlier in your filesystem tree traversal.

I would start allover, scratch , or just boot from live cd again.

---

### Post by xeth_delta on 2008-09-01
> **Charlie708 said:**
> Output just before fail:
```
make[2]: Entering directory `/home/lfs/binutils-build/libiberty'
if [ x"" != x ] && [ ! -d pic ]; then \
	  mkdir pic; \
	else true; fi
touch stamp-picdir
make[2]: execvp: touch: Too many levels of symbolic links
make[2]: *** [stamp-picdir] Error 127
make[2]: Leaving directory `/home/lfs/binutils-build/libiberty'
make[1]: *** [all-libiberty] Error 2
make[1]: Leaving directory `/home/lfs/binutils-build'
make: *** [all] Error 2

```


The "too many levels" error can happen when you have circular symbolic links, the loop would be infinite.

Is this the only error? It does not seem to be a compilation error per se, as this appears to be from the Makefile.
Can you post the compilation command you issued, and what ./configure options you used (if that is used in this step)?

---

### Post by Charlie708 on 2008-09-02
I think it may be related to the LFS user on the host system.  Under myself I can use make and view the man file for make, but under LFS viewing the man file and using it generates the loop error.

```

lfs@5000be:~$ man make
man: can't execute pager: Too many levels of symbolic links

```

Edit:
It was the user.  Root compiled binutils no problem.  I am not exactly sure what caused the problem, but I did follow the directions exactly as they are in [4.3](http://www.linuxfromscratch.org/lfs/view/stable/chapter04/addinguser.html) for adding the LFS user.

---

