---
title: "Gscan2pdf Problem"
date: 2008-07-22
forum: General Help
---

### Post by natibo on 2008-07-22
I get the following error when I run gscan2pdf program.  It slows my entire system after i run it.  Gscan never opens.

[INDENT]natibo@ubuntu:~$ gscan2pdf
Can't load '/usr/local/lib/perl/5.8.8/auto/Image/Magick/Magick.so' for module Image::Magick: libgomp.so.1: shared object cannot be dlopen()ed at /usr/lib/perl/5.8/DynaLoader.pm line 225.
 at /usr/bin/gscan2pdf line 113
Compilation failed in require at /usr/bin/gscan2pdf line 113.
BEGIN failed--compilation aborted at /usr/bin/gscan2pdf line 113.
[/INDENT]

---

### Post by unutbu on 2008-07-22
Did you install both perlmagick and gscan2pdf from the official repos?

The perlmagick package provides /usr/lib/perl5/auto/Image/Magick/Magick.so.
For some reason your gscan2pdf is looking for it at /usr/local/lib/perl/5.8.8/auto/Image/Magick/Magick.so. 

If you are not adamant about having a certain version of gscan2pdf,
then I suggest uninstalling gscan2pdf, then enabling only the official repos, and then installing gscan2pdf again.

If that does not work, please post
```
apt-cache policy gscan2pdf
apt-cache policy perlmagick
```

---

### Post by natibo on 2008-07-22
Still have the problem.  Here is the output you requested.

[INDENT]natibo@ubuntu:~$ apt-cache policy gscan2pdf
gscan2pdf:
  Installed: 0.9.21-1ubuntu4
  Candidate: 0.9.21-1ubuntu4
  Version table:
 *** 0.9.21-1ubuntu4 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
        100 /var/lib/dpkg/status
natibo@ubuntu:~$ apt-cache policy perlmagick
perlmagick:
  Installed: 7:6.3.7.9.dfsg1-2ubuntu1
  Candidate: 7:6.3.7.9.dfsg1-2ubuntu1
  Version table:
 *** 7:6.3.7.9.dfsg1-2ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
        100 /var/lib/dpkg/status
natibo@ubuntu:~$ 
[/INDENT]

---

### Post by unutbu on 2008-07-22
This bug report seems relevant:
[http://bugs.gentoo.org/show_bug.cgi?id=223817](http://bugs.gentoo.org/show_bug.cgi?id=223817)

I don't understand enough to give you a fix, however. :(

---

### Post by rob263 on 2008-09-18
Had exact same problem, and solved it as follows:
1) uninstall any magick-related packages
2) download the ImageMagick source code
3) run "configure" with --disable-openmp
4) run "make", and "make install"

problem solved!

---

### Post by samburney on 2009-10-22
> **rob263 said:**
> Had exact same problem, and solved it as follows:
1) uninstall any magick-related packages
2) download the ImageMagick source code
3) run "configure" with --disable-openmp
4) run "make", and "make install"

problem solved!

Thanks for that hint!

I've rebuilt imagemagick to include that change, if you add the following line to your sources.list and do an apt-get upgrade you'll get the fixed package (Or you can manually install 6.5.1.0-1.1ubuntu3.1):

deb [http://mirror.sifnt.net.au/linux](http://mirror.sifnt.net.au/linux) karmic main

I've attached the updated .diff.gz to this post for anyone who'd rather just build their own.

---

### Post by sjdenton on 2009-11-17
:d

---

### Post by yzf600 on 2009-12-04
I'm getting issues with that package source:

Err [http://mirror.sifnt.net.au](http://mirror.sifnt.net.au) karmic/main libmagick++2 7:6.5.1.0-1.1ubuntu3.1
  404  Not Found
Failed to fetch [http://mirror.sifnt.net.au/linux/dists/karmic/main/binary-i386/libmagick++2_6.5.1.0-1.1ubuntu3.1_i386.deb](http://mirror.sifnt.net.au/linux/dists/karmic/main/binary-i386/libmagick++2_6.5.1.0-1.1ubuntu3.1_i386.deb)  404  Not Found

---

### Post by yzf600 on 2009-12-04
Ah - it's ok that source is broken. The better fix for me was to put this in my ~/.gscan2pdf:

resolution = 200

---

### Post by mutrax on 2010-01-04
> **yzf600 said:**
> Ah - it's ok that source is broken. The better fix for me was to put this in my ~/.gscan2pdf:

resolution = 200

ah, thank you!

I just bumped into the same problem. This fix also does the trick here!

---

