---
title: "Cannot compile MySQL"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by didanoff on 2009-10-16
Hello.
I use 8.04 with all updates.
I try to compile MySQL from source. When I run ./configure I get:
/bin/rm: cannot remove `libtoolT': No such file or directory 

What it mean?

---

### Post by Vermind on 2009-10-16
Hi,
why do you want to compile MySQL from source?
It's  much easier to say ```
sudo apt-get install mysql-server
```, which will get you mysql 5.1. Do You need another version? Versions 4.1 and 5.0 are also available.

---

### Post by chaseleightone on 2011-08-14
I am trying to install BIND with DLZ (Dynamically Loadable Zones), for which I understand I DO need to compile MySQL.  I am following the procedure set out by cycloptivity in:

[http://ubuntuforums.org/showthread.php?t=823578&page=2](http://ubuntuforums.org/showthread.php?t=823578&page=2)

... when I get down to the Build MySQL & Install step, here's what happens

cd mysql-dfsg-5.1-5.1.41
./configure --prefix=/usr/local/mysql

... and towards the end of the config I ran into a snag with:

config.status: error: cannot find input file: Docs/Makefile.in

not really adept at fixing compiling errors, I am reaching out for any advice on how to proceed with this.  I'm also writing this up as a blog post on:

[http://fanaticaltenacity.blogspot.com/2011/08/mysql-data-driven-bind-dlz-dns-name.html](http://fanaticaltenacity.blogspot.com/2011/08/mysql-data-driven-bind-dlz-dns-name.html)

---

