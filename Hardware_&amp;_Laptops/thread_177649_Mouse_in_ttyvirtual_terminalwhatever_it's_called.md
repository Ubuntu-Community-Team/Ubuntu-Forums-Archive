---
title: "Mouse in tty/virtual terminal/whatever it's called?"
date: 2006-05-16
forum: Hardware &amp; Laptops
---

### Post by PatrickMay16 on 2006-05-16
Hello there. I recently tried using elinks, and noticed that you can use the mouse with it. I was running it in xterm. 
I remember being able to use the mouse in the tty thing (the console that you switch to using alt + ctrl + F1-6. I'm not sure what it's called exactly) when I was using my older sister's computer, who is using Slackware Linux.
Right now, I can't use the mouse in the tty thing on my Ubuntu machine. 

My question is, how do you enable use of the mouse in the tty/virtual terminal or whatever it's called? I'd appreciate any help on this.

---

### Post by kko1 on 2006-05-17
Hello.

[QUOTE=PatrickMay16]I remember being able to use the mouse in the tty thing (the console that you switch to using alt + ctrl + F1-6. I'm not sure what it's called exactly) when I was using my older sister's computer, who is using Slackware Linux.[/QUOTE]
Yup, it is standard stuff in Slackware.

[QUOTE=PatrickMay16]My question is, how do you enable use of the mouse in the tty/virtual terminal or whatever it's called? I'd appreciate any help on this.[/QUOTE]
I didn't remember the package name, so I searched the package data base. ;) You can do it for instance in Synaptic or from console line. This command helps:
```
apt-cache search console mouse
```
...and turns up a package called gpm, which stands for "General Purpose Mouse Interface". That's what Slackware uses too.

```
apt-cache show gpm
```
...gives you a description, if you insist on doing it from the command line. :p

I haven't used it on Ubuntu, so cannot attest to it working. Please tell us if it does.

HTH,

kko

---

### Post by PatrickMay16 on 2006-05-23
kko1, 

I installed gpm and now I can use the mouse in the console just like I wanted to. I tested it with elinks a little bit. Though it wasn't a very extensive text, it seems to have worked fine.

Thanks very much!

---

### Post by kko1 on 2006-05-24
Nice, glad it worked. :)

kko

---

