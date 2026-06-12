---
title: "libGL.so not found!?!"
date: 2005-11-24
forum: General Help
---

### Post by cataath on 2005-11-24
Hi everyone,

I recently installed a Linux game called  "Descent 3". When I tried to run it I got an error message that said "failed to load the library [libGL.so]".

I searched the file system and the best I could come up with is that there are a couple of files that are called "libGL.so.1". I'm guessing that since this is a game the file its trying to find is an openGL library file. I checked in Synaptic and the entry for OpenGL shows that I have it installed. Is it possible that there is a library file that I don't have that should be installed? Or is libGL.so.1 the file that it should be looking for?

I'm new to Ubuntu & Linux and am still trying to grok the whole file structure/dependancy thing. Any help would be really appeciated.

---

### Post by teaker1s on 2005-11-24
you can force install to use a newer library-someone will tell you more as I'm new to linux:KS

---

### Post by mlomker on 2005-11-24
You're right that it is related to video.  Normally that file is just a link in /usr/lib:

```

mlomker@mlomkernote:/usr/lib$ ls -l libGL.so*
lrwxrwxrwx  1 root root     10 2005-10-25 08:15 libGL.so -> libGL.so.1
lrwxrwxrwx  1 root root     12 2005-10-25 08:15 libGL.so.1 -> libGL.so.1.2
-rwxr-xr-x  1 root root 704504 2005-10-27 10:31 libGL.so.1.2

```

---

### Post by cataath on 2005-11-25
[QUOTE=teaker1s]you can force install to use a newer library-someone will tell you more as I'm new to linux:KS[/QUOTE]

Is this something that one has to do during the installation process, or is it like a an .ini file associated with the program that one has to edit?

---

### Post by triptoe on 2007-09-14
./descent3_demo -g /usr/lib/libGL.so.1

---

