---
title: "where can i download g++ package?"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by r1e1z1a on 2009-03-08
where can i download g++ package?
(i can't connect my home pc to internet for using add/remove
because of my modem zoltrix z919 3 chip is not recognized by ubuntu)
i can download g++ in my work and install in my home pc.

thanks a lot!!

---

### Post by pfdevil on 2009-03-08
```
sudo aptitude download build-essential
```

This downloads the .deb package to your current directory. I think build-essential is the correct package to get gcc, g++ etc.

You could have figured this out by reading the man pages.

```
man aptitude
```

---

### Post by binbash on 2009-03-08
sudo apt-get install g++

or you can browse and download the deb from packages.ubuntu.com

---

### Post by Partyboi2 on 2009-03-08
You can also install it from the ubuntu cd without needing a internet connection.
Open a terminal and
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

