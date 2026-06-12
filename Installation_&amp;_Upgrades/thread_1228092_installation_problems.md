---
title: "installation problems"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by electrovalent on 2009-07-31
Hi!I am having problem installing some things like vuze.
I try  "sudo apt-get install Vuze_4.2.0.4_linux.tar.bz2"  or  "sudo apt-get install vuze"  after extracting the tar.bz2 file and in both cases i get:

E: Couldn't find package........

---

### Post by slakkie on 2009-07-31
You're trying to install from sources via the package manager, that will never work.

What you can do is extract the file and with checkinstall create a .deb file from it, so you can install it via the package manager:

```

sudo aptitude install checkinstall

tar jxvf Vuze_4.2.0.4_linux.tar.bz2
cd $dir
./configure
make
make test
sudo checkinstall make install

```

Just accept the defaults of checkinstall and everything should be OK. It will leave a .deb file behind which can be installed by dpkg -i $deb_file. Checkinstall will have installed it already.

---

### Post by electrovalent on 2009-07-31
how do i end my description?with an empty line or EOF?and how the discription should be?

---

### Post by electrovalent on 2009-07-31
john@john-laptop:~$ tar jxvf Vuze_4.2.0.4_linux.tar.bz2
tar: Vuze_4.2.0.4_linux.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
john@john-laptop:~$ cd $dir
john@john-laptop:~$ ./configure
bash: ./configure: No such file or directory
john@john-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
john@john-laptop:~$ make test
make: *** No rule to make target `test'.  Stop.
john@john-laptop:~$ sudo checkinstall make install

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*** No known documentation files were found. The new package
*** won't include a documentation directory.

Please write a description for the package.
End your description with an empty line or EOF.

---

### Post by slakkie on 2009-07-31
If the first command is failing then there is no need to continue ;)

And $dir is meant to be the dir that the archive created, since I do not know that I made it a variable.. Eg, if the archive left a dir called vuze, you would cd into vuze: cd vuze. 

But it cannot extract the file, since it does not exists.

---

### Post by electrovalent on 2009-07-31
ok and after i cd into vuze,i do something?What is the ./configure meant to be..,the make?the make install?Are those commands?And should be follow by other words?

---

### Post by slakkie on 2009-07-31
Have a look here:

[http://tazbuntu.blogspot.com/2008/04/compile-and-install-from-source-code.html](http://tazbuntu.blogspot.com/2008/04/compile-and-install-from-source-code.html)
[http://www.hardwareforums.com/compiling-source-code-ubuntu-18746/](http://www.hardwareforums.com/compiling-source-code-ubuntu-18746/)
[http://www.linuxjournal.com/article/216](http://www.linuxjournal.com/article/216)

---

### Post by electrovalent on 2009-08-01
these links describe an installation of programs using a configure file.after extracting the .bz2 file downloaded from the oficial site of vuze and cd into the extracted file and type ./configure i get :No such file or directory.

---

