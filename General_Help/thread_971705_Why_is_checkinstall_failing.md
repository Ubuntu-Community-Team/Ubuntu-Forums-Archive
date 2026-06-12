---
title: "Why is checkinstall failing?"
date: 2008-11-05
forum: General Help
---

### Post by kevdog on 2008-11-05
Compiling various programs from source

At the end I perform something like this

./configure
make
sudo checkinstall -D make install

In all cases I seem to get an error similar to the following:

chmod 644 ....... Directory does not exist

Why can't checkinstall make the appropriate directories with the /usr/local tree?

As a side note -- If I perform a simple
sudo make install

I have no problems however then the package is installed outside the apt tree.

As a side note
If I do a 
sudo make install

and then try to repeat the checkinstall process
sudo checkinstall -D make install

Everything works since the directory tree has already been defined.

---

### Post by Dr Small on 2008-11-05
I don't know much about checkinstall since I'm running Arch with pacman (10 times easier), but it sounds like checkinstall is not creating the appropriate directories in your source directory (or whereever it does) to install the files to.

I know with makepkg, we use --prefix to specify which directory the entire thing should be installed into (in this case, the pkg/ directory). Sounds like some problem there.

---

### Post by Joeb454 on 2008-11-05
I don't know what the ```
-D make install
``` is for...

I usually use ```
./configure
make
sudo checkinstall
```

---

### Post by kevdog on 2008-11-05
sudo checkinstall

Gives the same problem complaining about not being able to create various directories.  Do I have to modify anything?  The funny part is if I run
sudo make install

and then
sudo checkinstall

Everything works -- however this is b/c the appropriate directory tree was created with the sudo make install statement and not with checkinstall.

Very puzzling?  Is dh an alternative?

---

### Post by mc4man on 2008-11-05
Without knowing a lot about creating packages I find if there is a debian directory in the source, that building off of the rules file works much better than ./configure, make, checkinstall. You can usually make configuration changes in rules and or prepend the build command.

As far as checkinstall, if you get the error message about a dir. doesn't exist or can't be created then just go ahead and manually create the needed empty dir(s) and then run checkinstall again.

---

### Post by kevdog on 2008-11-06
The problem with manually creating the directories (which does work), is that when trying to install a package such as pidgin, you are talking about creating 50 directories or so -- way too much work, particularly if you trying to write a tutorial to teach others how to compile things from source.

---

### Post by andrew.46 on 2008-11-21
Hi,

I may have posted this in another of your threads but there is a known problem with checkinstall that Intrepid Ibex is now exposed to. The hack is to use:

```
sudo checkinstall -D --fstrans=no --install=yes 
```

and usually this will get around the problem. The problem surfaced in late 2007 and I hear has been fixed in git version but not release version yet.

  Andrew

---

### Post by loko on 2008-11-21
Using checkinstall is a rough way and sometimes make big troubles if it overwrites some files that are also in other packages.

also, if it cannot create the dirs, i suggest ./configure --prefix=/usr, mostly the dirs are already there.

btw. for building a good package, i suggest that you read this:

[http://wiki.getdeb.net/quick%20build]("http://wiki.getdeb.net/quick%20build")

and long version:

[http://doc.ubuntu.com/pdf/ubuntu/C/packagingguide.pdf]("http://doc.ubuntu.com/pdf/ubuntu/C/packagingguide.pdf")

---

### Post by kevdog on 2008-11-21
Andrew 

Thanks for tip, I will have to try this.

I prefer to install into /usr/local/bin since its possible to have two separate versions of a program installed -- one the default in /usr/bin and the other my compiled version.

Getdeb.net --- Although they provide a good service, I really consider "their service" to be a joke.  Just compile from source on your own.  Its not really that hard, you can customize to your machine, and you learn a lot about how things compile in the process.  It really helps when you want to install from source with packages that are not included in getdeb.net

---

