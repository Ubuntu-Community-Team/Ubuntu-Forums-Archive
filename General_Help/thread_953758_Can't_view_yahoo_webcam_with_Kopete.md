---
title: "Can't view yahoo webcam with Kopete"
date: 2008-10-20
forum: General Help
---

### Post by 22-250 on 2008-10-20
I just installed Kopete with hope of being able to view a friend's yahoo webcam, when I click on 'request to view cam' I get the message:
> I cannot find the jasper image convert program.
jasper is required to render the yahoo webcam images.
Please see [http://wiki.kde.org/tiki-index.php?page=Kopete%20Webcam%20Support](http://wiki.kde.org/tiki-index.php?page=Kopete%20Webcam%20Support) for further information.

I'm running 8.04 Ubuntu (and am new to it) the link there talks about Suse, not Ubuntu...?

I downloaded the "JasPer version 1.900.1 source distribution (current version)"
and it's on the desktop as a .zip what do I do now?

Thanks

---

### Post by Hangwire on 2008-10-20
Hi,

Your problem is fairly common. I will help you with it.

First off, here is where to download Jasper. 

[http://www.ece.uvic.ca/~mdadams/jasper/#download](http://www.ece.uvic.ca/~mdadams/jasper/#download)

Save the file to your desktop.

Applications > Accessories > Terminal

cd to Desktop in terminal

then

cd <jasperFileNameHere>

then

./configure

then

make

then

sudo make install

If you receive a "make command not found" thingy, then first type this in the terminal:

```
sudo apt-get install build-essential
```

Click on the archive or w/e it is, it should install properly. 


Hope I helped. :)

---

### Post by 22-250 on 2008-10-20
thanks!

---

### Post by 22-250 on 2008-10-20
This is where I'm at, do I need to put in the "sudo apt-get install build-essential"? or what do I do now? 
> a429@empty:~$ cd Desktop
a429@empty:~/Desktop$ cd <jasper-1.900.1.zip>
bash: syntax error near unexpected token `newline'
a429@empty:~/Desktop$ ./configure
bash: ./configure: No such file or directory
a429@empty:~/Desktop$ make
make: *** No targets specified and no makefile found.  Stop.
a429@empty:~/Desktop$ sudo make install
[sudo] password for a429: 
make: *** No rule to make target `install'.  Stop.
a429@empty:~/Desktop$ 


---

### Post by Hangwire on 2008-10-20
> **22-250 said:**
> This is where I'm at, do I need to put in the "sudo apt-get install build-essential"? or what do I do now?

Yes, I believe so. Yet I think its installed already. Check by that command. 

Also, here's a link and a detailed tutorial on how to compile programs (the thing you need to do). 

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Or you can try [https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU) for instance ;D But I dont think they will reply.

---

### Post by 22-250 on 2008-10-20
Ok, I did the sudo apt-get install build-essential, here's what happened. Am I done, or do I still need to click on the archive and install?? 

> a429@empty:~/Desktop$ sudo apt-get install build-essential
[sudo] password for a429: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  glibc-doc manpages-dev libstdc++6-4.2-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 8611kB of archives.
After this operation, 34.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-21.42 [698kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libc6-dev 2.7-10ubuntu4 [3344kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7 [1187kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main g++-4.2 4.2.3-2ubuntu7 [2784kB]  
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1440B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1 [7066B]
Fetched 8611kB in 1min59s (71.8kB/s)                                           
Selecting previously deselected package linux-libc-dev.
(Reading database ... 146764 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-21.42_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu4_i386.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Setting up linux-libc-dev (2.6.24-21.42) ...
Setting up libc6-dev (2.7-10ubuntu4) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

Setting up build-essential (11.3ubuntu1) ...
a429@empty:~/Desktop$ 



---

### Post by Hangwire on 2008-10-20
You did excellent.
Now follow the tutorial which I gave you from my first post. It should work with no problems.

---

### Post by 22-250 on 2008-10-20
Like this?
> a429@empty:~/Desktop$ cd <jasper-1.900.1.zip>
bash: syntax error near unexpected token `newline'
a429@empty:~/Desktop$ ./configure
bash: ./configure: No such file or directory
a429@empty:~/Desktop$ make
make: *** No targets specified and no makefile found.  Stop.
a429@empty:~/Desktop$ sudo make install
[sudo] password for a429: 
make: *** No rule to make target `install'.  Stop.
a429@empty:~/Desktop$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
a429@empty:~/Desktop$ 


---

### Post by Hangwire on 2008-10-20
Dude.

Terminal.

cd to your desktop. dont use the "< >" i should have told you.

cd /home/<yourusername, dont add the <> just the username>/Desktop/Jasper.

Extract the file in a folder in your desktop. For example create a folder Jasper and extract the zip file in it. 

Then you do all the stuff in the tutorial. Starting with ./configure

Good Luck!

---

### Post by 22-250 on 2008-10-20
ok, I'll try it again later, have to go to work. Thanks for your help so far!

---

### Post by 22-250 on 2008-10-20
Okay, here's what I did

had the file *jasper1.900.1.zip* on my desktop

opened terminal

> cd Desktop

>  cd /home/a429/Desktop/jasper-1.900.1.zip
 

Then I made a new folder on desktop, moved the *jasper1.900.1.zip* file into it, opened the new folder, right clicked the file and selected Extract here.

> ./configure
 
> make
 
> sudo make install

entered password

> sudo apt-get install build-essential


Here's what I have in the terminal:
> a429@empty:~$ cd Desktop
a429@empty:~/Desktop$ cd /home/a429/Desktop/jasper-1.900.1.zip
bash: cd: /home/a429/Desktop/jasper-1.900.1.zip: No such file or directory
a429@empty:~/Desktop$ ./configure
bash: ./configure: No such file or directory
a429@empty:~/Desktop$ make
make: *** No targets specified and no makefile found.  Stop.
a429@empty:~/Desktop$ 
a429@empty:~/Desktop$ sudo make install
[sudo] password for a429: 
make: *** No rule to make target `install'.  Stop.
a429@empty:~/Desktop$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
a429@empty:~/Desktop$  

is this correct so far? what's the next step?

---

### Post by 22-250 on 2008-10-21
ok I did something else..
instead of doing the cd /home/username/Desktop jasper etc.zip
I did it to the new 'extracted' file inside the new folder (named jasper) so:
cd /home/username/Desktop/jasper/jasper-1.900.1

and followed the rest of the tutorial

When I pointed it to that extracted file it changed the prompt thing from:

a429@empty:~/Desktop$

to

a429@empty:~/Desktop/jasper/jasper-1.900.1$ 

it ran about 7 miles of text through the terminal

Don't really know what I did..haha but now that it finished, I get different results when trying to view a webcam..
When in Kopete and click Request webcam, or click accept to webcam invite, a popup from 'Yahoo-plugin Kopete' saying > webcam for is not available
and
> Webcam connection to the user could not be established.
Please relogin and try again.
Reason: 17 - 14 - operation is not supported
and
> Webcam connection to the user could not be established.
Please relogin and try again.
Reason: 3014772 - 14 - operation is not supported
:confused::confused:

---

### Post by Hangwire on 2008-10-21
Hm... weird. 
Dont CD to the .zip file. extract it in a folder, and cd to it. 
I believe you did that the second time though. 

Isnt there a INSTALL or HELP file somewhere in the extracted files? Copy whats in it.

---

### Post by 22-250 on 2008-10-21
This is from the extracted file (there's a document called INSTALL, inside it directs me to the following section of the .pdf JasPer Software Reference Manual)

> 2.4 Building the Software
Obviously, before the software can be built, the contents of the archive file containing the JasPer distribution
must be extracted.
     The JasPer code should compile and run on any platform with a C language implementation conforming
to ISO/IEC 9899:1999 [3] (i.e., the ISO C language standard) and supporting a subset of ISO/IEC 9945-1 [1]
(i.e., the POSIX C API). Only limited POSIX support is required (i.e., the open, close, read, write, and lseek
functions must be supported).
     Portability was a major consideration during the design of the JasPer software. For this reason, the
software makes minimal assumptions about the runtime environment. The code uses very little floating-point
arithmetic, most of which can be attributed to floating-point conversions in printf’s. This minimal use of
floating-point arithmetic should make the code much easier to port to platforms lacking hardware support for
floating-point arithmetic.
     The specific procedure required to build the JasPer software depends on the type of system involved.
Only two different build methods are supported. The first method is based on the well known make utility
and should work on most UNIX (or UNIX-like) systems. The second method is specifically tailored to the
needs of Microsoft Visual C under Microsoft Windows. In passing, we note that by using free software
such as Cygwin ([http://www.cygwin.com](http://www.cygwin.com)), one can also create a UNIX-like environment under Microsoft
Windows in which to build JasPer using the first method.
     If you are unfortunate enough to have a compiler that is not compliant with ISO/IEC 9899:1999, you
may need to make some changes to the code. Unfortunately, even some of the most popular C language
implementations do not strictly comply with the standard. One such example is Microsoft Visual C 6.0. Due
to the popularity of Visual C, however, several workarounds have been added to the JasPer code to ensure
that it will compile successfully with Visual C.
     The current version of the JasPer software is known to compile in the following environments:
     • Red Hat Linux 7.3, GNU C 2.96, GNU Make 3.79.1
     • SunOS/SPARC 5.7, GNU C 2.95, SunOS make
     • Windows 2000 Professional, Microsoft Visual C 6.0
Of course, the software should compile successfully in many other environments as well. For example, past
versions of JasPer have been reported to build successfully in the following environments:
     • Apple Macintosh PPC G3, Rhapsody 5.6, GNU C 2.7.2.1
     • Power Macintosh, GNU/Linux 2.2.15pre9, GNU C 2.95.2
     • Sun SPARC, Solaris 2.7, GNU C 2.95.2
     • Compaq/DEC Alpha, OSF/1 4.0F, GNU C 2.95.2
     • IBM PowerPC, AIX 4.2, GNU C 2.95.2
     • HP 9000/712, HP-UX 10.20, GNU C 2.95.2
     • SGI Origin 200, IRIX 6.5, GNU C 2.95.2
     • OpenVMS Alpha 7.2-1 with Compaq C compiler V6.2-008 (after creating custom makefiles)
2.4. BUILDING THE SOFTWARE        5
2.4.1     Build Process for UNIX (or UNIX-Like) Systems
The JasPer software is intended to be built using the standard UNIX make utility (in conjunction with a
configure script).
    If you need a C compiler that is reasonably compliant with the ISO/IEC 9899:1999 standard, you can
obtain GNU C from the GNU Project web site (i.e., [http://www.gnu.org](http://www.gnu.org)). If you need an implementation
of the make utility, you can also obtain GNU Make from the the GNU Project web site. All GNU software is
free software.
    In what follows, $TOPDIR denotes the top level directory of the JasPer software distribution (i.e., the
directory containing the file named configure). To build the software, the following steps are required (in
order):
    1. Set the current working directory to the top level directory of the JasPer software distribution.
       To set the current working directory as required, type:
             cd $TOPDIR
       (where $TOPDIR is defined as described earlier in this section).
    2. Perform the initial configuration of the software.
       This is accomplished by running the configure script. This process allows important information about
       the system configuration to be determined. The configure script also generates makefiles from makefile
       templates. In theory, it should not be necessary to manually edit any of the makefile templates (i.e., the
       Makefile.in files) used by the configure program. To invoke the configure program, type:
             ./configure
       The configure script accepts a number of options. These options can be listed by invoking the configure
       command with the --help option. Unless you know what you are doing (or have problems with
       the default build settings), it is strongly recommended that you not override the default settings for
       configure.
       In some cases, it may be necessary to explicitly disable the use of the IJG JPEG library (i.e., libjpeg).
       This is accomplished by supplying the --disable-libjpeg option to configure. For example, such
       action may be required if the version of the JPEG library installed on your system is not compatible
       with the version of JasPer being built. Also, when building under the Cygwin environment, it may be
       neccessary to explicitly disable the use of the JPEG library.
       In some situations, it may be necessary to explicitly disable the use of the OpenGL libraries. This is
       accomplished by supplying the --disable-opengl option to configure.
    3. Compile and link the software.
       This is accomplished via the make command. To run the make program, type:
             make
    4. Install the software.
       This step may require special (e.g., superuser/administrator) privileges depending on the target direc-
       tory for installation. (The default installation directories are normally under /usr/local.) To install
       the executables, libraries, include files, and other auxiliary data, type:
             make install
Presuming that the build was successful, the executables for the JasPer application programs can be found in
the directory $TOPDIR/src/appl.


---

### Post by 22-250 on 2008-10-22
I got it working! Thanks a million

---

