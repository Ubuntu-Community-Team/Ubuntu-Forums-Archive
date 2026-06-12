---
title: "Hello Everyone"
date: 2008-07-11
forum: General Help
---

### Post by sup3r501d13r on 2008-07-11
Hi everyone,

Today, I installed Ubuntu, overwriting Windows due to too many system intrusions in the past month. I do have a few questions though, seeing as I'm having a few problems. 

First, what is the easiest way to install software? It seems none of the packages I download function properly.

Second, my mom was doing work at home. She uses a Windows program to key in her data for work. I tried using WINE, but it was a bit too complicated for me. Can anyone help me with this? She's going to kill me if I don't get that program up and running.

Thanks,
Sup3r501d13r

---

### Post by iaculallad on 2008-07-11
Hello too and welcome. You've made a good choice on switching to Ubuntu.
The installation process is done in different ways since you can install from source (tarballs), debian binary formats (.deb), Red Hat's binary package (.rpm), and many more. To find out how to install this packages, try to read this [page]("http://monkeyblog.org/ubuntu/installing/").

And, you could always use Synaptics to install softwares located at the repositories.

For the winE part:

```
sudo apt-get update
sudo apt-get install wine
```

To launch an application in the terminal using winE:

> wine "x:\home\username\.wine\drive_c\Program Files\Filezilla\Filezilla.exe"

---

### Post by sup3r501d13r on 2008-07-11
Thanks. I downloaded the program. However, it is a Microsoft Installer Package (.msi). ..

I think I just need to do some researching. I've always done programming/hacking/everything else from Windows because I didn't have any money to buy my own computer.

---

### Post by lisati on 2008-07-11
> **sup3r501d13r said:**
> Thanks. I downloaded the program. However, it is a Microsoft Installer Package (.msi). ..

I think I just need to do some researching. I've always done programming/hacking/everything else from Windows because I didn't have any money to buy my own computer.
As a rule, programs written for Windows don't usually work on Ubuntu without help. There's a program called "Wine" available that will let you run some (but not all) windows programs.

---

### Post by sup3r501d13r on 2008-07-11
Yes I know that lol I'm not a complete idiot thanks anyway :)  and yes, I know about WINE (see original post).

---

### Post by iaculallad on 2008-07-11
> **sup3r501d13r said:**
> Thanks. I downloaded the program. However, it is a Microsoft Installer Package (.msi). ..

I think I just need to do some researching. I've always done programming/hacking/everything else from Windows because I didn't have any money to buy my own computer.

For the MSI packages, try reading [WinEHQ's native MSI]("http://wiki.winehq.org/NativeMsi") page.

---

### Post by lisati on 2008-07-11
> **sup3r501d13r said:**
> Yes I know that lol I'm not a complete idiot thanks anyway :)  and yes, I know about WINE (see original post).My bad, no offense intended.

---

### Post by sup3r501d13r on 2008-07-11
Thanks I'll check that out.

---

### Post by sup3r501d13r on 2008-07-11
Yes I didn't mean it like that. Thanks for your help :)

---

