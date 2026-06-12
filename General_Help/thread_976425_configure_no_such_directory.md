---
title: "/configure: no such directory"
date: 2008-11-09
forum: General Help
---

### Post by sardamil on 2008-11-09
Hi,

I updraded to ubuntu 8.10 (64 bit) recently and decided to try installing wine in order to being able to use the few windows progs and games I still wasn't using on linux. It seems that wine has some issues with 64 bit versions which requires you to do some manual work to get it right. I followed the steps posted on: [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)
When I got to CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure -v I ran into some problems. At first I found I had to change the gcc version, but I still keep getting this error message:

bash: ./configure: No such file or directory

Can anybody help me out here?

---

### Post by Nepherte on 2008-11-09
Why don't you install wine from the repositories? That always worked on my 64bit systems.

```
sudo apt-get install wine
```

---

### Post by sardamil on 2008-11-09
I did install it from the repositories, but then I read that stuff about the 64-bit versions and just followed the instructions. Before I did that I wasn't able to install any windows software, but that may also be due to me being a complete beginner in linux.

---

### Post by sardamil on 2008-11-09
perhaps a seriously stupid question, but what would happen if I run the command you just posted: sudo apt-get install wine ?

---

### Post by RATM_Owns on 2008-11-09
It would install wine.

---

### Post by Nepherte on 2008-11-09
> **sardamil said:**
> perhaps a seriously stupid question, but what would happen if I run the command you just posted: sudo apt-get install wine ?
That would install wine, but if you've already installed it, it would do nothing. How did you install that windows software?

The way to install the windows programs is:
```
wine programinstaller.exe
```
where programinstaller.exe is the installer of the program. Remember that not every piece of windows software will work.

---

### Post by sardamil on 2008-11-09
@RATM_owns: I knew it would install wine. What I didn't know was if installing wine while it was already installed could damage anything.

@ Nepherte: thanks, I must have missed that somehow.

---

