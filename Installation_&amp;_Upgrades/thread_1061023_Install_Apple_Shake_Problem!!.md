---
title: "Install Apple Shake Problem!!"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by mgrajeshvkm on 2009-02-05
hi friends,

i tried to install apple shake 4.  I got it as "shake-linux-v4.00.0607.tgz".

i copied that to home (places/home)directory.  and tryed to install using

"apt-get install shake-linux-v4.00.0607.tgz" command..but unfortunately i failed..the message was

"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package shake-linux-v4.00.0607.tgz
"

whats it?..how can i solve the problem??

PLZ HELP!!!

---

### Post by dstew on 2009-02-05
I am not sure you are supposed to install that package using apt-get. The .tgz file you downloaded is probably a source file. Apt-get is a tool for getting debian packages from a repository, and installing.

To install a source package, like you have, you will need to install the **build-essential** package, and then compile the source code. See [this How-To]("https://help.ubuntu.com/community/CompilingEasyHowTo").

---

### Post by Mark Phelps on 2009-02-05
That error is because a *.tgz file is not a package; it is a compressed archive file.  

Installing from source not only requires a compiler (which you probably have), but also a bunch of libraries and other modules.

Unless you're experienced and compiling, linking, and installing from source code, you would do better to find a .deb (package file) and install using that.  That way, it will identify the dependencies.

---

### Post by mgrajeshvkm on 2009-02-08
i have tried many methods for converting it to a deb file..i failed..the contents of shake-linux-v4.00.0607.tgz was

bin
doc 
fonts
icons
include
keys
lib
and a icons.pak files


plz help me...

---

