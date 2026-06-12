---
title: "Installing RemotePad: Help, please!"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by BEND IT 7 on 2009-05-09
Hi, everyone.

I have a laptop running VistaHP and Ubuntu 8.10 as a dual boot (going to upgrade to 9.04 soon).  I just purchased a new iPod Touch (2nd gen) and absolutely love it (I wish I could sync with Ubuntu and not have to spend so much annoying amounts of time in Windows, but that's a different topic).  I did get a VNC app to work with Ubuntu (I will post a thread on that another time), which is really sweet.

Anyway, I am trying to get RemotePad ([http://www.tenjin.org/RemotePad/downloads.html](http://www.tenjin.org/RemotePad/downloads.html)) to work, and I do not have a clue what to do with the "source package." I always just install .debs or Synaptic packages and do not mess with source code.  So, I was wondering if somebody could please give me a step by step on installation and then how to execute the code.

fyi, RemotePad is a free iPhone app that functions as a mouse over wifi for a computer.  What I am trying to get to work is the RemotePad server on my computer.

Thanks!

---

### Post by Partyboi2 on 2009-05-09
Hi, open a terminal and install build-essential
```
sudo apt-get install build-essential
```then change directory to where you have the downloaded RemotePadServer-1.10-X11-Source.tgz, so for example if its own your Desktop ```
cd ~/Desktop
``` then extract it with
```
tar xvzf RemotePadServer-1.10-X11-Source.tgz 
``` then change into the extracted source directory
```
 cd RemotePad\ Server/
```then run
```
./configure
``` make sure that there are no errors or complants about missing packages, if so install the required  development (dev) packages of the missing dependencies
Then build it with
```
make 
``` If that completes without errors you can then install with
```
sudo make install
```

---

### Post by oimikey on 2009-07-02
I tried the method above and it didn't work for me, so after checking [remotepad's forum]("http://groups.google.com/group/remotepad/topics"), I installed libXtst-dev using synaptic package manager. 

I then followed the process again but this time slightly changing step 4 to ```
cd RemotePad\ Server/X11/
```

After the last step, I entered ```
remotepad
``` into the terminal to run the remotepad server 

I had to turn my firewall off to get my iPhone and PC talking to each other, I haven't worked out how to configure the firewall yet :lolflag: but I'm working on that now.

---

### Post by BEND IT 7 on 2009-07-02
Thank you so much for the replies, guys.  I will be testing this later.  I am actually on Ubuntu 8.04 LTS now...works much better on my hardware.  Anyway, if it works, I'll let you know with the exact steps I used.  Thanks again!

---

### Post by BEND IT 7 on 2009-07-03
I changed my directory to ```
cd RemotePad\ Server/X11/
``` and when I ran the ```
./configure
``` command, I got the following reply:

```
corey@corey-laptop:~/Desktop/RemotePad Server/X11$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for sqrt in -lm... yes
checking for struct sockaddr.sa_len... no
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking X11/Xlib.h usability... no
checking X11/Xlib.h presence... no
checking for X11/Xlib.h... no
configure: error: X Window System is required.
```

---

### Post by BEND IT 7 on 2009-07-05
Help, please?  This is not super important, but something tells me it should be fairly easy to fix that problem.

Thank you.

---

### Post by Fatal Equinox on 2009-07-09
> **BEND IT 7 said:**
> Help, please?  This is not super important, but something tells me it should be fairly easy to fix that problem.

Thank you.

You need to go to synaptic package and isntall "libx11-dev package"  and then "libx11-dev"....  However after that you may get stuck where i am... which is  at the make command....

i get 

```
make: *** No rule to make target `remotepad.o', needed by `remotepad'.  Stop.
``` so i don't know where to go after that.

---

### Post by m3alnemer on 2009-09-27
> **BEND IT 7 said:**
> I changed my directory to ```
cd RemotePad\ Server/X11/
``` and when I ran the ```
./configure
``` command, I got the following reply:

```
corey@corey-laptop:~/Desktop/RemotePad Server/X11$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for sqrt in -lm... yes
checking for struct sockaddr.sa_len... no
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking X11/Xlib.h usability... no
checking X11/Xlib.h presence... no
checking for X11/Xlib.h... no
configure: error: X Window System is required.
```

you can solve by 

> Please install a libXtst development library package (maybe libXtst-
dev or libXtst-devel) and re-run configure. 

source[http://groups.google.com/group/remotepad/browse_thread/thread/4bc9af12d710f371?pli=1]("http://groups.google.com/group/remotepad/browse_thread/thread/4bc9af12d710f371?pli=1")

Regards

---

### Post by m3alnemer on 2009-09-27
Thanks Partyboi

```
me@me-laptop:/usr/local/bin$ ./remotepad
RemotePad Server for X11 version 1.10
Application launched.
Failed to bind socket: Address already in use

```

what do i do? :popcorn:

---

### Post by m3alnemer on 2009-10-01
bbbumbbb

---

### Post by m3alnemer on 2009-10-01
solved by restart!

---

### Post by jodonald on 2010-07-01
> **m3alnemer said:**
> Thanks Partyboi

```
me@me-laptop:/usr/local/bin$ ./remotepad
RemotePad Server for X11 version 1.10
Application launched.
Failed to bind socket: Address already in use

```

what do i do? :popcorn:

I got this and it just means that it's already running but you just didn't get the ip addy.  Restart RemotePad and you should be golden.

---

