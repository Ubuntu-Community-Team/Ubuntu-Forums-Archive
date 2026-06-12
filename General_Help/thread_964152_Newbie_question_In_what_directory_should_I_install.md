---
title: "Newbie question: In what directory should I install programs?"
date: 2008-10-30
forum: General Help
---

### Post by zachbb on 2008-10-30
Hi everyone

I have two typical newbie questions, but please be nice with me!


1. If i want to install a program without going through a package manager (say I want to install a .bin file), where should I install it?

If I have for instance want to install google:
```
wget http://whatever/googleearth.bin
sh ./googleearth.bin
```

Where should I install it? That is - What directory is the common install directory? Is it /usr? /usr/bin? Or just my home directory?


2. I installed google earth with the above method and it launches from the terminal, but I do not see Google Earth in the applications menu. I know some people managed to get it into their applications -> Internet menu. How do I do this?


Thanks!

---

### Post by nothingspecial on 2008-10-31
Ubuntu will install it where it needs to go. You can compile it/install it from wherever you like.

---

### Post by Naegling23 on 2008-10-31
usually the programs will install themselves where they need to go.  Otherwise, the home directory is best since you dont have to mess with permissions to put stuff in there (ie, its just easier).  As for google earth...google now has a linux repository, try searching for it, once you have it set up you can just install everything through synaptic/apt/adept to make everything easier.

---

### Post by employeeno5 on 2008-10-31
Yes, in the case of Google Earth, that installer will put it where it needs to be. 

Sometimes though, if you're downloading programs that aren't part of the repositories, you just unpack them and run them. The Songbird beta might be a good example of that. 

Though, not using the official repositories is not recommended by Ubuntu.

Traditionally, a place to put these programs might be in a folder labeled "bin" in your home folder. Folders named "bin" are where executable programs usually end up in Unix-like systems, so one in your home folder would be a sensible place to have stand alone programs that run only under your account. Truth be told though, you could put it anywhere you like.

Having an automated installer though, like your Google Earth file, or better yet using repositories and Debian packages prevents any need of that though, which helps to keep things the way we like it, nice and clean.

---

