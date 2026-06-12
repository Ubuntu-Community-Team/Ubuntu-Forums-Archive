---
title: "Mounting Phone - Not sufficient rights to access"
date: 2005-11-30
forum: General Help
---

### Post by ninocass on 2005-11-30
hi all

im using the p3nfsd program to mount my phone to the /mnt/psion/ folder

im connecting using:
```

sudo p3nfsd -series60 -tty /dev/rfcomm4

```

when i enter the password it phone is sucessfully mounted on the computer.

problem is when i try and access the files i need to be root, i can access it via the terminal but id prefer to do it via GUI

i have tried to change the properties of the folder but to no avail

Thanks 

Nino

---

### Post by exXplode on 2007-06-01
Hi! I know it's been a while but I found this thread while searching for "p3nfsd root rights" and it was listed #1.

As I found the solution somewhere else in the WWW I thought I'd post it here so that everybody who is looking for it can find it more easily ;)



The solution is quite simple:
just set the suid bit for the p3nfsd binary:

```
sudo chmod +s /usr/bin/p3nfsd
```

Then you can mount the phone memory to your directory of choice without root rights (and get access to its contents as well...):
```
p3nfsd -series60 -tty /dev/rfcomm0 -dir /mnt/nokia
```

origin of the information: [http://blog.siltala.net/post/2006/06/07/Mounting-the-Nokia-9300-file-system-on-Linux-with-p3nfs](http://blog.siltala.net/post/2006/06/07/Mounting-the-Nokia-9300-file-system-on-Linux-with-p3nfs)

greetings from Munich!

---

### Post by Unconscious on 2007-06-03
How did you build p3nfsd? 

I get the following error from the build configuration script:

*compiler cannot create executables*

I'm working with the 5.19 sources, on edgy.

sorry to be such a n00b.

---

### Post by k1001001 on 2007-06-03
To access your phone's files as root, you could run *gksudo nautilus* and have a root-access file browser.

---

### Post by Unconscious on 2007-06-14
I never did get p3nfsd compiled...  However, I downloaded the ARCH-Linux binaries adn installed them and it works just fine. :)

---

