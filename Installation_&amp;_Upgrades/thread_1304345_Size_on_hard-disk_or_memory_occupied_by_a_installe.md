---
title: "Size on hard-disk or memory occupied by a installed software !"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by chinmaya_n on 2009-10-29
HI

I would like to know the space occupied by an installed software in my Linux system!
What is the command for that?
Is there any GUI software that can do it?
Actually synaptic clearly shows while installing but Add/Remove dont!:(

Thanx

---

### Post by Mighty_Joe on 2009-10-29
```
df -h
```

[Gnome Disk Usage Analyzer]("http://library.gnome.org/users/baobab/")

---

### Post by Lord Landis on 2009-10-29
If you're looking for the size of a single application, that's kind of difficult to judge.  The problem is that the application doesn't live by itself - there are all sorts of dependencies and whatnot that you have to figure in, and not everything lives in the same folder.

Now, if you know the name of the binary itself (atanks, for example), you can see how large it is by doing the following:

```
sudo find / -type f | grep <name of program>
du <full path to binary> -hs
```

As an example, if I do this for SSH, I get this:

```
sudo find / -type f | grep ssh
```
*results that you need to sort through*
```
du /usr/bin/ssh -hs
```
**332K    /usr/bin/ssh**

Another option is to find the size of the .deb itself, which you can do like this:

```
ls -lh /var/cache/apt/archives
```

Since these are packages, however, the size you see on the file may not be truly reflective of the size of the installed application.

I hope this helps in some way.

---

### Post by chinmaya_n on 2009-10-29
> **Mighty_Joe said:**
> ```
df -h
```

[Gnome Disk Usage Analyzer]("http://library.gnome.org/users/baobab/")

**df -h** gives the disk usages but i'm asking for the usage of the space by a specific application !!
and Gnome disk usage analyzer shows the usage of hard-disk space by the files and folders but not of a specific application like amarok or openoffice etc., !

---

### Post by chinmaya_n on 2009-10-30
> **Lord Landis said:**
> If you're looking for the size of a single application, that's kind of difficult to judge.  The problem is that the application doesn't live by itself - there are all sorts of dependencies and whatnot that you have to figure in, and not everything lives in the same folder.

Now, if you know the name of the binary itself (atanks, for example), you can see how large it is by doing the following:

```
sudo find / -type f | grep <name of program>
du <full path to binary> -hs
```

.
.
.
.

Since these are packages, however, the size you see on the file may not be truly reflective of the size of the installed application.

I hope this helps in some way.

Thanx... But I could not get the exact result i'm looking for.

I've got an idea!
By finding the sizes of all the files which are needed by that application we can do it (may be we can't get exact size of the  whole application)... Can't we get it through a command like : first it gets all its installed files and pipes to find their sizes all together!!

---

### Post by Mighty_Joe on 2009-10-30
> **chinmaya_n said:**
> **df -h** gives the disk usages but i'm asking for the usage of the space by a specific application !!
and Gnome disk usage analyzer shows the usage of hard-disk space by the files and folders but not of a specific application like amarok or openoffice etc., !

Sorry.  Your question was a little on the vague side.
I wonder if the size of the package would give you a clue or if the packages are compressed in some way.

---

### Post by chinmaya_n on 2009-10-30
> **Mighty_Joe said:**
> Sorry.  Your question was a little on the vague side.
I wonder if the size of the package would give you a clue or if the packages are compressed in some way.

Ok ... I let us change like this :
If i remove an application how much space will be freed !!
and if I install it how much will it take ?

---

