---
title: "[SOLVED] Need help installing .tar"
date: 2008-09-27
forum: General Help
---

### Post by DougieFresh4U on 2008-09-27
Good morning every one :)
I am terrible at installing .tar files.  I would like to install this Mah Jong game called Netjan. Could some one please guide me in very simple terms?

 netjan-0.1.tar.bz2

---

### Post by Sorivenul on 2008-09-27
Just downloaded the file myself to help with this.  First, extract the archive with your favorite archive program.  Before you go forward make sure build-essential is installed, as you will need the included gcc to compile.
After that, open a terminal and move to the directory that was just created:
```
cd /path/to/netjan-0.1
```
After that, since it doesn't look like there are any config files, simply type:
```
make
```
then
```
make install
```

As a sidenote, my build failed with multiple errors and warnings.  Cheers!

---

### Post by kokkus on 2008-09-27
You can also sort the files manually.
usr is the program filder. Or usr/local for a specific users
Execute files = /bin
Icon files = /share/icons
program files = /lib
Help files = /share

Good luck.

---

### Post by DougieFresh4U on 2008-09-27
> **Sorivenul said:**
> Just downloaded the file myself to help with this.  First, extract the archive with your favorite archive program.  Before you go forward make sure build-essential is installed, as you will need the included gcc to compile.
After that, open a terminal and move to the directory that was just created:
```
cd /path/to/netjan-0.1
```
After that, since it doesn't look like there are any config files, simply type:
```
make
```
then
```
make install
```

As a sidenote, my build failed with multiple errors and warnings.  Cheers!

> **kokkus said:**
> You can also sort the files manually.
usr is the program filder. Or usr/local for a specific users
Execute files = /bin
Icon files = /share/icons
program files = /lib
Help files = /share

Good luck.

I'm lost  :confused::confused:

---

### Post by kokkus on 2008-09-27
> **DougieFresh4U said:**
> I'm lost  :confused::confused:

Ok? Why are you lost?

---

### Post by kokkus on 2008-09-27
Ok. Extract the archive to the desktop, go to terminal and type cd /home/yourhomefoldername/Desktop/netjan-0.1
Now you are in the folder.
now type "make" to sort the files automaticly where they belong.
Now type "make install" to set executer.
Now create a launcher (mahjongg)
Already in the games menu.

I guess this game is already in synatic too if this was too advanced for you, but you should do it this way because then you know how to install from archives for the future.

Good luck:)

---

### Post by DougieFresh4U on 2008-09-27
> **kokkus said:**
> Ok. Extract the archive to the desktop, go to terminal and type cd /home/yourhomefoldername/Desktop/netjan-0.1
Now you are in the folder.
now type "make" to sort the files automaticly where they belong.
Now type "make install" to set executer.
Now create a launcher (mahjongg)
Already in the games menu.

I guess this game is already in synatic too if this was too advanced for you, but you should do it this way because then you know how to install from archives for the future.

Good luck:)

Yes, it will be good for me to learn. Now here is what I have done(without success) 
dougie@DougiesLeanMachine:~$ cd/home/dougie/Desktop/netjan-0.1
bash: cd/home/dougie/Desktop/netjan-0.1: No such file or directory
dougie@DougiesLeanMachine:~$ cd/home/dougie/Desktop/netjan-0.1
bash: cd/home/dougie/Desktop/netjan-0.1: No such file or directory
dougie@DougiesLeanMachine:~$ cd/home/dougie/temp/netjan-0.1
bash: cd/home/dougie/temp/netjan-0.1: No such file or directory
dougie@DougiesLeanMachine:~$ 

I went looking for file and it's in 'temp' also it has to be  'Desktop' as there is an icon for downloaded file on desktop.
This is where I always get lost with .tar files..If I forgot some thing when I was in terminal, please let me know.
Thanks for your patients  :)
As for being in synaptic, thats not the same one. 
I have been trying to install Mahjong Medley from Gamehouse through 'wine' and not having any luck. Had it installed in Gusty.  It has over 300 different layouts.

---

### Post by kokkus on 2008-09-27
You are almost there
There should be a space after cd.
Here's the right command:
cd /home/dougie/Desktop/netjan-0.1

---

### Post by rossjman1 on 2008-09-27
You have to extract the tar.gz file, you can do this with file-roller (just double click the file and extract). In your cd statements, you have to put a space between cd and the path. So it would be like this:
```
cd /home/dougie/temp/netjan-0.1
```

---

### Post by kokkus on 2008-09-27
I think he's getting comfused more then helped now I'm afraid.

Ok step by step:

1. Download the archive file to your desktop.
2. Extrect it. (right-clck the file, and in the menu click extrect here)
3. Go to terminal and type 
```
cd /home/dougie/temp/netjan-0.1
``` (Now you are inside the Netjan folder)
4. Type 
```
make
```
This will sort the files in the folder to the right directories.
5. Type
```
make install
```
This will create the executer and launcher to the right category (games in this case) on your applications menu.

Good Luck:)

---

### Post by DougieFresh4U on 2008-09-27
I have tried many ways, terminal says:
```
dougie@DougiesLeanMachine:~$ cd /home/dougie/Desktop/netjan-0.1
bash: cd: /home/dougie/Desktop/netjan-0.1: No such file or directory
dougie@DougiesLeanMachine:~$ cd /home/dougie/temp/netjan-0.1
bash: cd: /home/dougie/temp/netjan-0.1: No such file or directory
dougie@DougiesLeanMachine:~$ cd /home/dougie/temp/netjan-0.1
bash: cd: /home/dougie/temp/netjan-0.1: No such file or directory
dougie@DougiesLeanMachine:~$ 
```
Now when I click to open from desktop (see screenshot)
I only did that to make sure it was on Desktop

---

### Post by Sorivenul on 2008-09-27
Looks like (from the screenshot) it should be:
xmahjongg-3.5 instead of netjen-0.1 in the cd command.
So try:
```
cd /home/dougie/Desktop/xmahjongg-3.5
```

---

### Post by DougieFresh4U on 2008-09-27
> **Sorivenul said:**
> Looks like (from the screenshot) it should be:
xmahjongg-3.5 instead of netjen-0.1 in the cd command.
So try:
```
cd /home/dougie/Desktop/xmahjongg-3.5
```

I had tried 2 different mahjong files and neither one will install for me.
I am gonna mark this thread 'solved' as I am frustrated and I am sure those that are helping me are getting frustrated as well.
Thanks to all who have helped

---

### Post by rossjman1 on 2008-09-27
**A breakdown of how to install**
1. You need to install some small programs so you can compile and install .tar.gz files.
```
sudo apt-get install build-essential
```

2. You ned to download and open the file, extract it's contents into a folder on the desktop.
3. Go to the folder
```
cd ~/Desktop/xmahjongg-3.5
```

4. Now you need to "make" the installation. Normally you would do a ./configure before this, but in this case you don't need to. If you get any errors please procede to step 6 or post the output here.
```
make
```

5. Now you need to install the application. If you get any errors please procede to step 6 or post the output here.
```
make install
```

6. (Optional) It appears that the program isn't able to be installed. This may be because you didn't install build-essential or the actual program has errors in it's code. The most common error is that the program has dependencies and you need to install them before you "make". We can tell you which one it is if you can post the output to make and make install.
You can still install the software. The way software was meant to be installed is APT. You can go to System > Administration > Synaptic Package Manager and search for xmahjongg, or you can install with apt:
```
sudo apt-get install xmahjongg
```
Note: This may be a slightly older version than the one on the website.

---

### Post by Sorivenul on 2008-09-28
+1 to rossjman1.

As I said in my original post, make sure you have build-essential installed, as it includes the compilers you will need to build and install most of your tarballed files.

Also of note, I was unable to successfuly build the first program, which I'm assuming means others would as well.  If the program is in the repository and unless you need the latest version, IMO it is advisable to install the program from the repository.  It is easier and will cause less problems than reinstalling and/or updating manually if you would ever wish to do so.  Just my two cents.  Good luck!

---

### Post by DougieFresh4U on 2008-09-28
> **Sorivenul said:**
> +1 to rossjman1.

As I said in my original post, make sure you have build-essential installed, as it includes the compilers you will need to build and install most of your tarballed files.

Also of note, I was unable to successfuly build the first program, which I'm assuming means others would as well.  If the program is in the repository and unless you need the latest version, IMO it is advisable to install the program from the repository.  It is easier and will cause less problems than reinstalling and/or updating manually if you would ever wish to do so.  Just my two cents.  Good luck!

The 'build-essential' is installed. These games are from 'The Linux Tome' They are not in repository (netjan) Thanks for help. I started the way your post says, but cannot get past 'make'

```
dougie@DougiesLeanMachine:~$ sudo apt-get install build-essential
[sudo] password for dougie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
The following packages were automatically installed and are no longer required:
  liboobs-1-4-dbg libgail-gnome-dbg libgdl-1-0 libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
dougie@DougiesLeanMachine:~$ cd ~/Desktop/xmahjongg-3.5
dougie@DougiesLeanMachine:~/Desktop/xmahjongg-3.5$ make
make: *** No targets specified and no makefile found.  Stop.
dougie@DougiesLeanMachine:~/Desktop/xmahjongg-3.5$ 

```

---

### Post by Sorivenul on 2008-09-28
In teh xmahjongg folder is a there a file called "configure"?  If so, you may have to run:
./configure

This often times created the Makefile needed to complete the "make", "make install" process.

EDIT:
Just downloaded the file from [www.linux.com](www.linux.com).  There is a "configure" script.  Run the indicated direction in the folder before you try "make" then "make install" and you should be headed in the right direction.

---

### Post by taladan on 2008-09-28
For clarity's sake and wholeness, you can extract tar files at the command line.

I usually create a temp/ directory in my home directory or on my desktop and move the archive there first before extracting (you don't know if they packaged the directory structure correctly or not)

```
mkdir ~/Desktop/temp;mv netjan-0.1.tar.bz2 ~/Desktop/temp;cd ~/Desktop/temp
```

Then extract it:

```
tar -jxf netjan-0.1.tar.bz2
```

then check the directory

```
ls
```

if they packaged the directory structure correctly, you'll need to cd <directoryname>

where <directoryname> = whatever directory is listed under there.

If all the files extracted out into the current folder, then you can run your:

```
./configure
```

then

```
make;make install
```

** Note: tar -jxf will extract .bz2 archives.  For tar.gz archives you'll want to use tar -zxf*

Hope this helps,

Tal

---

### Post by DougieFresh4U on 2008-09-28
Thanks so much for the help with understanding installation of '.tar' files. I did get a little farther along this time. It seems that the '.tar' files I choose to install are always troublesome. I got a whole lot of errors this time. Maybe the file is so old and non-functioning, here is some of what terminal spit out:


dougie@DougiesLeanMachine:~$ cd ~/Desktop/xmahjongg-3.5
dougie@DougiesLeanMachine:~/Desktop/xmahjongg-3.5$ ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for working const... yes
checking for inline... inline
checking how to run the C preprocessor... gcc -E
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking how to run the C++ preprocessor... c++ -E
checking for X... no
checking for strerror... yes
checking for gettimeofday prototype... 2
checking for integer typedefs... yes
checking for new.h... no
updating cache ./config.cache
creating ./config.status
creating Makefile
creating config.h
dougie@DougiesLeanMachine:~/Desktop/xmahjongg-3.5$ make;make install
gcc -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c clp.c
gcc -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c fmalloc.c
gcc -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c giffunc.c
gcc -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c gifread.c
gifread.c: In function ‘file_block_getter’:
gifread.c:91: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
gcc -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c gifx.c
c++ -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c permstr.cc
c++ -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c vectori.cc
In file included from vector.cc:1,
                 from vectori.cc:4:
vector.hh:8: error: ‘void* operator new(size_t, void*)’ may not be declared as static
vector.hh: In member function ‘void Vector<T>::push_back(const T&) [with T = short int]’:
vectori.cc:7:   instantiated from here
vector.hh:57: error: no matching function for call to ‘operator new(unsigned int, void*)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
vector.cc: In member function ‘bool Vector<T>::reserve(int) [with T = short int]’:
vectori.cc:7:   instantiated from here
vector.cc:55: error: no matching function for call to ‘operator new(unsigned int, void*)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
vector.cc: In member function ‘void Vector<T>::resize(int, const T&) [with T = short int]’:
vectori.cc:7:   instantiated from here
vector.cc:71: error: no matching function for call to ‘operator new(unsigned int,

---

