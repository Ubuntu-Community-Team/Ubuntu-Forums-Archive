---
title: "Lirc: How to install?"
date: 2005-03-19
forum: Hardware &amp; Laptops
---

### Post by mayco on 2005-03-19
Hi, I have almost all my hardware running in Hoary, except for my infrared remote. I used Fedora Core 3 before, and it worked perfectly there.
Can somebody give me a quick walktrough how to install lirc, because i'm a bit lost atm...

---

### Post by fido on 2005-03-20
[QUOTE=mayco]Hi, I have almost all my hardware running in Hoary, except for my infrared remote. I used Fedora Core 3 before, and it worked perfectly there.
Can somebody give me a quick walktrough how to install lirc, because i'm a bit lost atm...[/QUOTE]
 I also would like to know this it seems the ubuntu package is setup differently then the standard package and it would be useful to have a ubuntu specific tutorial

---

### Post by zoro_for_ubuntu on 2005-03-23
I know that in debian-like systems you have to install lirc package and lirc-modules-source package and compile modules in debian-way. I do it, but the result are modules with .o extension while right extension for 2.6 kernel is .ko;
in fact insmod answer the modules are in wrong format.
can anyone help us?
bye bye

zoro, who loves ubuntu

---

### Post by mayco on 2005-03-31
[QUOTE=zoro_for_ubuntu]I know that in debian-like systems you have to install lirc package and lirc-modules-source package and compile modules in debian-way. I do it, but the result are modules with .o extension while right extension for 2.6 kernel is .ko;
in fact insmod answer the modules are in wrong format.
can anyone help us?
bye bye

zoro, who loves ubuntu[/QUOTE]
 come on, i really want to use my remote, ubuntu is the best (most userfriendly) distro i've tried so far, but it just sucks that i can't use my remote!

i think the compilescripts aren't modified for 2.6 :(

when i configure lirc-modules-source, i get this message:

/usr/src/linux/ is not a valid kernel source tree.

any idea's, or somebody who is so kind to help me (us) out?

thanks!

edit: a lot can be found here: [http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=lirc-modules-source](http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=lirc-modules-source)

---

### Post by Cary Litchford on 2005-04-11
Yes, I just went through this headache yesterday.  I spent hours trying to get my Hauppauge PVR-250 remote working.

First, do not bother installing lirc or lirc-x you've successfully built and installed the lirc modules.   Once the lirc-modules are built and in place, the lirc install will configure for your hardware.  At least it did for me.

I've tried so many things that there may be more steps missing, but here goes (oh, and you're better off trying to use EVERYTHING from Synaptic package manager and not compiling from source):

1.  Install linux-source (I'm using 2.6.10 kernel), linux-headers, and lirc-modules-source.
2.  Open a root terminal and go to /usr/src.
3.  You should see 2 tar files and the new linux-headers-2.6.10 subdirectory
4.  Extract the tar files:  tar -xjvf linux-source-2.6.10.tar.bz2
5.  tar -xvzf lirc-modules.tar.gz
6.  Now you should have the source directories linux-source-2.6.10 and modules under /usr/src.
7.  If you have a /usr/src/linux directory, check (ls -l /usr/src) to see that it is a symlink to the new linux-source-2.6.10 directory.  If it isn't, move it to linux_old or something.  Then, create the link:  ln -s /usr/src/linux-source-2.6.10 /usr/src/linux
8.  Follow the directions in /usr/src/modules/lirc/README for 'To recompile the LIRC kernel modules'.  By the way, I left off the -revision flag and it still worked.  If no errors, then proceed to the next step.  If errors, then you may have some more steps to get your /usr/src/linux tree in shape.  I can possibly help with that, but let's hope that it doesn't get to that.
9.  If step 8 was successful, it created a debian package in /usr/src that begins lirc-modules-2.6.10... and has a suffix of .deb.  If you made it this far, you're home free.
10.  Install the .deb package:  dpkg -i <full name of lirc-modules..deb here>
11.  Check in /lib/modules.  For me, it created a 2.6.10 subdirectory and basically put the modules in the wrong place.  So, I had to move the entirer 'misc' subdirectory into the specific directory /lib/modules/2.6.10-5-386/.
12.  Update the modules:  depmod -ae && update-modules
13.  Install the modules:  modprobe lirc_dev
14.  Install the modules:  modprobe lirc_i2c

Once this has been successful, you can proceed with installing lirc and lirc-x from Synaptic Package Manager.  You should check with the "terminal" screen available inside the Synaptic UI while these packages install.  They may ask you to configure your card.

I apologize in advance if these steps seem sketchy.  There's no current howto for lirc that I'm aware of.  There are some really old ones out on the net that can give you grief.

Let me know if this helps out.  Any errors you might encounter will probably jog my memory.

Cary

---

### Post by fido on 2005-04-11
ok I appreciate someone finally posting something that may be of some help to this ubuntu lirc issue. But could you go into a little more detail about how you made your .deb package I keep getting errors. I think its my tree if you could help me out I would really appreciate it. I made the symbolic link pointing the linux directory to my linux-source-2.6.10 directory but I still get some errors. Thanks.

---

### Post by Rumo on 2005-04-15
Thanks for the nice walkthrough, Cary.

I still have some problems: The modules_image builds and installs nicely but the lirc-modules won't load. 

The .deb-package installed the modules in the following directory: /lib/modules/2.6.11/misc. I copied these directory to my actual module-directory /lib/modules/2.6.11-e3 (I tried ./misc ./drivers/input/i2c and several other places), but "depmod -ae && update.modules && modprobe lirc_dev" won't work - "FATAL: Module lirc_dev not found." I have absolutely no idea what went wrong.


Btw you won't need kernel-headers if kernel-source is installed.

---

### Post by slapps on 2005-04-17
[QUOTE=Rumo] but "depmod -ae && update.modules && modprobe lirc_dev" won't work - "FATAL: Module lirc_dev not found." I have absolutely no idea what went wrong.

.[/QUOTE]

I've got the same problem, i can't load my modules. :-| 

And i need the source to build the module, with the headers miss the file : bttv.h

slapps

---

### Post by slapps on 2005-04-17
I succeed to install lirc on my kubuntu, i give you the FRENCH link, wich help me to install lirc.

[http://mythubu.free.fr/phpBB2/viewtopic.php?t=99&sid=2e87babca566ad76d09b4db797c10a84](http://mythubu.free.fr/phpBB2/viewtopic.php?t=99&sid=2e87babca566ad76d09b4db797c10a84)

by hoping that help you.

Slapps

---

### Post by laurens on 2005-04-19
I might have found a solution for the problem of the not-loading .o files. They might require adding to /etc/modules/ivtv or, if you don't have a hauppauge card, to /etc/modules.conf. I'll try the following later today:

```

5. Update your /etc/modules.conf (or /etc/modutils/ivtv), adding the following
   lines if they don't exist:
    alias char-major-61 lirc_i2c
    add above ivtv lirc_dev lirc_i2c
    
   Then run:
    # update-modules (only if you're using modutils)
    # depmod -ae

```

THis is from [http://216.239.59.104/search?q=cache:1S-XEPEmME8J:205.209.168.201/~ckennedy/ivtv/OLD_good-ones/ivtv-0.1.10-pre2-ck100z/doc/README.lirc+setup+for+modutils+lirc](http://216.239.59.104/search?q=cache:1S-XEPEmME8J:205.209.168.201/~ckennedy/ivtv/OLD_good-ones/ivtv-0.1.10-pre2-ck100z/doc/README.lirc+setup+for+modutils+lirc)

Other sources which indicate this could be the/a problem: 
[http://www-isl.mach.uni-karlsruhe.de/~hi93/myth/mythtv_debian_epia_pvr350_walkthrough](http://www-isl.mach.uni-karlsruhe.de/~hi93/myth/mythtv_debian_epia_pvr350_walkthrough)
[http://www.mythtv.org/docs/mythtv-HOWTO-22.html#ss22.2](http://www.mythtv.org/docs/mythtv-HOWTO-22.html#ss22.2)
[http://www.mythtv.org/docs/mythtv-HOWTO-22.html#pvr250](http://www.mythtv.org/docs/mythtv-HOWTO-22.html#pvr250)

Edit:
Also, keep an eye out for [http://www.slash32.com/ubuntu-myth.html](http://www.slash32.com/ubuntu-myth.html) from a thread at [http://www.ubuntuforums.org/showthread.php?t=25814&page=2](http://www.ubuntuforums.org/showthread.php?t=25814&page=2) - there too seems to be a solution soon.

---

### Post by laurens on 2005-04-20
I tried yesterday, but this time I did not manage to compile the drivers, so couldn't check if adding them to /etc/modutils/ivtv works. WIll try again soon, though.

---

### Post by fackamato on 2005-04-22
I'm trying to get this to work.

I install everything, and go to /usr/src/modules/lirc/ and to ./setup.sh, but that doesn't give me the options to choose what remote I have or anything. It can't build either, says invalid kernel source dir. I forced some header/source dirs and it spit out lots of errors on make. If anyone has built lirc modules for 2.6.10-5-686-smp then let me know. :)

edit: and compiling from source works, but it gives me "invalid module format" on insmod/modprobe.

---

### Post by tlepes on 2005-04-29
For all you **Audigy 2 ZS** owners trying to get your remotes working with LIRC, there will be one more hurdle to jump.  I am not sure if this applies to other Audigy products or not..  I have what I have, ya know?  Anyway...

Once you do get LIRC installed properly, you still won't see anything coming from the Audigy2 when you try to use the remote.  If you're observant, you'll notice that the IR LED on the external sound module doesn't blink when you push buttons on the remote either.  This is because the Audigy2 IR receiver needs to be "initialized".  Once you properly initialize the device it will work fine until a cold boot.

Fortunately, the initialization is simple.  You need to pass a special string to the MIDI out of the sound card and your IR port will come alive.  You will even notice that the IR indicator LED starts to flash when you press buttons on the remote, indicating that it is receiving the IR signals.  The simplest way to do this is to create a bash script and execute it during either boot or session login, whichever is your pleasure.  I called mine start-audigy-ir as shown here...

```
 $ cat start-audigy-ir
#!/bin/bash

echo -e '\360\000\040\041\141\000\000\000\177\000\367' > /dev/snd/midiC1D1
```

Now it is important to note that in my configuration, the Audigy 2 is installed as my secondary sound card.  My motherboard has audio also, and I use that for all my system sounds and such.  I only use the Audigy for music and such, since it it such a nice card for that. This works for me since I can have the music volume separate from the system sounds (like startup/shutdown and GNOME sound events).

So if your Audigy 2 is sound card 1 like mine, this will work for you.  If your Audigy 2 is your only sound card, or your primary one (card 0), you will need to modify that command slightly...

The "C1" in "/dev/snd/midiC1D1" means Card 1.  Change it to "/dev/snd/midiC0D1" for Card 0 and you're good to go!

Good Luck and Happy Hacking!!!

Peace,
Tim

---

### Post by lbm on 2005-05-02
Hi!
If you do not want to move the modules after installing you can install them in the correct dir by doing the following (with bash as shell):
[list]
[*]Install and extract lirc-modules and kernel-source (see 04-11-2005 09:14 PM Cary Litchford [ahh -and thanks :)])
[*]Go to kernel-source-dir
[*]```
export MODULE_LOC=/usr/src/modules
```
[*]```
make-kpkg --append-to-version -5-686 modules_image
```
[*]```
cd ..
``` and install the generated package
[/list] 

I assumed your kernel-package-suffix is -5-686 and you extracted the lirc-modules in /usr/src.

You can find out your kernel-version with:
```
cat /proc/version
```
in the case of the above example it was 2.6.10-5-686

Cheers,
Thorsten

---

### Post by Haegin on 2005-10-09
How do I fill out my /usr/src/lirc-modules-src.conf file?

Currently it looks like this:
```

#   lirc-modules-source config file used by Debian GNU/Linux

# Coma separated list of lirc kernel drivers to build
LIRC_MODULES="serial"

# Serial module configuration
LIRC_SERIAL_PORT=""
LIRC_SERIAL_IRQ=""
LIRC_SERIAL_CFLAGS=" -DLIRC_SERIAL_SOFTCARRIER"

# Sir module configuration
LIRC_SIR_PORT="UNCONFIGURED"
LIRC_SIR_IRQ="UNCONFIGURED"
LIRC_SIR_CFLAGS="UNCONFIGURED"

# Parallel module configuration
LIRC_PARALLEL_PORT="UNCONFIGURED"
LIRC_PARALLEL_IRQ="UNCONFIGURED"
LIRC_PARALLEL_TIMER="UNCONFIGURED"

```

My IR device is a lego mindstorms transmitter and reciever connected to a serial port (the only one on my pc).

Thanks

---

### Post by syph on 2005-12-19
[QUOTE=mayco]

when i configure lirc-modules-source, i get this message:

/usr/src/linux/ is not a valid kernel source tree.
[/QUOTE]
My apologies to bump an old thread, this is the first hit on google when doing a search on "/usr/src/linux/ is not a valid kernel source tree", so I figured I'd write the sollution here for other people to find.

```
touch /usr/src/linux/Rules.make
```

---

### Post by Bananas21ca on 2005-12-20
Now i get "Couldn't build LIRC kernel modules"

---

### Post by Jeffrae on 2006-03-22
Hello,

Trying to compile the lirc-modules

I was struggling through the untill I brought in build essentials. . Well I am still struggling so I guess that is just a little comment..

When I do

sudo make-kpkg --revision 2.6.12-10.30 modules_image

I get asked tons and tons of questions like.......

[SIZE="1"]Local version - append to kernel release (LOCALVERSION) [] (NEW) Y
Support for paging of anonymous memory (swap) (SWAP) [Y/n/?] (NEW) Y
System V IPC (SYSVIPC) [Y/n/?] y
POSIX Message Queues (POSIX_MQUEUE) [N/y/?] (NEW)
BSD Process Accounting (BSD_PROCESS_ACCT) [Y/n/?] y
[/SIZE]

What is going on?  None of the pertaint o lirc and I don't know how to answer EVERY single question..

Thanks,
Jeff P

---

### Post by stefanr on 2006-03-22
Jeff, you get all these questions because the configuration for your kernel-source is not yet in the right place when you first unpack the linux-source package. That is because the configuration file is system dependent, but the kernel source is not. The configuration file for your system is in /boot and it's called config-*. Figure out which is the correct one for your running kernel (try 'uname -r' to find that out) if there are multiple files like that and copy it to /usr/src/linux/.config

I am trying to make-kpkg the lirc-modules, but it creates a deb containing .o files instead of .ko, which are in the wrong format, obviously. Anyone has an idea about that?

---

### Post by stefanr on 2006-03-22
Concerning my own problem, I resorted to the instructions on [http://www.abarbaccia.com/content/view/18/33/]("http://www.abarbaccia.com/content/view/18/33/") and ended up with a working setup.

---

### Post by Jeffrae on 2006-03-23
Thanks for that tip!! :)

I see it made many of the questions autoanswer..

I am still getting many querstion about EIDE, Digi Intl. RightSwitch SE-X support  and etc...  

Here is the example...

[http://paste.ubuntu-nl.org/11024]("http://paste.ubuntu-nl.org/11024")


Jeff

---

### Post by Jeffrae on 2006-03-28
This worked...

I used the headers instead..

sudo apt-get update
sudo apt-get install linux-headers-`uname -r` lirc-modules-source
cd /usr/src
sudo rm -rf linux-headers-`uname -r`/modules
sudo tar xzf lirc-modules.tar.gz
sudo mv modules linux-headers-`uname -r`
cd linux-headers-`uname -r`
sudo -s
CC=gcc-3.4 make-kpkg modules_image

---

### Post by Jeffrae on 2006-03-29
I was able to chop a little farther..
but I ran into another snag...

jeffrae@ubuntuPC:/lib/modules/2.6.12-10-386/misc$ ls
lirc_serial.o
jeffrae@ubuntuPC:/lib/modules/2.6.12-10-386/misc$ sudo depmod -ae && update-modules
jeffrae@ubuntuPC:/lib/modules/2.6.12-10-386/misc$ sudo modprobe lirc_i2c FATAL: Module lirc_i2c not found.

It doesn't find it.  Sometihng need to point to the o file?

Sorry I am using Breezy and on a Hoary forum..  this thread has just been so great!

Thanks,
Jeff

---

### Post by encompass on 2006-04-21
I am creating a how-to as we speak.  I hope it helps when it comes out.

---

### Post by dragonfyre13 on 2006-05-03
Make sure that you are loading the correct module. There is a possibility that itt doesn't take lirc_i2c, it could take lirc_serial like mine.

---

### Post by Scorpuk on 2006-07-07
> **Jeffrae said:**
> This worked...

I used the headers instead..

sudo apt-get update
sudo apt-get install linux-headers-`uname -r` lirc-modules-source
cd /usr/src
sudo rm -rf linux-headers-`uname -r`/modules
sudo tar xzf lirc-modules.tar.gz
sudo mv modules linux-headers-`uname -r`
cd linux-headers-`uname -r`
sudo -s
CC=gcc-3.4 make-kpkg modules_image


Tried doing the above, but ended with an error message:

```
john@silverstone:~$ sudo su
Password:
root@silverstone:/home/john# uname -r
2.6.15-25-amd64-generic
root@silverstone:/home/john# sudo apt-get update
Get: 1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get: 2 http://security.ubuntu.com dapper-security Release [30.9kB]
Get: 3 http://gb.archive.ubuntu.com dapper Release.gpg [189B]
Get: 4 http://gb.archive.ubuntu.com dapper-updates Release.gpg [189B]
Hit http://gb.archive.ubuntu.com dapper Release
Get: 5 http://gb.archive.ubuntu.com dapper-updates Release [30.9kB]
Get: 6 http://security.ubuntu.com dapper-security/main Packages [27.1kB]
Hit http://gb.archive.ubuntu.com dapper/main Packages
Hit http://gb.archive.ubuntu.com dapper/restricted Packages
Hit http://gb.archive.ubuntu.com dapper/main Sources
Hit http://gb.archive.ubuntu.com dapper/restricted Sources
Hit http://gb.archive.ubuntu.com dapper/universe Packages
Hit http://gb.archive.ubuntu.com dapper/universe Sources
Get: 7 http://security.ubuntu.com dapper-security/restricted Packages [4077B]
Get: 8 http://security.ubuntu.com dapper-security/main Sources [7105B]
Get: 9 http://gb.archive.ubuntu.com dapper-updates/main Packages [39.4kB]
Get: 10 http://security.ubuntu.com dapper-security/restricted Sources [974B]
Get: 11 http://www.beerorkid.com dapper Release.gpg [189B]
Get: 12 http://gb.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get: 13 http://gb.archive.ubuntu.com dapper-updates/main Sources [23.8kB]
Get: 14 http://gb.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Hit http://www.beerorkid.com dapper Release
Hit http://www.beerorkid.com dapper/main Packages
Fetched 165kB in 1s (113kB/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@silverstone:/home/john# sudo apt-get install linux-headers-2.6.15-25-amd64-generic lirc-modules-source
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@silverstone:/home/john# sudo apt-get install linux-headers-2.6.15-25-amd64-generic lirc-modules-source
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  debconf-utils debhelper html2text linux-headers-2.6.15-25
Suggested packages:
  dh-make kernel-source
Recommended packages:
  kernel-package
The following NEW packages will be installed
  debconf-utils debhelper html2text linux-headers-2.6.15-25
  linux-headers-2.6.15-25-amd64-generic lirc-modules-source
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 8611kB of archives.
After unpacking 79.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com dapper/main debconf-utils 1.4.72ubuntu9 [30.9kB]
Get: 2 http://security.ubuntu.com dapper-security/main linux-headers-2.6.15-25 2.6.15-25.43 [6907kB]
Get: 3 http://gb.archive.ubuntu.com dapper/main html2text 1.3.2a-3 [115kB]
Get: 4 http://gb.archive.ubuntu.com dapper/main debhelper 5.0.7ubuntu13 [506kB]
Get: 5 http://gb.archive.ubuntu.com dapper/universe lirc-modules-source 0.7.1pre2-11ubuntu1 [196kB]
Get: 6 http://security.ubuntu.com dapper-security/main linux-headers-2.6.15-25-amd64-generic 2.6.15-25.43 [858kB]
Fetched 8611kB in 36s (236kB/s)
Preconfiguring packages ...
Selecting previously deselected package debconf-utils.
(Reading database ... 79873 files and directories currently installed.)
Unpacking debconf-utils (from .../debconf-utils_1.4.72ubuntu9_all.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3_amd64.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.7ubuntu13_all.deb) ...
Selecting previously deselected package linux-headers-2.6.15-25.
Unpacking linux-headers-2.6.15-25 (from .../linux-headers-2.6.15-25_2.6.15-25.43_amd64.deb) ...
Selecting previously deselected package linux-headers-2.6.15-25-amd64-generic.
Unpacking linux-headers-2.6.15-25-amd64-generic (from .../linux-headers-2.6.15-25-amd64-generic_2.6.15-25.43_amd64.deb) ...
Selecting previously deselected package lirc-modules-source.
Unpacking lirc-modules-source (from .../lirc-modules-source_0.7.1pre2-11ubuntu1_amd64.deb) ...
Setting up debconf-utils (1.4.72ubuntu9) ...

Setting up html2text (1.3.2a-3) ...

Setting up debhelper (5.0.7ubuntu13) ...
Setting up linux-headers-2.6.15-25 (2.6.15-25.43) ...

Setting up linux-headers-2.6.15-25-amd64-generic (2.6.15-25.43) ...
Setting up lirc-modules-source (0.7.1pre2-11ubuntu1) ...

root@silverstone:/home/john# cd /usr/src
root@silverstone:/usr/src# rm -rf linux-headers-2.6.15-25-amd64-generic /modules
root@silverstone:/usr/src# tar xzf lirc-modules.tar.gz
root@silverstone:/usr/src# mv modules linux-headers-2.6.15-25-amd64-generic
root@silverstone:/usr/src# cd linux-headers-2.6.15-25-amd64-generic
root@silverstone:/usr/src/linux-headers-2.6.15-25-amd64-generic# sudo -s
root@silverstone:/usr/src/linux-headers-2.6.15-25-amd64-generic# CC=gcc-3.4 make-kpkg modules_image
bash: make-kpkg: command not found
root@silverstone:/usr/src/linux-headers-2.6.15-25-amd64-generic#
```


Any help would be appreciated.

---

### Post by mazirian on 2006-07-15
Bummer.

I installed lirc liblircclient0 liblircclient-dev lirc-modules-source lirc-x kernel-package and linux-source-2.6.15

I extracted the kernel and lirc module soures in /usr/src and made the appropriate symlink for the kernel sources.  I also copied over the kernel config from /boot for my current kernel image package.

Then I ran sudo dpkg-reconfigure lirc-modules-source to generate the /etc/lirc/lirc-modules-source.conf file.

Then following the instructions in the lirc-modules-source readme file:

```

cd /usr/src/linux
sudo make-kpkg --append-to-version -26-k7 modules_image

```

And here is the sad failure:

```

make[1]: Entering directory `/usr/src/modules/lirc'
sed -e "s!\$KVERS!2.6.15.7-ubuntu1-26-k7!g; s!\$KSRC!/usr/src/linux!; s!\$KARCH!i386!; s!\$KEMAIL!bowman@mazirian.com!; s!\$KMAINT!BRB!; s!\$KDREV!10.00.Custom!; s!\$DEBDATE!Sat, 15 Jul 2006 20:39:50 -0400!" debian/control.in > debian/control
dh_testdir
# Add here commands to compile the package.
/usr/bin/make debconf
make[2]: Entering directory `/usr/src/modules/lirc'
/usr/bin/make -e -C drivers SUBDIRS="lirc_dev"
make[3]: Entering directory `/usr/src/modules/lirc/drivers'
Making all in lirc_dev
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_dev'
Makefile:8: **************************************************
Makefile:8: *** Makefile trick not undone, trying to recover *
Makefile:8: **************************************************
mv Makefile.automake Makefile
/usr/bin/make all
make[5]: Entering directory `/usr/src/modules/lirc/drivers/lirc_dev'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/lirc/drivers/lirc_dev modules \
		KBUILD_VERBOSE=1
make[6]: Entering directory `/usr/src/linux-source-2.6.15'
mkdir -p /usr/src/modules/lirc/drivers/lirc_dev/.tmp_versions

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

/usr/bin/make -f scripts/Makefile.build obj=/usr/src/modules/lirc/drivers/lirc_dev
  gcc -m32 -Wp,-MD,/usr/src/modules/lirc/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=athlon -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I /usr/src/modules/lirc/drivers/lirc_dev/../.. -I /usr/src/linux/include/  -DMODULE -DKBUILD_BASENAME=lirc_dev -DKBUILD_MODNAME=lirc_dev -c -o /usr/src/modules/lirc/drivers/lirc_dev/.tmp_lirc_dev.o /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c: In function âlirc_register_pluginâ:
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:352: warning: implicit declaration of function âclass_simple_device_addâ
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:383: warning: implicit declaration of function âclass_simple_device_removeâ
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c: In function âlirc_dev_initâ:
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:792: warning: implicit declaration of function âclass_simple_createâ
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:792: warning: assignment makes pointer from integer without a cast
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c: In function âcleanup_moduleâ:
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:832: warning: implicit declaration of function âclass_simple_destroyâ
/bin/sh: scripts/genksyms/genksyms: No such file or directory
make[7]: *** [/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.o] Error 1
make[6]: *** [_module_/usr/src/modules/lirc/drivers/lirc_dev] Error 2
make[6]: Leaving directory `/usr/src/linux-source-2.6.15'
make[5]: *** [lirc_dev.o] Error 2
make[5]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_dev'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_dev'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/usr/src/modules/lirc/drivers'
make[2]: *** [dev] Error 2
make[2]: Leaving directory `/usr/src/modules/lirc'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/lirc'
Module /usr/src/modules/lirc failed.

```

I tried copying Module.symvers from the kernel headers package but that just made things worse.

Any ideas?

---

### Post by mazirian on 2006-07-15
Hmm... [https://launchpad.net/distros/ubuntu/+source/lirc/+bug/35456](https://launchpad.net/distros/ubuntu/+source/lirc/+bug/35456)

I wasn't able to get this to work in the end.  However, for those of you still in the trenches, please know that modules-assistant is your friend.  It's much much much easier to work with the helper scripts it wraps up than to labor away tweaking your source tree.  Check out the fakesource command.

---

### Post by mazirian on 2006-07-16
I should mention that I am trying to build lirc_gpio, which is impossible to build using the lirc-modules-source package in dapper's universe repo right now (0.7.1pre2-11ubuntu1).

However, if you extract the the modules tarball from the version of this package in edgy into /usr/src, you can get it to build.

First, make sure you have a properly configured /etc/lirc/lirc-modules-source.conf file:

```

sudo dpkg-reconfigure lirc-modules-source

```

Select the drivers you want when debconf prompts you. You need to confirm that debconf wrote /etc/lirc/lirc-modules-source.conf. It didn't write the file for me the first time (there's a bug pending on that).

Prepare the kernel sources to build the modules against:

```

sudo aptitude install modules-assistant
sudo module-assistant fakesource

```

That will automatically install and prepare kernel sources that match your running kernel as closely as possible.  You should now have a new kernel source directory in /usr/src that is probably named linux-source-$(uname -r). Also, m-a probably didn't generate a version.h file, the lack of which caused me problems.  So...

```

sudo cp /boot/configfileforcurrentkernelimage /usr/src/linux-source-$(uname -r)/.config
cd /usr/src/fakesource
sudo make prepare

```

Now build the modules:

```

sudo module-assistant --text-mode --kernel-dir /usr/src/linux-source-$(uname -r) build lirc

```

The above should generate a deb for you to install with dpkg.

Once the deb is installed, cross your fingers, and...

```

sudo modprobe lirc_gpio

```

Fortunately, the 0.7 version of lirc didn't have any problems loading the resulting modules generated from 0.8 source.  Too late now to test the remote, but at least the module builds and loads.

---

### Post by danjl on 2006-08-11
Like so many others, I've struggled with the lirc install!  I'm there now though, so thought I'd share my experience.  I'm using lirc_serial and was having lots of problems getting it to start correctly on reboot.

First of all I followed the instructions above, but I'll repeat what worked for me.  Particularly, I think the first howto at the top worked down to my step 5 (the extra hassle is due to using lirc_serial)

1. Install linux-source (I'm using 2.6.15 kernel), linux-headers, and lirc-modules-source.
2. Open a root terminal and go to /usr/src.
3. get the latest lirc drivers from [www.lirc.org](www.lirc.org) - 0.8.0 at time of writing. save them in /usr/src
4. Untar and cd to /usr/src/lirc-<version>
5. follow the install instructions: this for me was just running 
./setup.sh && make install (picking lirc_serial.)
6. copy the lircd.conf to /etc/ . IF you can get the right one for your remote from [www.lirc.org](www.lirc.org), then do (I couldn't)
7. The module lirc_serial wouldn't load - claimed it was busy.  The solution is to do: setserial /dev/ttyS0 uart none
8. modprobe -i lirc_serial
9. chmod 666 /dev/lirc
10. lircd (or irrecord to test)

PROBLEMS:
1. /dev/lirc not created, using udev.  The solution for me was to modify the udev rule provided with lirc:
lirc.rules (goes in /etc/udev/rules.d/lirc.rules)
KERNEL="lirc[0-9]*",    NAME="lirc"
2. It still isn't booted properly.  I think the lirc_serial driver was getting loaded very early, I didn't figure out when.  The problem is we need to use the setserial command from above before it is.  I wrote this script to unload and reload it correctly:

#!/bin/sh
modprobe -r lirc_serial
setserial /dev/ttyS0 uart none
modprobe -i lirc_serial
chmod 666 /dev/lirc
lircd

which I put in /usr/local/sbin/lirc_start.sh

Then I created /etc/init.d/lirc:
#! /bin/sh
/usr/local/sbin/lirc_start.sh

And ran:sudo update-rc.d lirc defaults 20

THIS IS A VERY UGLY WAY OF DOING IT, but it worked for me!  If someone knows a better way, please say. Otherwise if you are struggling, I hope this gives you some hints  as to what might help.  I'm a long way from an expert so take this all with a pinch of salt!

---

### Post by mazirian on 2006-08-11
I'd strongly suggest using the debian packaging tools, they are, after all, what makes debian so great.  I have to rebuild the lirc modules to accomodate the new kernel that just entered the stable repository, so I'll provide a more detailed howto then if you like.  But essentially, I think it is better to grab the lirc sources from edgy (the lirc package sources now includes the module-sources as well) and use the debuild utility to build them into debs.  Then build the modules using my instructions above and install all the debs using apt(itude).  I did this and it worked wonderfully.  I didn't update this thread because it apeared no one was reading it.

---

### Post by Rusna on 2006-10-08
**mazirian:** A more complete howto would be a lot appreciated!
I'm strugling with my Technisat remote, lirc_serial?

---

### Post by mazirian on 2006-10-10
Well, I am not sure how things will work for you with that driver.  I understand that the lirc_serial driver gives people a lot of problems.  However, here's what I did to get the lirc_gpio driver working.  Note that I already had the lirc package and its dependancies, including the lirc-modules package, installed from my previous efforts.

Grab the lirc sources from experimental (you may need to add edgy's source repository to your /etc/apt/sources.list.):

```

mkdir ~/src/lirc
cd ~/src/lirc
apt-get source lirc
cd lirc-0.8.0

```

I only build the driver I care about in order to avoid problems with other dependancies I'd have to bring in from edgy. Edit debian/rules as follows, substituting your driver in place of mine:

```

    ./configure --build=$(DEB_BUILD_GNU_TYPE) --host=$(DEB_HOST_GNU_TYPE) \
        --prefix=/usr \
        --mandir=\$${prefix}/share/man \
        --infodir=\$${prefix}/share/info \
        --libdir=\$${prefix}/lib \
        --sysconfdir=/etc/lirc/ \
-       --with-driver=userspace \
+       --with-driver=leadtek_0010\
        --with-syslog=LOG_DAEMON \
        --enable-sandboxed

```

Use debuild to check for missing dependancies:

```

debuild -us -uc

```

Debuild may give you complaints about libusb and libasound being missing dependancies, but you can ignore these unless you are using one of the drivers they relate to, and I don't think you are.  Otherwise try installing any missing dependancies.  If you don't resolve all the dependancy issues, just force debuild to build the package without the missing dependancies:

```

debuild -d -us -uc

```

Debuild may raise a few gpg related errors at the end, but I believe the debs you need will be generated in any event and you can ignore the gpg errors.  The end result of running debuild should be a bunch of debs that you should install. 

The lirc-modules-source is now included in the lirc proper package now.  You will need to copy the lirc module sources directory to /usr/src, then build the modules against the proper kernel sources, as I outline here:

[http://ubuntuforums.org/showpost.php?p=1261540&postcount=29](http://ubuntuforums.org/showpost.php?p=1261540&postcount=29)

With any luck you'll be setting up irexec and controlling mplayer from your couch in no time.

---

### Post by kmart216 on 2006-10-17
I'm currently stuck getting the lirc kernel module to build.  When compiling I get an error that I2C_ALGO_BIT is not defined in file /usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.c.  

Another problem, the terminal I'm using doesn't print symbols in code when printing compiler messages, but the errors at line 392 and 464 are from the above problem.  I tried it on a console on the actual machine and I2C_ALGO_BIT is the symbol it printed.

Kernal version is: 2.6.15-27-386

Here is the output:

```
sed -e "s!\$KVERS!2.6.15.7-ubuntu1-27-386!g; s!\$KSRC!/usr/src/linux!; s!\$KARCH!i386!; s!\$KEMAIL!!; s!\$KMAINT!!; s!\$KDREV!10.00.Custom!; s!\$DEBDATE!Tue, 17 Oct 2006 23:34:39 -0400!" debian/control.in > debian/control
dh_testdir
# Add here commands to configure the package.
touch configure-stamp
dh_testdir
# Add here commands to compile the package.
/usr/bin/make debconf
make[1]: Entering directory `/usr/src/modules/lirc'
mkdir modules
/usr/bin/make -e -C drivers SUBDIRS="lirc_dev"
make[2]: Entering directory `/usr/src/modules/lirc/drivers'
Making all in lirc_dev
make[3]: Entering directory `/usr/src/modules/lirc/drivers/lirc_dev'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/lirc/drivers/lirc_dev modules \
                KBUILD_VERBOSE=1
make[4]: Entering directory `/usr/src/linux-source-2.6.15'
mkdir -p /usr/src/modules/lirc/drivers/lirc_dev/.tmp_versions
/usr/bin/make -f scripts/Makefile.build obj=/usr/src/modules/lirc/drivers/lirc_dev
  gcc -m32 -Wp,-MD,/usr/src/modules/lirc/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i486 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I /usr/src/modules/lirc/drivers/lirc_dev/../.. -I /usr/src/linux/include/  -DMODULE -DKBUILD_BASENAME=lirc_dev -DKBUILD_MODNAME=lirc_dev -c -o /usr/src/modules/lirc/drivers/lirc_dev/.tmp_lirc_dev.o /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c: In function â:
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:352: warning: implicit declaration of function â
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:383: warning: implicit declaration of function â
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c: In function â:
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:792: warning: implicit declaration of function â
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:792: warning: assignment makes pointer from integer without a cast
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c: In function â:
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:832: warning: implicit declaration of function â
  Building modules, stage 2.
/usr/bin/make -rR -f /usr/src/linux-source-2.6.15/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-source-2.6.15/Module.symvers vmlinux /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.o
*** Warning: "class_simple_create" [/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.ko] undefined!
*** Warning: "class_simple_device_remove" [/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.ko] undefined!
*** Warning: "class_simple_destroy" [/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.ko] undefined!
*** Warning: "class_simple_device_add" [/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.ko] undefined!
  gcc -m32 -Wp,-MD,/usr/src/modules/lirc/drivers/lirc_dev/.lirc_dev.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i486 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign    -DKBUILD_BASENAME=lirc_dev -DKBUILD_MODNAME=lirc_dev -DMODULE -c -o /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.mod.o /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.mod.c
  ld -m elf_i386 -m elf_i386 -r -o /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.ko /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.o /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.mod.o
make[4]: Leaving directory `/usr/src/linux-source-2.6.15'
mv Makefile.automake Makefile
make[3]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_dev'
make[3]: Entering directory `/usr/src/modules/lirc/drivers'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/usr/src/modules/lirc/drivers'
make[2]: Leaving directory `/usr/src/modules/lirc/drivers'
mv drivers/lirc_dev/lirc_dev.ko modules
/usr/bin/make -e -C drivers SUBDIRS="lirc_i2c"
make[2]: Entering directory `/usr/src/modules/lirc/drivers'
Making all in lirc_i2c
make[3]: Entering directory `/usr/src/modules/lirc/drivers/lirc_i2c'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/lirc/drivers/lirc_i2c modules \
                KBUILD_VERBOSE=1
make[4]: Entering directory `/usr/src/linux-source-2.6.15'
mkdir -p /usr/src/modules/lirc/drivers/lirc_i2c/.tmp_versions
/usr/bin/make -f scripts/Makefile.build obj=/usr/src/modules/lirc/drivers/lirc_i2c
  gcc -m32 -Wp,-MD,/usr/src/modules/lirc/drivers/lirc_i2c/.lirc_i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i486 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I /usr/src/modules/lirc/drivers/lirc_i2c/../.. -I /usr/src/linux/include/  -DMODULE -DKBUILD_BASENAME=lirc_i2c -DKBUILD_MODNAME=lirc_i2c -c -o /usr/src/modules/lirc/drivers/lirc_i2c/.tmp_lirc_i2c.o /usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.c
/usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.c: In function â:
/usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.c:392: error: â undeclared (first use in this function)
/usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.c:392: error: (Each undeclared identifier is reported only once
/usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.c:392: error: for each function it appears in.)
/usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.c: In function â:
/usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.c:464: error: â undeclared (first use in this function)
make[5]: *** [/usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.o] Error 1
make[4]: *** [_module_/usr/src/modules/lirc/drivers/lirc_i2c] Error 2
make[4]: Leaving directory `/usr/src/linux-source-2.6.15'
make[3]: *** [lirc_i2c.o] Error 2
make[3]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_i2c'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/modules/lirc/drivers'
make[1]: *** [i2c] Error 2
make[1]: Leaving directory `/usr/src/modules/lirc'
make: *** [build-stamp] Error 2

```

---

### Post by Akleson on 2006-10-18
Hi

I am struggeling with my lirc installation as well. I am using the new MCE. Sofar I got my modules compiled and installed. I used the module-assistant way mentioned here. It worked fine.

The modules are installed and are in /lib/modules/2.6.16-27-386/misc. When I run modprobe lirc_dev it cant finde the modules. What is wrong? I did not get any warning or so. Should I move them manually to a different dir or can I tell modprobe where to look as well.

My best wishes
Akleson

---

### Post by Akleson on 2006-10-18
> **Akleson said:**
> Hi

I am struggeling with my lirc installation as well. I am using the new MCE. Sofar I got my modules compiled and installed. I used the module-assistant way mentioned here. It worked fine.

The modules are installed and are in /lib/modules/2.6.16-27-386/misc. When I run modprobe lirc_dev it cant finde the modules. What is wrong? I did not get any warning or so. Should I move them manually to a different dir or can I tell modprobe where to look as well.

My best wishes
Akleson

solved i simply forgot the depmod

---

### Post by mazirian on 2006-10-18
@kmart216: what version of the lirc-modules are you trying to compile?

---

### Post by kmart216 on 2006-10-18
I'm not really sure if this denotes the version, but this is the contents of the config.h file that was in the tar module source tar file:

```
#define DEV_LIRC        "lirc"
#define LIRC_MAJOR  61
```

---

### Post by kmart216 on 2006-10-18
Looked at some different stuff and I'm even more confused.  

Again from the files extracted from the source tarball (which BTW I got by doing a 'apt-get install lirc-modules-source') there are some debian associated files, 'changelog' and 'copyright'.

The newest entry for 'changelog' is: 
```
lirc (0.7.1pre2-11ubuntu1) dapper; urgency=low
```

So I guess that's my version.  I also see the 'copyright' file has this:
```
It was downloaded from http://download.sourceforge.net/LIRC/lirc-0.6.3.tar.gz
```

So I don't know what's the real version of it.

I looked online and I see that version 0.8.1 has a different drivers/kcompact.h file that defines I2C_ALGO_BIT to 0 if not defined.  I guess I'll modify my kcompact.h file and see if it works.

---

### Post by mazirian on 2006-10-18
Right, the problem, at least for me, is that you cannot build the version of lirc in the stable (dapper) repository.  It's an oustanding bug no one has done anything about.  I think you need to try and build the sources for the lirc package from unstable (edgy), which should be version 8.

To check, try: sudo dpkg -l | grep lirc

---

