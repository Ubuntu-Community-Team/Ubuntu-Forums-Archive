---
title: "[SOLVED] Removing Software"
date: 2008-11-03
forum: General Help
---

### Post by Tamalin on 2008-11-03
If I downloaded an installer from somewhere, say VirtualBox, from the sun website, and Installed it, how do I remove it if I decided I didn't need it anymore down the line?  It won't work using apt-get remove [HTML]<i>appname</i> (It can't find the packages in the repository or something).[/HTML]
Does anyone know what to do?

---

### Post by snova on 2008-11-03
It depends on how you installed it. VirtualBox provides a .deb, which is native to Ubuntu, and should be preferred as an installation media. But if you used a self-installing script or something, that makes it more difficult... Try running the script again with the --help argument and see if it says anything about uninstallation.

---

### Post by bwhite82 on 2008-11-03
Depends on how you installed it/what type of package it is.

If source code (.tar.gz), then make sure you always keep the untarred source directory, then enter that directory:

> sudo make uninstall && make clean

If its a binary installer (.bin) it will usually install an uninstaller for you to use. Usually in its install directory (/usr/bin/programName) or sometimes your home directory (/home/yourUserName/.programName). It will be a script or another .bin (virtualbox-uninstaller.sh/virtualbox-uninstaller.bin).

> sudo sh programName-uninstall.sh

If its a .deb then uninstall via Synaptic or apt-get.

---

### Post by Tamalin on 2008-11-03
Yes, but I have tried uninstalling programs installed with a .deb, but using apt-get returns a package not found error, but, ah-yes, here I have found my package in Synaptic! Oh, good!  But what if I installed it with a tar.gz file?  I'm not sure about what is meant by > sudo make uninstall && make clean  (I don't really even know what the make command does...).  This also seems a bit much just to uninstall a program, I know a several people I am trying to get to switch to Ubuntu, but none of them have ANY clue about how to use a command-line.  This would easily scare them off.  Is there some kind of automated system for this maybe?

---

### Post by oldos2er on 2008-11-03
> **Tamalin said:**
> Yes, but I have tried uninstalling programs installed with a .deb, but using apt-get returns a package not found error, but, ah-yes, here I have found my package in Synaptic! Oh, good!  But what if I installed it with a tar.gz file?  I'm not sure about what is meant by   (I don't really even know what the make command does...).  This also seems a bit much just to uninstall a program, I know a several people I am trying to get to switch to Ubuntu, but none of them have ANY clue about how to use a command-line.  This would easily scare them off.  Is there some kind of automated system for this maybe?

 You use "sudo make uninstall" if you compiled and installed source code. There's no real reason why a newbie would compile code, unless they're just curious about the process. Ubuntu doesn't even come with the ability to compile code by default (unlike nearly every other distro). 

 Newbies should probably stick to the GUI package managers such as Add/Remove or Synaptic. I think this is the "automated system" you're looking for.

---

### Post by Yellow Pasque on 2008-11-03
> If source code (.tar.gz), then make sure you always keep the untarred source directory..
Some Makefile's don't provide "make uninstall". For this reason (and others), I got turned on to a program called checkinstall, which monitors the files that "make install" puts on your system and wraps them up into a nice .deb (easily uninstallable).

---

### Post by Tamalin on 2008-11-03
Okay, can I have a quick synopsis on what exactly a "makefile" is?
Running man make was slightly helpful, but I'm still not crystal clear.  Usually when I want to install a package, I just run ./configure, and maybe make if it said to do so in the instructions.

---

### Post by snova on 2008-11-04
Make is program used in building software. Basically, everything that can be "built" or generated is a "target". When you run "make", it builds the default target.

"make install" simply tells make to build the target named "install". Rather than compile anything, this is a special target that just copies things to their target directories.

"uninstall" is a similar target with opposite purposes.

A Makefile is just a file detailing all the targets.

---

### Post by Tamalin on 2008-11-10
Okay, I'm still a little fuzzy on the details, but I get the idea.  Thanks.

Another question...  What if the applications are written in Java? Does that change anything about make?  The files shouldn't be compiled into native code.

---

### Post by snova on 2008-11-10
A Makefile is generic enough where it can be used for many things, not only compiled languages. And besides, Java is compiled in its own way. The only practical difference is in the commands the Makefile executes. Instead of calls to gcc or whatever, it calls javac and related tools.

If you're looking for a build system, I would recommend you find something else. Make is not exactly the quintessence of build systems, it has many annoyances inherited from its earliest implementations.

All the Java applications I've ever encountered used Ant (which is written in Java and uses XML configuration files) anyway.

---

### Post by Tamalin on 2008-11-12
Ok, thank you!

---

