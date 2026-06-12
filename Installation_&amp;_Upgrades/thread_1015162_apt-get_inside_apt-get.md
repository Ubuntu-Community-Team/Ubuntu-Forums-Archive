---
title: "apt-get inside apt-get"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by pablop on 2008-12-18
I'm using a software that is using apt-get to install something but let me add a 'post installation script' that will
be running as a child of this apt-get instance.

I was trying to run apt-get as part of the postinst script but then been told that the parent apt-get instance can't run another apt-get inside it. 

Is there a workaround or some ideas?

Thank you.

---

### Post by donkyhotay on 2008-12-18
Not certain what your doing but if you need apt-get to install something then immediately run apt-get again I would create a bash script to do that for me
```
sudo apt-get install somepackage
sudo apt-get autoremove
sudo apt-get autoclean
```
as a theoretical example. Because of the way apt-get runs you can only have one instance of apt-get running at a time. If you run apt-get from two terminal sessions at the same time you get an error. Although I've never used the post-install scripting option I'm pretty certain the fact that the parent is technically running until the child is finished is the reason why this fails. Obviously the solution is to have something else run both instances of apt-get (like the above-mentioned bash script) so it's not an issue.

---

### Post by pablop on 2008-12-19
```
sudo apt-get install somepackage
sudo apt-get autoremove
sudo apt-get autoclean
```

That won't work for me.

I actually need:
```
sudo apt-get install somepackage
```

and inside somepackage to run:
```
apt-get install childpackage
```

I know it sound unusual but it's part of a complex system.

Maybe there is a different package manager that can be run inside apt-get?

---

### Post by bapoumba on 2008-12-20
I'm not sure I understand what you are trying to do, but would dependencies work? (childpackage has to be a dep of somepackage, and will be installed if you ask for somepackage).

Maybe auto-apt ?
[http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html)
> 5.3 How to install packages "on demand"

You're compiling a program and, all of a sudden, boom! There's an error because it needs a .h file you don't have. The program auto-apt can save you from such scenarios. It asks you to install packages if they're needed, stopping the relevant process and continuing once the package is installed.

What you do, basically, is run:

     # auto-apt run command

Where `command' is the command to be executed that may need some unavailable file. For example:

     # auto-apt run ./configure

It will then ask to install the needed packages and call apt-get automatically. If you're running X, a graphical interface will replace the default text interface.

Auto-apt keeps databases which need to be kept up-to-date in order for it to be effective. This is achieved by calling the commands auto-apt update, auto-apt updatedb and auto-apt update-local. 
I have no idea if this would work replacing "command" with apt-get itself..

---

