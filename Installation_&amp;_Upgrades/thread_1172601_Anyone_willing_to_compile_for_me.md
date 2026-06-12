---
title: "Anyone willing to compile for me?"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by Thanatios on 2009-05-28
Hello,

There is a little problem I have with a laptop. I don't have an internet connection on it. But want to install iTunnel on it to connect to my iphone trough the internet. 
But now my problem is, that it seems that my Xubuntu system doesn't have a libiphone package istalled on it. Now I found the package, but I can't compile it on the Xubunt system (I'm writing this using a Windows Vista Notebook). 

The libiphone source: # [http://cloud.github.com/downloads/MattColyer/libiphone/libiphone-0.9.1.tar.bz2](http://cloud.github.com/downloads/MattColyer/libiphone/libiphone-0.9.1.tar.bz2) 

I hope someone will help me out making this a working install file for the Xubuntu.
Thanks in advace!

---

### Post by Thanatios on 2009-05-28
anyone please?

---

### Post by albinootje on 2009-05-28
> **Thanatios said:**
>  I can't compile it on the Xubunt system 


Which Xubuntu release are you using ? 8.04 or 9.04 or which one ?

---

### Post by kerry_s on 2009-05-28
why not just try ifuse: [http://matt.colyer.name/projects/iphone-linux/index.php?title=Main_Page](http://matt.colyer.name/projects/iphone-linux/index.php?title=Main_Page)

there's debs you can just download and install.
[http://ppa.launchpad.net/jonabeck/ppa/ubuntu/pool/main/libi/libiphone/](http://ppa.launchpad.net/jonabeck/ppa/ubuntu/pool/main/libi/libiphone/)

[http://ppa.launchpad.net/jonabeck/ppa/ubuntu/pool/main/i/ifuse/](http://ppa.launchpad.net/jonabeck/ppa/ubuntu/pool/main/i/ifuse/)

---

### Post by Thanatios on 2009-05-28
Thanks for your answers again!

The version is 8.02. Thanks for the help.

Thanks for the links, but the question would still be what to download? :P 

Thanks in advance.

---

### Post by kerry_s on 2009-05-28
> **Thanatios said:**
> Thanks for your answers again!

The version is 8.02. Thanks for the help.

Thanks for the links, but the question would still be what to download? :P 

Thanks in advance.

[http://ppa.launchpad.net/jonabeck/ppa/ubuntu/pool/main/libi/libiphone/libiphone0_0.9.1-1ubuntu2_i386.deb](http://ppa.launchpad.net/jonabeck/ppa/ubuntu/pool/main/libi/libiphone/libiphone0_0.9.1-1ubuntu2_i386.deb)

[http://ppa.launchpad.net/jonabeck/ppa/ubuntu/pool/main/i/ifuse/ifuse_0.9.1-1ubuntu2_i386.deb](http://ppa.launchpad.net/jonabeck/ppa/ubuntu/pool/main/i/ifuse/ifuse_0.9.1-1ubuntu2_i386.deb)

download those get them to the computer.
run> sudo dpkg -i *.deb
from the terminal in the place that you put them.
or
just double click on them, you'll proably have to do the libiphone before ifuse.

---

### Post by albinootje on 2009-05-28
> **kerry_s said:**
> 
download those get them to the computer.

From a quick look at a few pages it looked like those debs are only for 8.10, and newer.

The OP has 8.04... so the options are a.o. :
- upgrade to Xubuntu 8.10 
(could lead to trouble, depending on the hardware that the OP uses.)
- backporting the software to 8.04
- start using apt-pinning (carefully!) to mix 8.04 and 8.10

---

### Post by kerry_s on 2009-05-29
> **albinootje said:**
> From a quick look at a few pages it looked like those debs are only for 8.10, and newer.

The OP has 8.04... so the options are a.o. :
- upgrade to Xubuntu 8.10 
(could lead to trouble, depending on the hardware that the OP uses.)
- backporting the software to 8.04
- start using apt-pinning (carefully!) to mix 8.04 and 8.10

it don't matter, there stand alone packages that don't require anything else for dependency.

>  What is it?

libiphone is a software library that talks the native Apple USB protocols that the iPhone uses. Unlike other projects, `libiphone` does not depends on using any existing `.dll` or `.so` libraries from Apple.

iFuse is a FUSE filesystem driver which uses `libiphone` to connect to devices without jailbreak. iFuse is using the native Apple "AFC" protocol, over the normal USB cable in order to access the iPhone's (or iPod Touch's) media files under Linux. 

---

### Post by Thanatios on 2009-05-30
greetings again.

Well I have tried to open the deb packages. But both of them give me this error: Error: Dependency is not satisfiable: libplist0 (>= 0.12)

In terminal:
root@Linux:/home/art# sudo dpkg -i /home/art/Desktop/libiphone0_0.9.1-1ubuntu2_i386.deb
Selecting previously deselected package libiphone0.
(Reading database ... 106750 files and directories currently installed.)
Unpacking libiphone0 (from .../libiphone0_0.9.1-1ubuntu2_i386.deb) ...
dpkg: dependency problems prevent configuration of libiphone0:
 libiphone0 depends on libplist0 (>= 0.12); however:
  Package libplist0 is not installed.
dpkg: error processing libiphone0 (--install):
 dependency problems - leaving unconfigured
Processing triggers for hal ...
Regenerating hal fdi cache ...
 * Restarting Hardware abstraction layer hald                            [ OK ] 
Errors were encountered while processing:
 libiphone0

I also tried to download the libplist0 package after that (libplist0-dbg_0.12-1_i386.deb). But when I want to install that package, I get the exact same error... 
Strange..

Any more suggestions?

---

### Post by y2k103 on 2009-07-05
Same thing here. Is there a way to "force install" these packages? (or is that not a good thing to do?)

---

### Post by albinootje on 2009-07-05
> **y2k103 said:**
> Same thing here. Is there a way to "force install" these packages? 

dpkg has quite some "force" options, but..
> 
(or is that not a good thing to do?)
In this case it looks like a bad choice to do that imho.
Which Ubuntu release are you using ? See my previous comment in this thread.

---

### Post by y2k103 on 2009-07-07
I'm using 9.04 - 64 Bit. Does that make a different? I do have a laptop running the same thing but 32 Bit. (Never really thought about it until you asked) BTW, thanks for the reply.

---

