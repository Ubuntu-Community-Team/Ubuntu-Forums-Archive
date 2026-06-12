---
title: "g++ compiler help"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by Bolter on 2009-08-04
hello i'm new here and just installed ubuntu 9.04 on my laptop.
I'm writing c++ programs using the terminal but when i try to compile them with g++ it doesnt work, i type in the command  "g++ test.cpp -o test " and it says this:

The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: sudo apt-get install <selected package>
bash: g++: command not found  

I went on the documentation and tried to to get the build-essential package but a error message box came up saying "package not found" :(:confused:

anyone know what the problem is or is there any other way to get the g++ compiler? i really need it.

thanks in advance

---

### Post by credobyte on 2009-08-04
You haven't installed it ( and I'm not sure about what you meant with "I went to the documentation and tried to get it" ?? ) :)

```
sudo apt-get install build-essential

```

---

### Post by Bolter on 2009-08-04
> **credobyte said:**
> You haven't installed it ( and I'm not sure about what you meant with "I went to the documentation and tried to get it" ?? ) :)

```
sudo apt-get install build-essential

```

by documentation i meant this website: [https://help.ubuntu.com/9.04/programming/C/build-essential.html](https://help.ubuntu.com/9.04/programming/C/build-essential.html)

and when i typed in: sudo apt-get install build-essential

i got an error saying this:

ssk@ssk-laptop:~/newfolder$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

---

### Post by credobyte on 2009-08-04
Update your Aptitude database and try again:

```
sudo apt-get update

```

Otherwise, you can try to install it from .deb: [http://packages.ubuntu.com/jaunty/i386/build-essential/download](http://packages.ubuntu.com/jaunty/i386/build-essential/download)

---

### Post by Bolter on 2009-08-04
[LEFT]it still doesnt work for some reason:

ssk@ssk-laptop:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

and when trying the website you gave me and after i downloaded the installer i got a error message saying this:

Package: build-essential
Status: Error: Dependency is not satisfiable: g++ (>= 4:4.3.1)

[/LEFT]

---

