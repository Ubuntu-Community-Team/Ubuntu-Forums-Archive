---
title: "problems compiling polipo, makeinfo"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by chaosdesigner on 2009-10-05
Hey guys,

Im trying to install polipo and im having problems compiling it. I did 'make all' and got this error at the end:

```
makeinfo polipo.texi
make: makeinfo: Command not found
make: *** [polipo.info] Error 127

```

The same comes when i trie to make install:


```
 user@workstation:~/Downloads/polipo-1.0.4$ sudo make install
makeinfo polipo.texi
make: makeinfo: Command not found
make: *** [polipo.info] Error 127

```

Any help on how to fix this? Im sure im just missing something obvious ...


thank you!

---

### Post by inobe on 2009-10-05
you can use apt to get the same exact version.

any reason why you are trying to compile from source ?

i will be more than glad to try it myself except for a good enough reason.

---

### Post by chaosdesigner on 2009-10-06
There is none, you are right. Thank you for the nudge :).

---

### Post by inobe on 2009-10-06
your welcome

-------------------------------------------------------------------------

i originally thought a newer version was available at polipo's site and decided to check, i then made a comparison to one searching in synaptic to see if it was older, old applications tend to lack feature's so i assumed this is why you tried compiling from source considering it takes a bit long for newer applications to be added to ubuntu repositories.

always make comparisons

---

### Post by chaosdesigner on 2009-10-06
well you are right that was first the reason for me to get it from source. It did tell me on the page that it was apt-gettable but i wanted to make sure i got the newest. I downloaded it from the repository now and it is the same version. So worked out fine. Still wondering though why it didnt compile...

---

### Post by enjoygo on 2009-11-30
sudo apt-get install texinfo

---

