---
title: "About compiling programs"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by frangoitia on 2009-02-11
Guys, I got some questions about compiling programs. I always follow this procedure:
- Download the source
- cd xxx
- ./configure
- make

But when i get to configure step i obtain always the message that there wasn't found any file or directory.
And I can't go on. Thats what happens for example when i try to compile banshee.

I installed build-essential and I have Hardy.

Cheers !

---

### Post by unixeducation on 2009-02-11
What are you trying to compile? Sometimes developers don't always follow the standard routine for installing software. Try reading any documentation that came with the software, too.

---

### Post by donkyhotay on 2009-02-11
Not all programs use make to compile, it just happens to be the most common. A good example of a program that doesn't use make is globulation2 which uses scons for compilation instead. Attempting to do a 
```
./configure
make
sudo make install
```
will fail simply because they don't use make. Instead for globulation2 you just
```
sudo scons install
```
which basically does the same thing. It will help if we knew what program  you are attempting to compile but generally most programs will have a readme or install file that will tell you what system they use for compiling and instructions on how to use it. It's always a good idea to read the instructions when compiling to confirm what system is being used (rather then assuming make) as well as confirm what dependencies are needed.

---

### Post by frangoitia on 2009-02-11
I'm trying to compile banshee, the version i download from the trunk. When i put ./configure, i get an error.

---

### Post by oldos2er on 2009-02-11
> **frangoitia said:**
> I'm trying to compile banshee, the version i download from the trunk. When i put ./configure, i get an error.

 And the error is ...?

---

### Post by frangoitia on 2009-02-11
> **oldos2er said:**
> And the error is ...?
It says that the file or directory doesnt exist.

---

### Post by snova on 2009-02-11
Not that error, the one from ./configure. Copy and paste it, and not just the individual line- a bit of context would be useful.

---

### Post by frangoitia on 2009-02-11
> **snova said:**
> Not that error, the one from ./configure. Copy and paste it, and not just the individual line- a bit of context would be useful.
That is the error. It says that there is no file and it dont configure anything.

---

### Post by snova on 2009-02-11
Ah. Apologies, I didn't read everything.

What does this folder contain? It might use a different build system, or it might only contain binaries.

Quick terminal command to get a directory listing:

```
ls
```

---

### Post by frangoitia on 2009-02-12
This is what i get:

admin           Banshee.sln   COPYING  gstreamer    Makefile.am  src
AUTHORS         build         data     HACKING      NEWS         tests
autogen.osx.sh  ChangeLog     docs     libbanshee   po
autogen.sh      configure.ac  extras   MAINTAINERS  README

---

### Post by oldos2er on 2009-02-12
Start by reading README, then run 'sh ./autogen.sh'

---

