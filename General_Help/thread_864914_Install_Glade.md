---
title: "Install Glade"
date: 2008-07-20
forum: General Help
---

### Post by lieja on 2008-07-20
Im trying to install glade but i got this result when i run the ./configure command. what should i do? im newbie to this linux stuff..FYI..im using the tar packages coz couldnt install frm sypnatic due to repo problems..please help me:(


checking for msgfmt... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.8.0  libxml-2.0 >= 2.4.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GTK_CFLAGS and GTK_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

---

### Post by fsmithred on 2008-07-20
You probably need to tell configure where to find libgtk2 and libxml2. It's probably expecting them to be in /usr/local instead of /usr/lib.

Try:
```
./configure --help
```
and it'll show you the options you can use.

A better solution might be to fix the repo problem.

---

### Post by lieja on 2008-07-22
thanks 4 ur reply..but can u give me some steps to fix the problem with any command. i had already used that help command but still couldnt find the answer:(

---

### Post by fsmithred on 2008-07-22
Sorry, I haven't mastered pkg-config. I can't even seem to be able to download the glade tarball to look at it, but I do notice that the versions on the glade download page don't match the versions in the hardy repository. That may or may not be a problem. Which version are you trying to install?

Is there some reason why you don't want to install from the .deb files? Here are the download pages. There's a much higher chance for success if you install the packages that are tailored to your installation. 
Get the files, and do:
```
sudo dpkg -i [filename]
``` 

[http://packages.ubuntu.com/gutsy/glade](http://packages.ubuntu.com/gutsy/glade)
[http://packages.ubuntu.com/gutsy/glade-common](http://packages.ubuntu.com/gutsy/glade-common)

---

### Post by lieja on 2008-07-23
the problem is my internet connection is to slow and sometimes couldnt access at all when im using ubuntu. im not really sure what the problem because i can access the internet without any problem frm XP.

---

### Post by ookamisan on 2008-07-23
[http://packages.ubuntu.com/hardy/gnome/]("http://packages.ubuntu.com/hardy/gnome/")

Try looking there for the glade.deb package under Windows. In Ubuntu you can install it with ```
sudo dpkg -i thepackage.deb
```

---

### Post by lieja on 2008-07-23
b4 that..i wanna ask a question..can i use deb package for hardy coz im using gutsy DE

---

### Post by ookamisan on 2008-07-23
[http://packages.ubuntu.com/gutsy/gnome/]("http://packages.ubuntu.com/gutsy/gnome/")

try that one then ;)

---

### Post by lieja on 2008-07-23
ok..thanks ookamisan..i'll try it first:)

---

