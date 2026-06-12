---
title: "Need help installing F4L (from .tar.gz or .deb)"
date: 2008-07-23
forum: General Help
---

### Post by pikabuntu on 2008-07-23
I have never successfully done this before and need some help, as there is no readme or anything in the file.

I am trying to install flash4linux

[http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)

---

### Post by lisati on 2008-07-23
What happened when you tried the instructions on the web page?

---

### Post by pikabuntu on 2008-07-23
it went ok until 

zach@zach-desktop:~/f4l-0.2$ make
make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.

---

### Post by Tim Sharitt on 2008-07-23
```
sudo apt-get install libqt3-headers
```
and try it again.

---

### Post by pikabuntu on 2008-07-23
> **Tim Sharitt said:**
> ```
sudo apt-get install libqt3-headers
```and try it again.
what does this install?

EDIT:

i still got the same error

---

### Post by pikabuntu on 2008-07-23
I don't know, but now that I think about it, I think that I was not doing the right thing.  I think that those were the instructions to update it...
If at all possible I would like to install it from the .tar.gz for the experience.

---

### Post by pikabuntu on 2008-07-23
How do you install from .deb?

---

### Post by iaculallad on 2008-07-23
> **pikabuntu said:**
> How do you install from .deb?

Using your terminal:

```
sudo dpkg -i application_filename.deb
```

---

### Post by Tim Sharitt on 2008-07-23
> **pikabuntu said:**
> what does this install?
It installs the files needed to compile qt3 applications. That's about all I know about compiling qt apps. Sorry I can't be of more help. :(

---

### Post by the_real_fourthdimension on 2008-07-23
> **pikabuntu said:**
> How do you install from .deb?

You can also just double-click it in ubuntu.

---

### Post by pikabuntu on 2008-07-23
i got an error :

zach@zach-desktop:~/Desktop$ sudo dpkg -i f4l_0.2-1_i386.deb
(Reading database ... 206685 files and directories currently installed.)
Preparing to replace f4l 0.2-1 (using f4l_0.2-1_i386.deb) ...
Unpacking replacement f4l ...
dpkg: dependency problems prevent configuration of f4l:
 f4l depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
 f4l depends on libqt3c102-mt (>= 3:3.3.4-3); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing f4l (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 f4l
zach@zach-desktop:~/Desktop$

---

### Post by pikabuntu on 2008-07-23
double clicking gets me to this window that says i have broken dependencies, i fix them, then i double click on it again and i get this:

error: dependency is not satisfiable: libqt3c102-mt

---

### Post by pikabuntu on 2008-07-23
that's ok anyway, i'm giving up on this for now :(

---

### Post by steveneddy on 2008-07-23
First I always download the files to my desktop.

You want to open a terminal.

Go to the desktop and right click on the file and select Extract.

A folder is created.

Now we want to **[COLOR="Blue"]cd[/COLOR]** to the directory.

(**[COLOR="Blue"]change directory[/COLOR]**)

In terminal

```
cd ~/Desktop/**[COLOR="Blue"]name_of_folder[/COLOR]**
```

Find the read me. It will say something like

./configure
make
make install

So, in terminal you will

```
./configure
```

and let it run, then

```
make
```

after that runs type

```
sudo make install
```

After that is finished, type

```
sudo make clean
```

That should do it for you.

---

### Post by the_real_fourthdimension on 2008-07-23
Try "sudo apt-get install libqt3c102-mt" in your terminal, then double-clicking again.  You're using the right process; you've just got unmet dependencies.

EDIT:  you may need to install this package instead: libqt3-mt.  It seems to be a replacement package.

---

### Post by pikabuntu on 2008-07-23
there's no readme :(

zach@zach-desktop:~/Desktop/f4l-0.2.1$ ./configure
bash: ./configure: No such file or directory

---

### Post by pikabuntu on 2008-07-23
> **the_real_fourthdimension said:**
> Try "sudo apt-get install libqt3c102-mt" in your terminal, then double-clicking again.  You're using the right process; you've just got unmet dependencies.

EDIT:  you may need to install this package instead: libqt3-mt.  It seems to be a replacement package.

zach@zach-desktop:~$ sudo apt-get install libqt3-mt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt3-mt is already the newest version.
libqt3-mt set to manually installed.
The following packages were automatically installed and are no longerrequired:
  libstdc++5 gcc-3.3-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded


It only seems to want libqt3c102-mt because it still says that when i double click... :confused:

---

### Post by the_real_fourthdimension on 2008-07-23
> **pikabuntu said:**
> zach@zach-desktop:~$ sudo apt-get install libqt3-mt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt3-mt is already the newest version.
libqt3-mt set to manually installed.
The following packages were automatically installed and are no longerrequired:
  libstdc++5 gcc-3.3-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded


It only seems to want libqt3c102-mt because it still says that when i double click... :confused:

You can download that from here: [http://packages.debian.org/sarge/libqt3c102-mt](http://packages.debian.org/sarge/libqt3c102-mt)
Let's hope that you already have all its dependencies installed on your system!

---

### Post by iaculallad on 2008-07-23
> **pikabuntu said:**
> i got an error :

zach@zach-desktop:~/Desktop$ sudo dpkg -i f4l_0.2-1_i386.deb
(Reading database ... 206685 files and directories currently installed.)
Preparing to replace f4l 0.2-1 (using f4l_0.2-1_i386.deb) ...
Unpacking replacement f4l ...
dpkg: dependency problems prevent configuration of f4l:
 f4l depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
 f4l depends on libqt3c102-mt (>= 3:3.3.4-3); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing f4l (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 f4l
zach@zach-desktop:~/Desktop$

With that error, use:

```
apt-get install -f
```

To fix dependency.

---

### Post by pikabuntu on 2008-07-23
what do I do with it now that I have downloaded it?

---

### Post by aysiu on 2008-07-23
One of these threads may help you:
[HOWTO: Install F4L](http://ubuntuforums.org/showthread.php?t=69156&highlight=install+f4l)
[install tar .bz2 flash for linux](http://ubuntuforums.org/showthread.php?p=4737022#post4737022)

---

### Post by pikabuntu on 2008-07-23
> **iaculallad said:**
> With that error, use:

```
apt-get install -f
```To fix dependency.

I've tried that, it just does the same thing again afterwards :(

---

### Post by the_real_fourthdimension on 2008-07-23
The same thing - double click it.  We're hoping that the files it depends on are already installed on your machine.  But the command above should work.
Usually installing from a deb or tarball is really simple.  It's just that this one depends on obsolete packages.

---

### Post by pikabuntu on 2008-07-23
i got an error saying conflicting packages: not installing libqtc102-mt

---

### Post by pikabuntu on 2008-07-23
Is there any alternative to f4l i could use?


(p.s. thank you whoever combined these threads)

---

### Post by pikabuntu on 2008-07-23
Thanks for everyone that has helped so far
I am getting off of the computer for the night so i don't kick it 
help would be greatly appreciated.  :)

---

### Post by pikabuntu on 2008-07-26
What can I do? It says "conflicting pakages: not installing libqtc102-mt"

---

### Post by dannymichel on 2009-07-26
> **pikabuntu said:**
> what do I do with it now that I have downloaded it?

bump

---

### Post by amine.hch on 2010-01-10
try :

[https://bugs.launchpad.net/ubuntu/+bug/195030]("https://bugs.launchpad.net/ubuntu/+bug/195030")
to create a lancer :

type : app
commande :/usr/local/bin/f4lm

---

