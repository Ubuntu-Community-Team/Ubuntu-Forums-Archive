---
title: "Attempted To Install Skype"
date: 2008-08-04
forum: General Help
---

### Post by CarlosinFL on 2008-08-04
I downloaded the .deb package from Skype's site and installed it however when I try to run it I get the following error:

```
cwilliams@tunafish:~$ skype
skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory

```

---

### Post by mannheim on 2008-08-04
You should check first if the file libQtDBus.so.4 is really present in your system. It should be located in /usr/lib. So try opening a terminal and typing

```
locate libQtDBus.so.4
```

The file **should** be there, because it should be installed by the libqt4-core package, which is a dependency of the skype package. If it isn't there, check if the package libqt4-core is installed.

(If you are running a 64-bit version of Ubuntu, then the 32-bit version of the library should be installed in /usr/lib32. In this case, you need the package ia32-libs installed.)

---

### Post by LowSky on 2008-08-04
Isn't Skype in the repos?
to install you should have only needed to type the following
```
sudo apt-get install skype
```

---

### Post by kostkon on 2008-08-04
> **Carlwill said:**
> I downloaded the .deb package from Skype's site and installed it however when I try to run it I get the following error:

```
cwilliams@tunafish:~$ skype
skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory

```
What version of *Ubuntu* do you have?

This library is provided by the *libqt4-core* package. Install it and try again with *Skype*.

There are two repositories that provide *Skype*, if you want to know:

- Its official repository
```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```
Just go to *System -> Adminstration -> Software Sources* and add the above line to *Third Party Software*.

- The [*Medibuntu* repository]("http://www.medibuntu.org/")

If you have a 64bit system, you can check [the *Ubuntu* documentation page for *Skype*]("https://help.ubuntu.com/community/Skype") for instructions on how to install it.

---

