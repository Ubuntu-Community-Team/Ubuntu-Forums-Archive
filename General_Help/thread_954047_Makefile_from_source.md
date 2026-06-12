---
title: "Makefile from source"
date: 2008-10-20
forum: General Help
---

### Post by xnerdx on 2008-10-20
Hello everyone,
      I hope to fix my problem and I really hope that it is possible. I like to build files from source, the only problem with that is that I do not have all the dependencies, so what I have to do is the ./configure command then run read the errors and run the synaptic package manager to install the package. Now this isn't to be bad but because I have Intrepid Ibex and it is quite a pain because my package manager frequently decided to crash, especially when I type lib into the search bar :P). Anyways I am wondering if there is a command to make it download and install the dependency files.
   Thank you :)

---

### Post by tuxxy on 2008-10-20
Providing you know the dependencies needed, you could do in terminal

```
sudo apt-get install <filename>
```

---

### Post by xnerdx on 2008-10-20
Thank you for the reply but sadly I knew that, the problem is that the dependencies are not listed as the package name just something similar to it in the ./configure output.

---

### Post by cicatrix1 on 2008-10-20
> **xnerdx said:**
> Thank you for the reply but sadly I knew that, the problem is that the dependencies are not listed as the package name just something similar to it in the ./configure output.

sudo apt-cache search "something"

will search all packages names for the something.  You can also use regex, i.e. "compiz.*settings.*" to search for compiz*settings*.

There may be a way to search for a specific file or lib, but I do not know it.  I know there is a way with yum in fedora and other redhat, but I have not found the apt equivalent of "yum whatprovides <thing>".

Does any body know?

---

### Post by RequinB4 on 2008-10-20
You can search via

```
synaptic
```

or

```
apt-cache search *packagename*
```

where *packagename* is what you're searching for.

No need for sudo - you shouldn't use it unless you are actually installing something.

Before you do anything, make sure you run

```
sudo apt-get install build-essential
```

You need this to compile anything

---

### Post by cicatrix1 on 2008-10-20
Oh yes.  Sorry.  I just have a habit of sudo-ing anything apt.

---

### Post by xnerdx on 2008-10-21
Oh thank you so much! This outta' make my linux life much more of a breeze!

---

