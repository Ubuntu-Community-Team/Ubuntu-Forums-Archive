---
title: "Is there an apt repository for the newest versions Scipy, Numpy and Matplotlib?"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by helstreak on 2009-03-11
I was wondering if there were repositories for Scipy, Numpy and Matplotlib for Ubuntu 8.04.

There is this:
[https://edge.launchpad.net/~scipy/+archive/ppa](https://edge.launchpad.net/~scipy/+archive/ppa)
but its for Intrepid.

Any help would be nice.

Thanks in advance.

---

### Post by martrn on 2009-03-11
> **helstreak said:**
> I was wondering if there were repositories for Scipy, Numpy and Matplotlib for Ubuntu 8.04.... There is this:
[https://edge.launchpad.net/~scipy/+archive/ppa](https://edge.launchpad.net/~scipy/+archive/ppa)
but its for Intrepid....Any help would be nice.....Thanks in advance.

From the URL you gave it says : Description

This archive contains the latest release or release candidate of numpy and scipy, built for all currently supported Ubuntu releases.

That means unless there is some major modifications to the functionality of the underlying libraries then it has been built for and will continue to work with Ubuntu 8.04(LTS).

---

### Post by helstreak on 2009-03-11
> **martrn said:**
> From the URL you gave it says : Description

This archive contains the latest release or release candidate of numpy and scipy, built for all currently supported Ubuntu releases.

That means unless there is some major modifications to the functionality of the underlying libraries then it has been built for and will continue to work with Ubuntu 8.04(LTS).

Scipy and Numpy show up but when I try to install Numpy, I get an error message:

python-numpy:
 Depends: libgfortran3 (>=4.3) but it is not installable

I can't seem to find what it's asking for either....

---

### Post by martrn on 2009-03-11
[http://packages.debian.org/lenny/libgfortran3]("http://packages.debian.org/lenny/libgfortran3").

Ok this is a debian package, but I cant find it in the ubuntu repositories at all.

I did a searh for it in the 8.04 repositories but it is not in them or the backports repository either :
~m  $sudo apt-cache search libgfortran
libgfortran1 - Runtime library for GNU Fortran applications
libgfortran2 - Runtime library for GNU Fortran applications
libgfortran2-dbg - Runtime library for GNU Fortran applications (debug symbols)

You can install it from the ubuntu repository's if you can find it, but there is no guarantee it will work.

You are looking for an ubuntu package called 'libgfortran3' which is greater than version 4.3.xx

There is a i386 binary here :
[https://launchpad.net/ubuntu/jaunty/i386/libgfortran3/4.3.2-2ubuntu7]("https://launchpad.net/ubuntu/jaunty/i386/libgfortran3/4.3.2-2ubuntu7")  (Make sure you get the binary), it might work. ?

---

### Post by helstreak on 2009-03-11
> **martrn said:**
> [http://packages.debian.org/lenny/libgfortran3]("http://packages.debian.org/lenny/libgfortran3").

Ok this is a debian package, but I cant find it in the ubuntu repositories at all.

I did a searh for it in the 8.04 repositories but it is not in them or the backports repository either :
~m  $sudo apt-cache search libgfortran
libgfortran1 - Runtime library for GNU Fortran applications
libgfortran2 - Runtime library for GNU Fortran applications
libgfortran2-dbg - Runtime library for GNU Fortran applications (debug symbols)

You can install it from the ubuntu repository's if you can find it, but there is no guarantee it will work.

You are looking for an ubuntu package called 'libgfortran3' which is greater than version 4.3.xx

There is a i386 binary here :
[https://launchpad.net/ubuntu/jaunty/i386/libgfortran3/4.3.2-2ubuntu7]("https://launchpad.net/ubuntu/jaunty/i386/libgfortran3/4.3.2-2ubuntu7")  (Make sure you get the binary), it might work. ?


urg...so how do they expect you to get the updated version of the software if you can't even get a key component for the install?

---

### Post by MethodsMan on 2010-04-16
Did you ever get anything to workout for you?  I decided to go ahead and upgrade ubuntu.

---

