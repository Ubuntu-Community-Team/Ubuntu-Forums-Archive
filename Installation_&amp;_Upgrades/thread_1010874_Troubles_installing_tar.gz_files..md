---
title: "Troubles installing tar.gz files."
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by Youbuntoo44 on 2008-12-14
Hi everybody, I've been a linux (Ubuntu) user for a few months and fail to install tar.gz files in under 3 hours or without asking my dad. Everything is dandy until I give it the 'make' or 'make clean' or 'make install' commands. I ALWAYS get this error:

giles@Thinkpad:~/src/crrcsim-0.9.9$ make
make: *** No targets specified and no makefile found.  Stop.
giles@Thinkpad:~/src/crrcsim-0.9.9$ 

I'm trying to install the RC flight sim 'Crrcsim'. I've compiled it, uncompressed it, what can I do to stop the errors? TIA.

---

### Post by forkandles on 2008-12-14
Is this any help?

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by djbushido on 2008-12-14
if you are wanting to install a package that is packaged in *.tar.gz or *.tgz (note: this means it is pre-compiled) you can do:
```

sudo tar xvzf -C /

```
This will install package contents for you, but only if it doesn't need to be compiled.

---

### Post by logos34 on 2008-12-14
when dealing with tar.gz application archives always look in the parent dir for README.txt or INSTALL.txt file for installation info.  Or check the website. The instructions are here:

[http://crrcsim.berlios.de/wiki/index.php?n=CRRCsim.InstallLinux](http://crrcsim.berlios.de/wiki/index.php?n=CRRCsim.InstallLinux)

In this case it looks as though you can simply run it from your /home/user dir, invoking it with the standard './'.  To install, cd the parent dir and run

sudo make install_local

---

### Post by linux_tech on 2008-12-14
Applications>Accessories>Terminal
The first step is to uncompress the files-

```
tar xvfz nameoffile.tar.gz
```

or another way-
when you download the file, in the downloads window, double-click on the file. (This will bring up another window), then click the extract button to extract, (this will bring up another window) to browse to where you would like to extract then to. For this example select Desktop and click extract.

The 2nd step is to compile-
For this enter the terminal Application>Accessories>Terminal

```
cd Desktop
```

```
cd nameoffolder
```

(that was extracted to desktop) there will usually be a readme.txt in it that give the install instructions
then from inside the folder type (3 seperate commands)

```
./configure
```

[code]make[/code

[code]make install[/code

https://help.ubuntu.com/community/CompilingEasyHowTo

---

