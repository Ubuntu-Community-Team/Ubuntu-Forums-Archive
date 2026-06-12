---
title: "[SOLVED] Which package is used to run a command"
date: 2008-09-12
forum: General Help
---

### Post by jis on 2008-09-12
Ubuntu has great feature to show which package needs to be installed to be able to run a command in terminal. How do you know which package is used for a command, if the package needed for the command is already installed? This knowledge would help to uninstall some applications.

---

### Post by mb_webguy on 2008-09-12
I'm not sure what you're asking.  

Each command is often its own package, though several closely related commands may be packaged together.  The easiest way I can think of to find out the package in which a command is found, run Synaptic and search for the command.  If you get multiple results, right click on one of the results, select Properties, and then the Installed files tab.  The commands included in the package are the files preceded by "/usr/bin" or "/usr/local/bin".

The ability to *run* a command is a function of the shell, which is the most basic form of user interface for a Unix-like operating system.  There are many shells available -- sh (the original Bourne shell), csh (the C shell), ksh (the Korn shell), and zsh (the Z shell) are some of the more popular -- but the default used by Ubuntu is the bash (Bourne-again) shell.  The various shells are typically packaged individually.  You generally don't want to uninstall the shells on your system, since if you do you're pretty much hosed -- you'll no longer be able to use the command line because in a very real sense, the shell *is* the command line.

---

### Post by jis on 2008-09-12
I edited the original post a little bit. I don't think using Synaptic works, since I can not search for installed files there.

---

### Post by gaussian on 2008-09-12
dpkg-query is your answer. E.g.

```

home@atmycomputer$ dpkg-query -S /usr/bin/firefox
firefox: /usr/bin/firefox

```

---

### Post by Vivaldi Gloria on 2008-09-12
Try

```
apt-cache search file
```

to search in packages (installed or not).

Also install apt-file and read

```
man apt-cache
man apt-file
```

to learn more about them.

---

### Post by jis on 2008-09-12
> **gaussian said:**
> dpkg-query is your answer.

Thanks, it works. Would be nice feature in Synaptic.

---

### Post by mb_webguy on 2008-09-12
> **jis said:**
> I edited the original post a little bit. I don't think using Synaptic works, since I can not search for installed files there.

Sure you can.  You can perform a search, then sort by the first column to see the installed packages matching the query.

Or, if you want to see all installed packages, click the Status button, then select Installed.

---

### Post by jis on 2008-09-13
I can search from  package names & descriptions, but how do you search from installed files by Synaptic? Remember, that I know the command name, not the package name.

---

### Post by AptlyNamed on 2008-09-13
```

dpkg -S <name-of-the-file> 

```
searches installed packages for a file. 'man dpkg' would have revealed this info.

---

### Post by jis on 2008-09-13
AptlyNamed, "dpkg -S <name-of-the-file>" is not the answer even for command line; dpkg-query is and this thread would have revealed this info. However, later I asked about Synaptic.

---

### Post by AptlyNamed on 2008-09-13
> **jis said:**
> AptlyNamed, "dpkg -S <name-of-the-file>" is not the answer even for command line; dpkg-query is and this thread would have revealed this info. However, later I asked about Synaptic.

Sorry! I should read before posting. Still 'dpkg -S' works fine (uppercase S) for packages already installed.

---

### Post by jis on 2008-09-13
I think dpkg works as a front end to dpkg-query. (At least it does work for dpkg-deb, which is explicitly stated in "man dpkg".) So both are answers for command line users. You might get better results, if you use command's whole path name as an argument for the commands.

---

### Post by AptlyNamed on 2008-09-13
My guess is that searching for files in packages was left out of Synaptic because it is an 'easy' apt-get front-end aimed at average users who mostly want to install some 'package', and not a certain 'command'.

---

