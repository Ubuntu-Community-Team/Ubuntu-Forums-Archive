---
title: "Compiling makehuman 0.9.1"
date: 2008-11-05
forum: General Help
---

### Post by Anarchid on 2008-11-05
Hi. I have tried to compile Makehuman on Xubuntu Intrepid, and failed thoroughly.

While everything so far seems to do the ./configure, the consequential make (starting with the animorph package) rants about some "str" functions not being defined in the current context.

I suspect this is a slashback from my system being dependency-borked on libc6 prior to its upgrade to Intrepid.

Can anyone give me any insight on how to circumvent this trouble?

---

### Post by Tindytim on 2008-11-06
I had similar issues, what is the exact error?

---

### Post by Anarchid on 2008-11-06
"strlen is not declared in this scope".

However, the topic name is thus a misnomer: attempting to compile dunelegacy ranted about not finding uint32.

I have a sneaking suspicion i need to (re)install some c headers, but i already have revamped my build-essential and all of its dependencies, including libstdc-dev and libc6-dev...

---

### Post by Yellow Pasque on 2008-11-06
I believe I tried compiling makehuman/animorph for someone once and got similar compilation errors (Ubuntu 8.10, no dependency "borking").

---

### Post by Yellow Pasque on 2008-11-06
Ah, this might answer some ?'s
[http://gcc.gnu.org/gcc-4.3/porting_to.html](http://gcc.gnu.org/gcc-4.3/porting_to.html)

---

### Post by Anarchid on 2008-11-06
Hm, then perhaps it has something to do with Intrepid itself? Possibly, its use of a later version gcc/libc6? :P

---

### Post by Anarchid on 2008-11-06
> Ah, this might answer some ?'s
[http://gcc.gnu.org/gcc-4.3/porting_to.html](http://gcc.gnu.org/gcc-4.3/porting_to.html)
Ahhah. I knew i would find a use for that emacs thingy. ^^

---

