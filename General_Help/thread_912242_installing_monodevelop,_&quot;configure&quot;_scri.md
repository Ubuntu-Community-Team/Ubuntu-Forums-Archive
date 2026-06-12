---
title: "installing monodevelop, &quot;configure&quot; script fails-- don't have &quot;gmcs&quot; in path?!"
date: 2008-09-06
forum: General Help
---

### Post by MaxIBoy on 2008-09-06
```
maxtothemax@maxtothemax-desktop:~/monodevelop$ ./configure

Configuring package: main
-------------------------
Configuration options: 
Running aclocal  ...
Running automake --gnu  ...
Makefile.am: installing `./INSTALL'
Makefile.am: installing `./COPYING'
Running autoconf ...
Running ./configure --enable-maintainer-mode --enable-compile-warnings --prefix=/usr/local ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for mono... /usr/bin/mono
checking for gmcs... no
configure: error: Can't find "gmcs" in your PATH
maxtothemax@maxtothemax-desktop:~/monodevelop$  

```

What should I do about this?

---

### Post by pbotros1234 on 2008-09-06
```
sudo apt-get install mono-gmcs
```

Recompile and see if that works?

---

### Post by MaxIBoy on 2008-09-06
Okay, here's what happens when I try to do that:
```
maxtothemax@maxtothemax-desktop:~/monodevelop$  sudo apt-get install mono-gmcs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libgtkglext1-ruby1.8: Depends: libgtkglext1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
maxtothemax@maxtothemax-desktop:~/monodevelop$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  x11proto-xinerama-dev x11proto-render-dev libxi-dev libxmu-headers
  libxrender-dev libqt4-core libpng12-dev libsqlite0-dev libfontconfig1-dev
  libxcursor-dev x11proto-randr-dev libxmu-dev libqt4-sql libfreetype6-dev
  x11proto-fixes-dev liblcms1-dev libpq-dev libxrandr-dev libexpat1-dev
  libxft-dev libxfixes-dev libmng-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgtkglext1
The following NEW packages will be installed:
  libgtkglext1
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 0B/126kB of archives.
After this operation, 414kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 139252 files and directories currently installed.)
Unpacking libgtkglext1 (from .../libgtkglext1_1.2.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgdkglext-x11-1.0.so.0.0.0', which is also in package libgtkglext-1.0-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
maxtothemax@maxtothemax-desktop:~/monodevelop$ 


```

---

### Post by sliverman69 on 2009-02-09
I have a similar problem...same configure script fail, same reason...only I successfully installed mono-gmcs but it still says it's not in the path.  

Additionally, I have tried apt-get remove mono-gmcs and reinstalling and it still says that it couldn't find it in the path

---

### Post by directhex on 2009-02-10
mono-devel.

And next time, either don't use random PPA's, or read changelog.Debian.gz

---

### Post by ben2talk on 2009-03-22
Okay - which 'mono-devel' - I think 1.0 is a 6MB download, and internet isn't fast for everyone. I'm actually getting 'Gnome-Do' - but honestly, mono-devel isn't in the repositories.

---

### Post by directhex on 2009-03-22
> **ben2talk said:**
> Okay - which 'mono-devel' - I think 1.0 is a 6MB download, and internet isn't fast for everyone. I'm actually getting 'Gnome-Do' - but honestly, mono-devel isn't in the repositories.

[http://packages.ubuntu.com/jaunty/mono-devel](http://packages.ubuntu.com/jaunty/mono-devel)

Nope, not in the repositories, evidently

As for sliverman69 and MaxIBoy, I'd put money on them being users of Eric Butler's backport PPA - backporting a version of Mono which contains several significant packaging changes, which result in problems like this.

---

### Post by theDaveTheRave on 2010-01-07
> **directhex said:**
> mono-devel.

And next time, either don't use random PPA's, or read changelog.Debian.gz


OOH bit harsh! have you done a search for changelog.debian.gz on google lately? I only get 15 million results, and unless you are experience how would you know which one to look for?? (I certainly got put off trying to find it!).

Who knows how many "newbies" may read this and be immediately put off from ever attempting to install from source :(


Full info on this bug can be found [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=537081").

The solution is to perform the following

```

sudo apt-get install mono-devel

```

This bug was reported in July 2009, and has now been fixed, but is obviously taking a while to filter down to all the distro's.

Hope that clears things up for everyone....

David.

ps. sorry if I sound a little 'agravated', but it is this sort of thing that would put off newcomers (as far as I'm concerned).

---

### Post by liverpudd on 2010-05-17
I am new to Ubuntu/linux and I am trying without much success to install Mono 2.2.1 on my machine (which is NOT connected to the internet for security reasons) and am getting the 'Can't find "gmcs" in your PATH' error.

So far I have downloaded the monodevelop_2.2.1+dfsg.org.tar.gz on another machine and transfered it to the download directory on the target machine.

Any help appreciated.

---

