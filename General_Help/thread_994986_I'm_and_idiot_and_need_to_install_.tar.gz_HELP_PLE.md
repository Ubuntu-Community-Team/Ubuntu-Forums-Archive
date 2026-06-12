---
title: "I'm and idiot and need to install .tar.gz HELP PLEASE"
date: 2008-11-27
forum: General Help
---

### Post by TriggerIsHappy on 2008-11-27
I know that the easy way to install some programs is the .deb files but I can't always find them and need to know how to install using the .tar.gz files. Will someone please help me.

---

### Post by Skripka on 2008-11-27
> **TriggerIsHappy said:**
> I know that the easy way to install some programs is the .deb files but I can't always find them and need to know how to install using the .tar.gz files. Will someone please help me.

Google is my Home Boy ;)

[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

You'll also need to extract the contents of the tar.gz with Ark or something similar.  The above will do you 95% of the time.  Read the README and INSTALL files in the archive-they should tell you everything you need to know.

---

### Post by eder.apt-get on 2008-11-27
$ tar -zxvf package_name.tar.gz
For example, if your package is in /home/username, all the files will be "unzipped" right there.

---

### Post by jerome1232 on 2008-11-27
The way to do this is strongly dependant on the program, do you have a link to the software that you are installing?

.tar.gz files are just compressed archives of files, similar to a .zip file, so it depends on what is compressed in there, be it an installation binary, the program itself or source code.  

You've already been given instructions on how to uncompress the archive and a very limited how-to for compiling from source, if you are still having trouble let us know what the program is and give a link to the site where you downloaded it from and we can help you more.

---

### Post by lavadisco on 2008-11-27
I just downloaded Kdenlive 0.7 a few minutes ago, and unzipped the tar.gz file to a folder on my desktop. The INSTALL file says this:

> To install, become root:

sudo make install
(enter root password at prompt)

So then I did this:

```
lavadisco@lavadisco:~$ cd ~/Desktop/kdenlive-0.7
lavadisco@lavadisco:~/Desktop/kdenlive-0.7$ sudo make install
[sudo] password for lavadisco: 
make: *** No rule to make target `install'.  Stop.

```

Then I went into the "src" subdirectory and tried again, with the same result. What am I doing wrong?

---

### Post by kevdog on 2008-11-27
I would try the following (I'm just guessing)

./configure
make
sudo make install

---

### Post by lavadisco on 2008-11-27
> **kevdog said:**
> I would try the following (I'm just guessing)

./configure
make
sudo make install

Thanks, but that didn't work.

---

### Post by linux_tech on 2008-11-27
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
```(that was extracted to desktop) there will usually be a readme.txt in it that give the install instructions
then from inside the folder type (3 seperate commands)
```
./configure 
```
```
make
```
```
make install
```

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by jespdj on 2008-11-27
> **lavadisco said:**
> Thanks, but that didn't work.

Well, then tell us what happened. Just saying "that didn't work" is useless, if you want help with this. Did you get error messages? If so, then what are the error messages?

If you're going to compile software yourself, the first thing you need is the compiler and other build tools. Install them with:
```
sudo apt-get install build-essential
```
Then do the configure, make, sudo make install steps again.

It will probably not work the first time, because you'll need development versions of libraries that the software you're compiling uses.

---

### Post by TriggerIsHappy on 2008-11-27
this is what I got from the commands


eric@eric-laptop:~/Desktop/n_v1linux$ ./configure
bash: ./configure: No such file or directory
eric@eric-laptop:~/Desktop/n_v1linux$ make
make: *** No targets specified and no makefile found.  Stop.
eric@eric-laptop:~/Desktop/n_v1linux$ sudo make install
make: *** No rule to make target `install'.  Stop.

The program is nothing more than a little game. Here is the website:

[http://www.harveycartel.org/metanet/downloads.html](http://www.harveycartel.org/metanet/downloads.html)

---

### Post by Skripka on 2008-11-27
> **TriggerIsHappy said:**
> this is what I got from the commands


eric@eric-laptop:~/Desktop/n_v1linux$ ./configure
bash: ./configure: No such file or directory
eric@eric-laptop:~/Desktop/n_v1linux$ make
make: *** No targets specified and no makefile found.  Stop.
eric@eric-laptop:~/Desktop/n_v1linux$ sudo make install
make: *** No rule to make target `install'.  Stop.

The program is nothing more than a little game. Here is the website:

[http://www.harveycartel.org/metanet/downloads.html](http://www.harveycartel.org/metanet/downloads.html)

Based on this:

[http://forum.therealn.com/viewtopic.php?f=21&t=799](http://forum.therealn.com/viewtopic.php?f=21&t=799)

And looking at the tar archive, you don't need to do any compiling--the N file in the archive is already an executable-I think.  You should be able to just run it (either via terminal or clicking on it.)

EDIT-playing a bit with it...it has a strange depend on it.....there is a valuable bit of running instruction in the README.....

EDIT2: That strange depend I can't find in the Ubuntu repos.  I don't know for sure what it is, it is called "libgtk-1.2.so.0"

---

### Post by nzadLithium on 2008-11-28
it wouldn't happen to be the package called libgtk1.2 would it? XP

---

### Post by noerrorsfound on 2008-11-28
[sorry, only saw first page]

---

### Post by Skripka on 2008-11-28
> **nzadLithium said:**
> it wouldn't happen to be the package called libgtk1.2 would it? XP

Nope-'tis something else, I already have libgtk1.2 installed...I can't find the depend on Synaptic on Kubuntu...maybe it is a Gnome library? :confused:

---

### Post by philetus on 2008-11-28
[http://lifehacker.com/software/ubuntu/how-to-install-anything-in-ubuntu-231105.php](http://lifehacker.com/software/ubuntu/how-to-install-anything-in-ubuntu-231105.php)

---

### Post by jerome1232 on 2008-11-28
Yeah, the dependencies are getting me as well, usually getlibs will do the trick but that didn't get it done this time.  This output from getlibs ought to help with figuring out what is needed I'm sure these libraries can be found.  
```
$ getlibs Desktop/n_v1linux/n_v14 
libgtk-1.2.so.0: libgtk1.2
libgdk-1.2.so.0: libgtk1.2
libgmodule-1.2.so.0: libglib1.2
libglib-1.2.so.0: libglib1.2ldbl
No match for libstdc++-libc6.2-2.so.3
The following i386 packages will be installed:
libglib1.2
libglib1.2ldbl
libgtk1.2
Continue [Y/n]? y
libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
Downloading ...
Installing libraries ...

```

```
$ Desktop/n_v1linux/n_v14 
Desktop/n_v1linux/n_v14: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

```

---

### Post by StooJ on 2009-01-19
From [this thread]("http://ubuntuforums.org/showthread.php?t=973961").

> **Partyboi2 said:**
> Try going [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/gutsy/libstdc++2.10-glibc2.2") and manually installing the deb. To manually install it double click on the deb after you have downloaded it.

This lets the game load, but I've yet to get it to work. Keyboard inputs don't seem to work yet.

---

