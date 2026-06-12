---
title: "How do I build a very basic linux with only networking,kernel,busybox,AMP ?"
date: 2008-08-21
forum: General Help
---

### Post by Sycron on 2008-08-21
Is there a tut ? I have less than a week to do that.

---

### Post by amitkher on 2008-08-21
There are so many distributions already, that it is unlikely you will have to build anything. Installing the lesser known distributions might be a pain, so direct your efforts there.

If the reason for wanting to build a basic linux is that you want low resource consumption, consider damn small linux ([http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)). It will take less than 100MB hard disk space and less than 17 MB  RAM. It will not be basic however: it is a full-fledged linux with gui.

---

### Post by Sycron on 2008-08-21
> **amitkher said:**
> There are so many distributions already, that it is unlikely you will have to build anything. Installing the lesser known distributions might be a pain, so direct your efforts there.

If the reason for wanting to build a basic linux is that you want low resource consumption, consider damn small linux ([http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)). It will take less than 100MB hard disk space and less than 17 MB  RAM. It will not be basic however: it is a full-fledged linux with gui.

I tried DSL , but it's to bloated. I want something very simple... so my 486DX2 66Mhz can be a full LAMP server. I have to show this at a contest.

---

### Post by spupy on 2008-08-21
> **Sycron said:**
> I tried DSL , but it's to bloated. I want something very simple... so my 486DX2 66Mhz can be a full LAMP server. I have to show this at a contest.

The first thing that came to mind was some kind of really stripped down linux used in embedded devices.

Also, Gentoo Stage 3. Don't worry, there is no compiling involved. Stage 3 is an archive you extract in your would-be-root partition, it contains the bare working system. It is normally used to install the rest of gentoo and compile new kernel/programs, but I think you can use it for your purpose without recompiling the kernel. You still have to compile LAMP, though. And that is going to take a lot of time on that machine. Cross-compilation on another machine is possible.

Last thing: [http://www.polypux.org/](http://www.polypux.org/)
It's linux distro from a gentoo user. It is specially for 386/486 computers. But I don't know if/how you can install LAMP on it.

---

### Post by Sycron on 2008-08-21
> Also, Gentoo Stage 3. Don't worry, there is no compiling involved. Stage 3 is an archive you extract in your would-be-root partition, it contains the bare working system. It is normally used to install the rest of gentoo and compile new kernel/programs, but I think you can use it for your purpose without recompiling the kernel. You still have to compile LAMP, though. And that is going to take a lot of time on that machine. Cross-compilation on another machine is possible

Will fit on a 365MB HDD ?

---

### Post by spupy on 2008-08-21
> **Sycron said:**
> Will fit on a 365MB HDD ?

Sorry, I just found the system requirements for the latest Gentoo - they are too high.
i486 or later, 64MB RAM, 1.5GB disk + swap
DSL is smaller. I guess there could be a way to make a stripped down DSL.

---

### Post by linuxguymarshall on 2008-08-21
Google "Linux From Scratch"

---

### Post by Sycron on 2008-08-21
> **linuxguymarshall said:**
> Google "Linux From Scratch"

I read it a bit, but i don't have time to do it. I think DSL it's doing his job inspite is bloated... :)

I need more space.. lol I've downloaded mysql ,untar-ed it and it has 390MB. I need a new HDD...

---

### Post by amitkher on 2008-08-22
> **spupy said:**
> Sorry, I just found the system requirements for the latest Gentoo - they are too high.
i486 or later, 64MB RAM, 1.5GB disk + swap
DSL is smaller. I guess there could be a way to make a stripped down DSL.

DSL needs less than 100MB disk space to install.

---

### Post by tuxulin on 2008-08-22
i think you need to roll ya own linux.
here is another starting point in doing just that

[http://custom.nimblex.net/](http://custom.nimblex.net/)

[http://hehe2.net/linuxhowto/create-your-own-linux-distro/](http://hehe2.net/linuxhowto/create-your-own-linux-distro/)

i hope this might help
Tuxulin

---

