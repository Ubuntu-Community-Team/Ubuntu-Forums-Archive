---
title: "no rule to make target  kernel/bounds.c"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by l_Thorium on 2009-01-22
Hello,

I must compile my kernel for my webcam driver. But after the command "make prepare", I've got that :

make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.
make: *** [prepare0] Error 2

so I've try sudo apt-get --reinstall install linux-headers-`uname -r` and I've installed the kernel source, but without any success... 

It's the same error with other kernel version.

Can you help me please ?

$(uname -r) is 2.6.27-9-server

---

### Post by HubertB on 2009-02-22
Hi!

Installing the kernel sources using apt / aptitude / synaptic / whatsoever only puts the compressed source code into /usr/src. You need to uncompress the sources:

```
$ cd /usr/src
$ sudo tar -xvjf linux-source-$YOUR_VERSION_HERE.tar.bz2
```

Then just change into the new /usr/src/linux-source-$YOUR_VERSION_HERE directory and built your kernel like you used to :-)

So long

---

### Post by jellylogix on 2009-03-16
Thank you. This helped me with the same problem.

---

### Post by StarkGläubige on 2009-07-05
Sorry, I'm new in it, what does $YOUR_VERSION_HERE mean? Is it my kernel version?

Thanks.

---

### Post by StarkGläubige on 2009-07-09
Sorry for my last reply. I installed linux-source and then I understood what you meant with $YOUR_VERSION_HERE.

Thanks!

---

### Post by amikam on 2009-09-22
I have the  same problem but my archive is uncompressed already ! But i still get the same message 
[B]
***@***-laptop:~$ cd microdia 
***@***-laptop:~/microdia$ sudo make
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [driver] Error 2
[/B]
I'm trying to setup my built-in webcam on Lenovo 3000 N100 (Ubuntu 9.04) 
I need help !!!!

---

### Post by Kinnunen on 2009-09-27
I have same problem, and installing linux-source didn't not help, this is a fresh ubuntu 9.04 installation and ran latest updates.
This command has also been used:
```
$sudo apt-get install build-essential linux-headers-$(uname -r)
```I always get the following error:
```
kinnunen@Atom:~/Desktop/rtl8192u_linux_2.6.0006.1031.2008$ sudo make install
[sudo] password for kinnunen: 
make[1]: Entering directory `/home/kinnunen/Desktop/rtl8192u_linux_2.6.0006.1031.2008/ieee80211'
make -C /lib/modules/2.6.28-15-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/kinnunen/Desktop/rtl8192u_linux_2.6.0006.1031.2008/ieee80211'
make: *** [install] Error 2
kinnunen@Atom:~/Desktop/rtl8192u_linux_2.6.0006.1031.2008$ 
```Please help!!!

---

### Post by yuszuv on 2009-10-12
Same problem here. Please help!

---

### Post by Nalroff on 2009-10-17
same kind of prob here. bump.

---

### Post by GeryonD on 2009-10-28
> **HubertB said:**
> Hi!

Installing the kernel sources using apt / aptitude / synaptic / whatsoever only puts the compressed source code into /usr/src. You need to uncompress the sources:

```
$ cd /usr/src
$ sudo tar -xvjf linux-source-$YOUR_VERSION_HERE.tar.bz2
```

Then just change into the new /usr/src/linux-source-$YOUR_VERSION_HERE directory and built your kernel like you used to :-)

So long

This works, you need to make sure when you compile your code it's pointing to the Linux sources and not the headers.  You will see in the error where it's point to.  For example:

make[1]: Entering directory `/usr/src/linux-headers-2.6.28-16-generic'

You can see it's still pointing to the headers.

---

### Post by kedarm on 2009-11-04
Hi!

I tried to follow the instructions [(here)]("http://www.linuxforums.org/forum/linux-kernel/116863-how-compile-device-driver-program.html") as I was getting the following error when trying to build kernel modules (a simple hello_world module) -
> error: linux/module.h: No such file or directory,
and got the following errors -
> ~/workspace/work/rtl$ sudo make
make -C /lib/modules/2.6.28-15-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function &#8216;conf_askvalue&#8217;:
scripts/kconfig/conf.c:104: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function &#8216;conf_choice&#8217;:
scripts/kconfig/conf.c:306: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [all] Error 2

I've been following the steps above to get past the error. I first tried installing the linux-headers -
```
sudo apt-get --reinstall install linux-headers-`uname -r`
```
but I cannot see any file of the name linux-source-2.6.28-15-generic.tar.bz2. In fact, I don't see any compressed file (tar.bz2) at all!

Have I missed out installing something?

---

### Post by HubertB on 2009-11-04
Since you've installed linux-headers, you won't find a file called "linux-source".

If you need the complete kernel sources, you have to install the package named "linux-source" by running

```

sudo apt-get install linux-source

```

Mind the difference between linux-**headers** and linux-**source**. 

Headers are being unpacked automatically to /usr/src whereas the installation of linux-source places a .tar.bz2 file in the directory /usr/src. This .tar.bz2 file (which is only there if you installed linux-**source**) has to be unpacked by running these commands:

```

cd /usr/src
sudo tar xvjf linux-source-$YOUR_VERSION_HERE.tar.bz2

```

---

### Post by kedarm on 2009-11-04
Hi!

Thanks. I followed the steps mentioned -
```
~$ sudo apt-get install linux-source
~$ cd /usr/src
/usr/src$ sudo tar -xjvf linux-source-2.6.28.tar.bz2
```
However, I still get the following error -
> make -C /lib/modules/2.6.28-15-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [all] Error 2

In my /usr/src directory, I have two header folders -
> /usr/src$ ls -al
linux-headers-2.6.28-15-generic
linux-headers-2.6.28-15
...
Should the linux-source-2.6.28.tar.bz2 be extracted to a folder 'linux-source-2.6.28-15-generic' or 'linux-source-2.6.28-15', instead of 'linux-source-2.6.28'?

Thanks

---

### Post by HubertB on 2009-11-05
Something is very strange here. You said that you installed linux-source and also unpacked it, but your /usr/src directory contains only 2 subdirectories.

I just verified the above stated procedure. On a fresh installed Ubuntu 9.10 system, /usr/src contains this:
```

$ ls /usr/src/
linux-headers-2.6.31-14
linux-headers-2.6.31-14-generic

```

Then, I went ahead:
```

$ sudo apt-get install linux-source
$ cd /usr/src
$ sudo tar xvjf linux-source-2.6.31.tar.bz2
$ ls /usr/src
linux-headers-2.6.31-14          
linux-headers-2.6.31-14-generic
linux-source-2.6.31
linux-source-2.6.31.tar.bz2

```

Maybe you made a mistake while copy-pasting the output of ls /usr/src since I even don't see a linux-source-$VERSION.tar.bz2?

PS: You could try creating a symlink to the extracted kernel sources (provided that they are extracted in /usr/src). Make sure you replace the version numbers which the ones that you need:
```

$ sudo ln -s /usr/src/linux-source-2.6.31 /usr/src/linux

```

---

### Post by Asem on 2009-11-13
hi

i was facing a similar problem when i was trying to install  a wireless driver
the solution was not to use sudo with make install, instead try this
sudo su
make 
make install
i don't know a reson for this but it worked that way

---

### Post by rlue on 2009-11-17
Working as superuser instead of sudoing worked for me, too!

---

### Post by larry85704 on 2009-11-20
Ok, something is broken here. I tried doing a make clean and sudo make and sudo install. No luck. My problem is that I get a "No rule to make target 'kernel/bounds.c ... ' in the make install step. I am running 9.10. 

When I try and do a make in the /usr/src/linux-headers directory it doesn't work either. Same error. Why are we discussing the linux-sources?

---

### Post by volodymyr on 2009-12-07
Anyone solved the problem? I got exactly the same problem at Ubuntu 9.10 ...

---

### Post by HubertB on 2009-12-07
Guys, please read the thread more carefully!

**bounds.c** is in the file **/usr/src/linux-source-2.6.31.tar.bz2** (hint: This version number applies to 9.10) which is only there if you have the package **linux-source** installed [COLOR="Red"]**AND**[/COLOR] extracted (see above on how to do this).

Furthermore you've already been given another hint: Try compiling and installing using **sudo -s** instead of **sudo**. Using sudo -s you'll become superuser aka root so you have to use this command only once:
```

$ sudo -s
# a_command_to_be_executed <- executed with full priviledges - please be careful!
# another_command_with_root_rights

```

Please don't take that personally, but I'm tired of answering this question over and over again.

If you still need help, let me know.

---

### Post by RegPerrin on 2010-01-10
I am trying to compile, make and install the latest Ralink Wireless drivers on my fresh install of Ubuntu 9.1 64 bit.
I get the following error message when I type "make":
make -C tools
make[1]: Entering directory `/home/testrig4ub64/Desktop/Wireless installers/RT2870_LinuxSTA_V2.3.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/testrig4ub64/Desktop/Wireless installers/RT2870_LinuxSTA_V2.3.0.0/tools'
/home/testrig4ub64/Desktop/Wireless installers/RT2870_LinuxSTA_V2.3.0.0/tools/bin2h
make: /home/testrig4ub64/Desktop/Wireless: Command not found
make: *** [build_tools] Error 127

I have done pretty much all that has been suggested above. Does Ubuntu not come with a compiler? Why does it not recognise the 'make' command like all the other linux flavours?

Already done the following:
sudo apt-get update
sudo apt-get install build-essential
Still get errors as though it does not know what make means.

The same process compiled happily on another machine so I am fairly sure it is not the source code which is wrong.
Can anyone help here please?

Ed: I have followed all the Compiling instructions on this site, so I have checkinstall, but that still returns the same error.

---

### Post by RegPerrin on 2010-01-10
I have answered my own question.
I discovered that for some reason the process does not like to be inside too many folders !
My problem was that I had put the extracted folder from the tar.gz inside another on my desktop, instead of extracting the folder itslef to the desktop.

Wrong:
Desktop->WirelessInstalls->RT2870_LinuxSTA_V2.3.0.0

Correct:
Desktop->RT2870_LinuxSTA_V2.3.0.0

The makefile sits inside the RT2870_LinuxSTA_V2.3.0.0 folder.

Whether or not this makes sense, or why it should make any difference at all, I don't know. Nevertheless, I simply extracted the RT2870_LinuxSTA_V2.3.0.0 folder straight to the desktop, opened in terminal, typed checkinstall, and bingo, it all works.

Cheers for anyone who started giving this some thought for me.

---

### Post by HubertB on 2010-01-10
I think the problem is the "space" between "Wireless" and "installers" in the directory name "/home/testrig4ub64/Desktop/Wireless installers/RT2870_LinuxSTA_V2.3.0.0/tools" because it says "make: /home/testrig4ub64/Desktop/Wireless: Command not found"

---

### Post by go_linux on 2010-01-10
In some case some extra steps are required to make it compile.

Doing apt-get install linux-sources and decompressing the file is not sufficient.
After doing that step you also need to:
1. cd /usr/src/linux-source-{Version}/
    (To find the value to replace in {Version} do: uname -r and use only the dot separated numbers, if
     there is dash something, please discard everything after and including the dash)

2. sudo cp -vi /boot/config-`uname -r` .config

3. sudo make oldconfig

4. cd /lib/modules/`uname -r`

5. Check if the build softlink is pointing to /usr/src/linux-header-* by doing:
    ls -l

6. If you see something like:    
       ... build -> /usr/src/linux-headers-2.6.31-16-generic
    then proceed with 6.1, otherwise jump to step 7
6.1 then switch the softlink, first by deleting build:
   sudo rm build
6.2 and then create the new link by doing:
   sudo ln -s /usr/src/{Version} build

7. It is not required for this, but it won't hurt if you create 
   /usr/src/linux symlink
   for that do:
   sudo ln -s /usr/src/{Version} /usr/src/linux

8. Now go ahead and build those drivers

Good Luck! ;)

---

### Post by joyboyhardik@yahoo.com on 2010-03-10
There is no bounds.c or bounds.h or nay bounds fine in kernal folder call it source or header

I have similar problem

I tried everything
still i get this

root@ubuntu:/usr/src/linux-headers-2.6.31-20-generic# make
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make: *** [prepare0] Error 2

---

### Post by HubertB on 2010-03-11
Really? I bet 1000 bucks that it's there. Are you in? :-) 

Running Ubuntu 10.04:

```

$ sudo apt-get install linux-headers-2.6.32-16 linux-source-2.6.32
$ cd /usr/src
$ sudo tar xvjf linux-source-2.6.32.tar.bz2
$ find /usr/src -name "bounds.*" -ls
2629663    4 -rw-r--r--   1 root     root          526 Dec  3 04:51 ./linux-source-2.6.32/kernel/bounds.c
2502234    4 -rw-r--r--   1 root     root          224 Mar  9 22:49 ./linux-headers-2.6.32-16-generic-pae/include/linux/bounds.h
2507692    4 -rw-r--r--   1 root     root         3738 Mar  9 22:49 ./linux-headers-2.6.32-16-generic-pae/kernel/bounds.s

```

Please wire 500 dollar each to Debian and to to Canonical as a donation for their great work. Thanks :-)

---

### Post by joyboyhardik@yahoo.com on 2010-03-11
hmmm.. tell me onething.. 

i am reading this book in which it has a hello.c program for the driver thing..

after saving that it asks me to use this command in the kernel

make

ddoes this command take hours?

---

### Post by HubertB on 2010-03-12
Compiling the kernel indeed does take some time.

---

### Post by scctor on 2010-03-28
I m a new to Ubuntu and to device drivers.
Even I have same problem as discussed in this thread.
The package linux-source-2.6.31.14 is not found.
--------------
sudo apt-get install linux-source-2.6.31.14
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-source-2.6.31.14
--------------

Any help is appreciated.

---

### Post by HubertB on 2010-03-28
You're running Karmic, right? Then this is what you need:

```

$ sudo apt-get install linux-source-2.6.31

```

---

### Post by scctor on 2010-03-29
This is what I get when I do
sudo apt-get install linux-source-2.6.31

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libncurses-dev ncurses-dev kernel-package libqt3-dev
The following NEW packages will be installed:
  linux-source-2.6.31
0 upgraded, 1 newly installed, 0 to remove and 242 not upgraded.
Need to get 62.2MB of archives.
After this operation, 62.3MB of additional disk space will be used.
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main linux-source-2.6.31 2.6.31-20.58
  Could not resolve 'in.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main linux-source-2.6.31 2.6.31-20.58
  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-source-2.6.31_2.6.31-20.58_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-source-2.6.31_2.6.31-20.58_all.deb)  Could not resolve 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

What next ? :(

---

### Post by HubertB on 2010-03-31
The package mirror archive you are using (in.archive.ubuntu.com) is not reachable. Try using a different mirror. In GNOME, just use System => Administration => Software Sources and select a different mirror in the field "Download from".

---

### Post by scctor on 2010-04-01
Thanks. It works.
I m able to compile my hello world module.

---

### Post by HubertB on 2010-04-01
You're welcome :)

---

### Post by gramound on 2010-04-12
> **HubertB said:**
> You're running Karmic, right? Then this is what you need:

```

$ sudo apt-get install linux-source-2.6.31

```

I thought the purpose of the linux-headers package was to build drivers without the full kernel source. :confused: Is it broken? If so, can someone file a bug report?

I really enjoyed compiling my drivers on hardy (without linux-source). :)

---

### Post by mo.mashi on 2010-06-22
> **l_Thorium said:**
> Hello,

I must compile my kernel for my webcam driver. But after the command  "make prepare", I've got that :

make[1]: *** No rule to make target `kernel/bounds.c', needed by  `kernel/bounds.s'. Stop.
make: *** [prepare0] Error 2

so I've try sudo apt-get --reinstall install linux-headers-`uname -r`  and I've installed the kernel source, but without any success... 

It's the same error with other kernel version.

Can you help me please ?

$(uname -r) is 2.6.27-9-server


Hey buddy,

I had the same problem and just found the solution:

[COLOR=DarkRed][U][I][B]you're trying to compile the linux header directory. 

if it looks something like [/B][/I][/U][/COLOR]
[B]
/usr/src/linux-headers-YOUR-KERNEL-VERSION[/B] - eg. mine is linux-headers-2.6.32-21

**[COLOR=DarkRed]_*you're trying to compile the wrong folder.*_[/COLOR]**

Just go to [www.kernel.org](www.kernel.org) and download the kernel of your choice. 

To uncompress the compressed source archive, be sure use the command they specify in the readme file and not the uncrompress command that comes up in the contextual menu when you right click on the archive in your file manager (eg. if you use Dolphin, don't right click on the file and select an option from the contextual menu like "Extract Archive Here" as that will give you errors when trying to compile). 

Open a command prompt window. To extract the source code from the archive, go to the directory that has your compressed archive and use:

        **gzip -cd linux-2.6.XX.tar.gz | tar xvf -**

   or
        **bzip2 -dc linux-2.6.XX.tar.bz2 | tar xvf -**

(where XX is your version of linux, include the minus sign in the command)

After that: 

**make menuconfig **

(if you want to turn on certain modules in the kernel, I used this menu to turn on support for HFS+ and mac partitions as well as Virtualization so that my Virtualbox application can run faster).

**make**
(go have a coffee, it takes a while)

for anything else, check the readme file, it's very complete.

---

### Post by outleradam on 2010-07-05
I had to do ```
apt-get removebuild-essential linux-headers-$(uname -r)
```to get it to install the drivers.  I'm rebooting now

---

### Post by outleradam on 2010-07-05
seems to have worked

---

### Post by difuiv250385 on 2011-11-08
Hi all,

Here is the simplest solution.
use **"make -C $(KDIR) M=$(PWD) modules**" instead of "**make -C $(KDIR) SUBDIR=$(PWD) modules**"

and it works ...!!! :P

---

### Post by oldos2er on 2011-11-08
Closed, please don't bump old threads.

---

