---
title: "[Newbie] problem when using sudo + [command]"
date: 2008-08-10
forum: General Help
---

### Post by asaf.lahav on 2008-08-10
Hi all,
For some reason, i'm getting the following note each time i'm using sudo.
e.g, 

*When I executed the following command:*
my@my-laptop:/etc/resolvconf$ sudo gedit resolv.conf.d
I got this:
*sudo: unable to resolve host my-laptop*

Any idea why is that?
Thanks in advance,
Asaf

---

### Post by Sycron on 2008-08-10
Try this:
```
$ gksudo gedit /etc/resolv.conf
```

---

### Post by asaf.lahav on 2008-08-10
Sycron,
That command works with no apparent problems.
Do you have any idea what causes the problem I encounter when I use the 'sudo' command instead of the 'gksudo'?
Thanks

---

### Post by Sycron on 2008-08-10
You can use **gksudo** for graphical programs and **sudo** for console programs.
Did you tried:
```
$ gksudo gedit /etc/resolvconf/resolv.conf.d
```

---

### Post by linux_tech on 2008-08-10
This page explains the differences between gksudo and sudo -

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by asaf.lahav on 2008-08-10
> **Sycron said:**
> You can use **gksudo** for graphical programs and **sudo** for console programs.
Did you tried:
```
$ gksudo gedit /etc/resolvconf/resolv.conf.d
```
I just tried: $ gksudo gedit /etc/resolvconf/resolv.conf.d/back
It appears as if some administrative application is being started, yet nothing happens.

---

### Post by asaf.lahav on 2008-08-10
> **linux_tech said:**
> This page explains the differences between gksudo and sudo -

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Thanks...

---

### Post by Sycron on 2008-08-10
The file doesn't exist maybe. But it should open a blank gedit window.
gksudo gedit /etc/resolvconf/resolv.conf.d**/back** Did you typed **/back** ?

---

### Post by asaf.lahav on 2008-08-10
> **Sycron said:**
> The file doesn't exist maybe. But it should open a blank gedit window.
gksudo gedit /etc/resolvconf/resolv.conf.d**/back** Did you typed **/back** ?

nope nope nope :`)
i ment base

---

### Post by Sycron on 2008-08-10
What are you trying to do... i don't have **/back** folder.

---

### Post by rp3 on 2008-08-10
> **Sycron said:**
> What are you trying to do... i don't have **/back** folder.

I fixed this by doing this

gksudo gedit /etc/hosts

on the line that has 127.0.1.1 hostname.xxx

remove the .xxx save file and sudo should work.

I saw that fix here, not sure it's right or wrong but seems to work fine after that.

---

### Post by Mister.Vash on 2008-08-10
The sudo error is reported here
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/195308](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/195308)

Basically, the hostname just needs to be fixed.  If you have trouble with this, post the output of the command hostname and contents of your /etc/hosts file

---

