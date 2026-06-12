---
title: "program to make int easier to install"
date: 2005-11-27
forum: General Help
---

### Post by freemanen on 2005-11-27
is there a program that help you to intalll programs?

---

### Post by psyguy92 on 2005-11-27
System -> Administration -> Synaptic Package Manager

---

### Post by freemanen on 2005-11-27
but how does it help if you download it from internet?

---

### Post by kosmic on 2005-11-27
freemanem if you download programs from the internet and you are a newbie you are asking for troubles...
 
If oyu download a program in the tgz format you will need to have all the compilers necessary to compile the program installed and you will also need the lib files that the program uses.
 
 
So the best way to install programs in Ubuntu is to use apt-get or Synaptic

---

### Post by freemanen on 2005-11-27
what to do if can't find it synaptic?

---

### Post by kosmic on 2005-11-27
If you can't find it in the repositories and want that program, when you donwloaded the source code from the site, inside should be a file called README or INSTALL you just have to read what are the dependencies that program needs and install them first.
 
then it should be someting like this
 
configure
make
make install / or make checkinstall
 
 
More info on checkinstall can be found in the wiki -> [https://wiki.ubuntu.com/CheckInstall?action=fullsearch&value=linkto%3A%22CheckInstall%22&context=180]("https://wiki.ubuntu.com/CheckInstall?action=fullsearch&value=linkto%3A%22CheckInstall%22&context=180")

---

### Post by psyguy92 on 2005-11-27
Have you enabled extra repos?
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Have you searched for a debian package that *might* work? 
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

You could try an .rpm and use alien to convert it.
[http://ubuntuguide.org/#convertrpmtodebfiles](http://ubuntuguide.org/#convertrpmtodebfiles)

If these don't work, you will have to build from source.  This will require a bit of reading :)

---

### Post by bonzodog on 2005-11-27
Have you enabled the backports and extras?- it should take synaptic to around 17,000 programs- if you haven't see: [http://www.ubuntuforums.org/showthread.php?t=40291](http://www.ubuntuforums.org/showthread.php?t=40291)

However, if it is a really individual program, try and see if you can find the file as a .deb - this is a pre-built debian binary which can be unpackaged with one line in the terminal. i.e: 

```
dpkg -i <name of program>
```

Otherwise, try and see if you can find it as a .rpm (pre-packaged binary for mandrake and redhat) or binary slackware .tgz. If you can, follow these steps to get the program to work in ubuntu:

```
sudo apt-get install alien
```

Then;

```
alien <name of program>
```

This will convert the rpm or binary .tgz to a .deb that can be installed with step 1.

If you are unable to get the package in a linux binary format, you will need to get the source code, which will either be a .tar.gz or a .tar.bz2 and build it yourself. This is rather more complicated.

First, get the development tools;

```
sudo apt-get install build-essential
```

Then untar and unzip the source code into a local directory (next instruction for .tar.gz only)

```
tar -xvzf <name of file>
```

Find the README.txt file and the INSTALL.txt file and read both, thoroughly. They will tell you of any dependencies the program may have. Also there should have been information on the site where it came from, especially if it requires a non-standard library or unusual package. (this is what sometimes is known as 'dependency hell' -you can get caught in an endless list of dependencies)

After unpacking the file and being fairly sure that you have what the program requires, build it like so:

```
 cd <program dir>
./configure
make 
sudo make install 
```

Hopefully now you should have a working installed package, which will need adding to the gnome menus manually using smeg. Don't panic if it doesn't compile first time. Look carefully at the output and see what the program is missing. any questions about errors can always be asked to us; try and paste any errors into your posts and we will be able to explain them to you.

I hope this has provided some useful pointers to people new to this.

---

