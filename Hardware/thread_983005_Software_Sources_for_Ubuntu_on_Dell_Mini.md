---
title: "Software Sources for Ubuntu on Dell Mini"
date: 2008-11-15
forum: Hardware
---

### Post by JamieV on 2008-11-15
I just acquired a Dell Inspiron 910, the new mini.  I bought it with Ubuntu pre-installed.  The links displayed in the Software Sources utility don't work - the update manager reports it "failed to fetch" each of the URLs listed in the Software Source.

What should these URLs be?

---

### Post by taurus on 2008-11-15
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by JamieV on 2008-11-15
Here it is:

# deb [http://dell-mini.archive.canonical.com/dists/](http://dell-mini.archive.canonical.com/dists/) hardy main universe multiverse restricted
# deb-src [http://dell-mini.archive.canonical.com/dists/](http://dell-mini.archive.canonical.com/dists/) hardy main universe multiverse restricted

# deb [http://dell-mini.archive.canonical.com/dists/hardy-updates/](http://dell-mini.archive.canonical.com/dists/hardy-updates/) hardy-updates main universe multiverse restricted
# deb-src [http://dell-mini.archive.canonical.com/dists/hardy-updates/](http://dell-mini.archive.canonical.com/dists/hardy-updates/) hardy-updates main universe multiverse restricted

# deb [http://dell-mini.archive.canonical.com/dists/hardy-security/](http://dell-mini.archive.canonical.com/dists/hardy-security/) hardy-security main universe multiverse restricted
# deb-src [http://dell-mini.archive.canonical.com/dists/hardy-security/](http://dell-mini.archive.canonical.com/dists/hardy-security/) hardy-security main universe multiverse restricted

# deb [http://dell-mini.archive.canonical.com/dists/hardy-security/](http://dell-mini.archive.canonical.com/dists/hardy-security/) hardy-netbook-base main universe multiverse restricted
# deb-src [http://dell-mini.archive.canonical.com/dists/hardy-security/](http://dell-mini.archive.canonical.com/dists/hardy-security/) hardy-netbook-base main universe multiverse restricted

# deb [http://dell-mini.archive.canonical.com/dists/hardy-dell-mini/](http://dell-mini.archive.canonical.com/dists/hardy-dell-mini/) hardy-dell-mini main universe multiverse restricted
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy main universe restricted multiverse
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy main universe restricted multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main restricted multiverse #Added by software-properties
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-updates universe main restricted multiverse
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-updates universe main restricted multiverse #Added by software-properties
# deb-src [http://dell-mini.archive.canonical.com/dists/hardy-dell-mini/](http://dell-mini.archive.canonical.com/dists/hardy-dell-mini/) hardy-dell-mini main universe multiverse restricted

---

### Post by pleinad on 2008-11-17
Hello! This is my working configuration:

user@myMiniDell:~$ cat /etc/apt/sources.list

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

I hope this will help you.

---

### Post by JamieV on 2008-11-17
That did it!!

Tanks - a - gallon!

:KS

---

