---
title: "Trouble compiling cairo-dock"
date: 2008-10-23
forum: General Help
---

### Post by Idefix82 on 2008-10-23
I am trying to compile cairo-dock with glitz enabled following this guide:
[http://ubuntuforums.org/showthread.php?t=924242]("http://ubuntuforums.org/showthread.php?t=924242")
But when I try to compile pixman from source and type in
```
sudo ./configure --prefix=/usr && make
```
I get the error
```
pixman-access.c:1686: fatal error: opening dependency file .deps/pixman-access.Tpo: Permission denied
```
The same happens when I try to compile glitz. This is the first time I am compiling something from source so my suspicion is that I am lacking some dependencies.
Thanks in advance!

---

### Post by fabounet on 2008-10-24
you shouldn't be root to execute configure and make
only make install needs to be root.
so try a chmod -R / chown -R on your folders, and restart the process.
be careful to grab the last glitz version on git, and not the 0.5.6

---

### Post by Idefix82 on 2008-10-24
Thanks for the tips! I will give it a try tonight.
On a related noet: does the dock get noticeably more responsive or is it not worth the time spent, other than for educational value?

---

### Post by fabounet on 2008-10-27
it makes the dock use OpenGL, so you can guess the result. ^_^
but don't expect a perfect result, as glitz is under heavy development.

---

