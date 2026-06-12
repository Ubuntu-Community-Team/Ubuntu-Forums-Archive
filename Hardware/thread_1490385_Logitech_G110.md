---
title: "Logitech G110"
date: 2010-05-22
forum: Hardware
---

### Post by marcozs on 2010-05-22
Hey everyone,

I got a new Logitech G110 keyboard [IMG]http://gamingweapons.com/image/logitech-g110-keyboard-01/logitech-g110-keyboard-00.jpg[/IMG].

I used the Logitech G15 settings, which seems to be the closer layout but I have a few problems:
- The G1-G12 keys are giving the same output as F1-F12 keys, so I can't actually use them
- The Super/windows key is not mapped neither left nor right one

Any help on this issues? Do you know if there's a better driver for it?

Thanks in advance

P.s.
Using Ubuntu 10.04 64bit

---

### Post by marcozs on 2010-05-22
Any idea?

---

### Post by marcozs on 2010-06-01
Bump...

---

### Post by dino99 on 2010-06-01
not so good news :(

[http://www.overclock.net/computer-peripherals/684125-issues-brand-new-logitech-g110-terrible.html](http://www.overclock.net/computer-peripherals/684125-issues-brand-new-logitech-g110-terrible.html)

[https://help.ubuntu.com/community/LogitechG15](https://help.ubuntu.com/community/LogitechG15)

[http://www.g15tools.com/node/193](http://www.g15tools.com/node/193)

---

### Post by GammaRay256 on 2010-06-05
I am also in the same situation.  I too have the G110 and am having the same problems.  The G-keys are mapped the same as the F-keys.  The M1-M3 and MR keys do not work either.  
Most of the other features really do work, including the onboard sound.  So far, though, I haven't been able to get the macro keys to work - and that's the main reason I got the keyboard :( I rarely use Windows, and it'll just be an expensive lighted keyboard in Linux until I can get the drivers to work.

So, according to [http://www.g15tools.com/node/193]("http://www.g15tools.com/node/193"), there is a patch for the G110, however, I haven't been able to get it working.

I had tried compiling the G15Tools and G15Daemon (first without the patch), and then I noticed that there were actually packages in the repositories for them.  Unfortunately, installing the g15daemon package gives this error (I tried it on two different computers, one 64-bit [my computer], the other 32-bit - same error on both):
```

Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 g15daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
It appears it can't find uinput... I'm not sure what to do there.  "sudo modprobe uinput" doesn't help.

Nonetheless, even if those packages actually did work, they probably don't have the patch applied.  I tried applying the G110 patch, but I was only partially successful (if anyone knows the proper way to apply that patch, it would help - I'm not very familiar with applying source code patches).
I tried compiling g15daemon anyway, but then got yet another error when I run make :(
```

grep: /usr/lib/libfreetype.la: No such file or directory
/bin/sed: can't read /usr/lib/libfreetype.la: No such file or directory
libtool: link: `/usr/lib/libfreetype.la' is not a valid libtool archive
make[2]: *** [libg15daemon_client.la] Error 1
make[2]: Leaving directory `/home/logan/Downloads/Source/g15daemon-1.9.5.3/libg15daemon_client'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/logan/Downloads/Source/g15daemon-1.9.5.3'
make: *** [all] Error 2

```
It looks like it can't find libfreetype, so I tried installing "libfreetype6" and "libfreetype6-dev", but when dpkg tries to configure those packages, it attempts to start g15daemon again and gets the same error as the first one above.


I sent a customer support request to Logitech.  I highly doubt they'll send back anything useful, but I thought it would be worth a try.  Their support form actually recognizes Linux as an operating system at least :), but I'll probably just get the "Linux is an unsupported operating system blah blah" response.


I noticed G15Tools is still being updated occasionally... I haven't tried the SVN code yet, I probably need to figure out why I can't compile the standard release code first before I try the SVN code.

Anyone out there have any ideas?

EDIT 1: I remember reading a post somewhere earlier today (sorry, can't remember where), that claimed they were able to get the G110 working with the patch in Linux.  So, it must be possible - I'm probably doing something wrong though.

EDIT 2: I found some more information, but still haven't got it working, check out these links:
[https://bugs.launchpad.net/ubuntu/+source/g15daemon/+bug/570245](https://bugs.launchpad.net/ubuntu/+source/g15daemon/+bug/570245)
[https://bugs.launchpad.net/ubuntu/+source/g15daemon/+bug/538259](https://bugs.launchpad.net/ubuntu/+source/g15daemon/+bug/538259)

---

### Post by Recon20k on 2010-06-12
> **dino99 said:**
> not so good news :(

...

[https://help.ubuntu.com/community/LogitechG15](https://help.ubuntu.com/community/LogitechG15)

...

from the website

> 

This content is quite old and may not be applicable to current versions of Ubuntu. If you use 9.04 like I do you will find all packages are in Synaptic package manager, no need to download the source and compile or just do a "sudo apt-get install g15stats"



I get the following error message when running 

sudo apt-get install g15daemon

in the terminal.
I'm on the 64-bit version of ubuntu 10.04.


> 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
g15daemon is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up g15daemon (1.9.5.3-8ubuntu1) ...
Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of g15macro:
 g15macro depends on g15daemon; however:
  Package g15daemon is not configured yet.
dpkg: error processing g15macro (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g15stats:
 g15stats depends on g15daemon; however:
  Package g15daemon is not configured yet.
dpkg: error processing g15stats (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                  Errors were encountered while processing:
 g15daemon
 g15macro
 g15stats
E: Sub-process /usr/bin/dpkg returned an error code (1)



A resolution to this would be great as everytime I try to update ubuntu with update manage I'm always getting errors to do with g15daemon, package failure etc.

---

### Post by JosephBus on 2010-12-21
Hi GammaRay, Just now saw your reply /note:
*Last edited by GammaRay256; June 4th, 2010 at 08:28 PM..*
My Question:
Have you been able to find a way to Install the G110 w/o errors?
I am in same situation & also have not programmed code for
a very long time...
On installing g15daemon, I also got:

E: g15daemon: 
subprocess installed post-installation script returned error exit status 1
E: g15macro: dependency problems - leaving unconfigured
E: g15stats: dependency problems - leaving unconfigured...


If you had any breakthroughs, please give an update...
Thank You, Joseph 12/20/2010
[email]JosephBus@gmail.com[/email]
==================================================
> **GammaRay256 said:**
> I am also in the same situation.  I too have the G110 and am having the same problems.  The G-keys are mapped the same as the F-keys.  The M1-M3 and MR keys do not work either.  
Most of the other features really do work, including the onboard sound.  So far, though, I haven't been able to get the macro keys to work - and that's the main reason I got the keyboard :( I rarely use Windows, and it'll just be an expensive lighted keyboard in Linux until I can get the drivers to work.

So, according to [http://www.g15tools.com/node/193](http://www.g15tools.com/node/193), there is a patch for the G110, however, I haven't been able to get it working.

I had tried compiling the G15Tools and G15Daemon (first without the patch), and then I noticed that there were actually packages in the repositories for them.  Unfortunately, installing the g15daemon package gives this error (I tried it on two different computers, one 64-bit [my computer], the other 32-bit - same error on both):
```

Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 g15daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

```It appears it can't find uinput... I'm not sure what to do there.  "sudo modprobe uinput" doesn't help.

Nonetheless, even if those packages actually did work, they probably don't have the patch applied.  I tried applying the G110 patch, but I was only partially successful (if anyone knows the proper way to apply that patch, it would help - I'm not very familiar with applying source code patches).
I tried compiling g15daemon anyway, but then got yet another error when I run make :(
```

grep: /usr/lib/libfreetype.la: No such file or directory
/bin/sed: can't read /usr/lib/libfreetype.la: No such file or directory
libtool: link: `/usr/lib/libfreetype.la' is not a valid libtool archive
make[2]: *** [libg15daemon_client.la] Error 1
make[2]: Leaving directory `/home/logan/Downloads/Source/g15daemon-1.9.5.3/libg15daemon_client'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/logan/Downloads/Source/g15daemon-1.9.5.3'
make: *** [all] Error 2

```It looks like it can't find libfreetype, so I tried installing "libfreetype6" and "libfreetype6-dev", but when dpkg tries to configure those packages, it attempts to start g15daemon again and gets the same error as the first one above.


I sent a customer support request to Logitech.  I highly doubt they'll send back anything useful, but I thought it would be worth a try.  Their support form actually recognizes Linux as an operating system at least :), but I'll probably just get the "Linux is an unsupported operating system blah blah" response.


I noticed G15Tools is still being updated occasionally... I haven't tried the SVN code yet, I probably need to figure out why I can't compile the standard release code first before I try the SVN code.

Anyone out there have any ideas?

EDIT 1: I remember reading a post somewhere earlier today (sorry, can't remember where), that claimed they were able to get the G110 working with the patch in Linux.  So, it must be possible - I'm probably doing something wrong though.

EDIT 2: I found some more information, but still haven't got it working, check out these links:
[https://bugs.launchpad.net/ubuntu/+source/g15daemon/+bug/570245](https://bugs.launchpad.net/ubuntu/+source/g15daemon/+bug/570245)
[https://bugs.launchpad.net/ubuntu/+source/g15daemon/+bug/538259](https://bugs.launchpad.net/ubuntu/+source/g15daemon/+bug/538259)

---

### Post by crlcan81 on 2011-02-07
I also got a Logitech g110 for what little gaming I do on Windows Xp, a few macros and shortcuts, along with a Razer DeathAdder. Would love to try and get both functioning somehow to at least use the g keys on the keyboard, as well as the DeathAdder's features.

---

### Post by Wild-Storm on 2011-03-08
you need to get the svn repository and compile the binaries yourself. the versions ubuntu provides in apt are outdated.

svn co [https://g15tools.svn.sourceforge.net/svnroot/g15tools](https://g15tools.svn.sourceforge.net/svnroot/g15tools) g15tools

then cd into trunk/libg15 and run ./bootstrap, ./configure, make, checkinstall.
do the same in g15daemon
after doing modprobe uinput
and running g15daemon the G keys weren't mapped to the Fx keys any more but i still didn't figure out, how i could use the macros on the G keys (like on the fly recording)

---

### Post by jobcol on 2011-03-14
Thank you for your instructions Wild-Storm , was able to get this damn keyboard installed  and able to record macros.
For the macros,,do you have g15macro installed as well? u need this program running in order to be able to record/run macros.
Only problem I am having now is figuring out how to insert pauses between keystrokes in a macro.

---

### Post by JosephBus1 on 2011-03-25
Thank You for instructions Wild-Storm...
Got as far as checkinstall , then: 

[B]"The program 'checkinstall' is currently not installed.  You can install it by typing: sudo apt-get install checkinstall
[/B]
~/g15tools/g15tools/trunk/libg15$ sudo apt-get checkinstall
[sudo] password for josephbus1: 

**"E: Invalid operation checkinstall..."**

Using 10.04 LTS...
Any Ideas?
Thx, [email]JosephBus@gmail.com[/email]

---

### Post by jwcalla on 2011-04-04
> **JosephBus1 said:**
> Thank You for instructions Wild-Storm...
Got as far as checkinstall , then: 

[B]"The program 'checkinstall' is currently not installed.  You can install it by typing: sudo apt-get install checkinstall
[/B]
~/g15tools/g15tools/trunk/libg15$ sudo apt-get checkinstall
[sudo] password for josephbus1: 

**"E: Invalid operation checkinstall..."**

Using 10.04 LTS...
Any Ideas?
Thx, [EMAIL="JosephBus@gmail.com"]JosephBus@gmail.com[/EMAIL]

Did you type "sudo apt-get checkinstall" or "sudo apt-get install checkinstall"?

---

### Post by SL666 on 2011-06-08
so...

I had the G-keys giving the same as the F1 keys on my G110, built G15lib and G15daemon from the svn, now the keys don't show up as anything...

any ideas?

---

### Post by jwcalla on 2011-06-08
> **SL666 said:**
> so...

I had the G-keys giving the same as the F1 keys on my G110, built G15lib and G15daemon from the svn, now the keys don't show up as anything...

any ideas?

Yeah I was able to define the G keys with g15daemon using the following instructions:

[https://help.ubuntu.com/community/LogitechG15](https://help.ubuntu.com/community/LogitechG15)

Steps labeled "Adding key symbols to X" and "Binding the keys to the symbols".

You have to use xev to find the right keycodes.  If your keys don't give any keycodes in xev then I'm clueless.

My version of g15daemon had an insane memory leak so I don't use it anymore... but that could have been due to some tinkering I did.

I'm still looking for a better solution for my G110 myself, but haven't put much energy into it for awhile now.

---

### Post by SL666 on 2011-06-08
:( no codes in xev at all. (for G keys)


firing up g15daemon in debug shows it detecting my G110 ok, but no other issues.. might have to reboot to clean the slate a little (i was running a G15 before my wife had a beverage mishap, ps, you can't just rinse them off and dry them out like most keyboards)

---

### Post by jwcalla on 2011-06-08
> **SL666 said:**
> :( no codes in xev at all. (for G keys)


firing up g15daemon in debug shows it detecting my G110 ok, but no other issues.. might have to reboot to clean the slate a little (i was running a G15 before my wife had a beverage mishap, ps, you can't just rinse them off and dry them out like most keyboards)

I forgot to mention that for g15daemon you have to compile from the latest version in sourceforge with some kind of patch for the G110 keyboard.  I think there's like a million versions and libraries in there and they're all in crazy places.  I don't remember exactly, I just remember that I was confused as to what exactly I should be compiling.  I don't know why people working on projects put up a website and then don't tell you what's what and how to go about doing anything.  A little bit of communication (with occasional updates) can go a long way.  Maybe just a text document here and there... nothing fancy.  If you pulled g15daemon out of the repo it's not going to work for the G110.  I can't even find their latest work and patches in sourceforge from their website.  (Actually, I think **[this]("https://g15daemon.svn.sourceforge.net/svnroot/g15daemon/trunk/g15daemon-wip/")** is the package you'd want to checkout from svn, using:  svn co [https://.](https://.).. g15daemon)

I wouldn't waste time with the g15daemon thing though.  It seems like a disaster and pretty hacky and not really going anywhere.

I also forgot to mention that there is a **[kernel module]("https://github.com/martynsmith/lg4l")** available if you'd like to try compiling that.  However, that gives me F-key values for my G-keys so that's probably not going to help you.  This driver probably holds the most promise though.

---

### Post by SL666 on 2011-06-08
I compiled the latest version of that code (eventually, nothing like having to check the errors to see what else needs to be installed).

I had the G-keys throwing the F-keys to start with.. so i might go back to that frankly - and try to re-map those suckers.

---

### Post by JosephBus1 on 2011-07-07
[B]QUOTE=Wild-Storm;10536505]you need to get the svn repository and compile the binaries yourself. the versions ubuntu provides in apt are outdated.

svn co  [https://g15tools.svn.sourceforge.net/svnroot/g15tools](https://g15tools.svn.sourceforge.net/svnroot/g15tools) g15tools

then cd into trunk/libg15 and run ./bootstrap, ./configure, make, checkinstall. 
do the same in g15daemon
after doing modprobe uinput
and running g15daemon the G keys weren't mapped to the Fx keys any more but i still didn't figure out, how i could use the macros on the G keys (like on the fly recording)[/QUOTE]
==================================================
Thanks for your message, Wild Storm...

I'm in Lucid,  Got through your commands  up to   ./configure  ... 

./configure      had error:                 E: Couldn't find package libusb
=======================================
The command  sudo apt-get install libusb    results in:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libusb
====================================
Synaptic says libusb-1.0-0 is installed, I re-installed but still the /.configure fails as above...
====================================

Any ideas?  Thx, JosephBus1

[/B]

---

### Post by JosephBus1 on 2011-07-23
Thanks, Wild Storm . You said:
 ================================
                                  **Re: Logitech G110**             
                                                                you need to get the svn repository and compile the binaries yourself. the versions ubuntu provides in apt are outdated.

svn co [https://g15tools.svn.sourceforge.net/svnroot/g15tools](https://g15tools.svn.sourceforge.net/svnroot/g15tools) g15tools

then cd into trunk/libg15 and run ./bootstrap, ./configure, make, checkinstall.
do the same in g15daemon
after doing modprobe uinput
and running g15daemon the G keys weren't mapped to the Fx keys any more  but i still didn't figure out, how i could use the macros on the G keys  (like on the fly recording)
                                                                                                  
       
========================================
I'm in Lucid with:
jg@jg-dsktp:~/g15tools/trunk/libg15$ ./bootstrap && ./configure && ./make
+ aclocal -I config
+ libtoolize --force --copy
./bootstrap: 1: libtoolize: not found
+ autoheader
+ automake --add-missing --copy
configure.in:8: installing `config/config.guess'
configure.in:8: installing `config/config.sub'
configure.in:10: installing `config/install-sh'
configure.in:10: installing `config/missing'
Makefile.am:2: Libtool library used but `LIBTOOL' is undefined
Makefile.am:2:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
Makefile.am:2:   to `configure.in' and run `aclocal' and `autoconf' again.
Makefile.am:2:   If `AC_PROG_LIBTOOL' is in `configure.in', make sure
Makefile.am:2:   its definition is in aclocal's search path.
Makefile.am: installing `config/depcomp'
+ autoconf
configure.in:16: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
jg@jg-dsktp:~/g15tools/trunk/libg15$ cd ../g15daemon
jg@jg-dsktp:~/g15tools/trunk/g15daemon$ cd ../libg15
jg@jg-dsktp:~/g15tools/trunk/libg15$ checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: Y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> Default Set of package docs
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ jg@jg-dsktp ]
1 -  Summary: [ Default Set of package docs ]
2 -  Name:    [ libg15 ]
3 -  Version: [ 20110723 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ libg15 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ libg15 ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make...Installing with install...

====== Installation results ===========================
make: *** No rule to make target `install'.  Stop.
****  Installation failed. Aborting package creation.
Cleaning up...OK
Bye.
 ===========================================


                                                                [URL="http://ubuntuforums.org/newreply.php?do=newreply&p=10536505"]
[/URL]Appreciate any ideas...JosephBus1:(  :guitar:  :(

---

### Post by sweener on 2011-08-14
> **JosephBus1 said:**
> Thanks, Wild Storm . You said:
 ================================
                                  **Re: Logitech G110**             
                                                                you need to get the svn repository and compile the binaries yourself. the versions ubuntu provides in apt are outdated.

svn co [https://g15tools.svn.sourceforge.net/svnroot/g15tools](https://g15tools.svn.sourceforge.net/svnroot/g15tools) g15tools

then cd into trunk/libg15 and run ./bootstrap, ./configure, make, checkinstall.
do the same in g15daemon
after doing modprobe uinput
and running g15daemon the G keys weren't mapped to the Fx keys any more  but i still didn't figure out, how i could use the macros on the G keys  (like on the fly recording)
                                                                                                  
       
========================================
I'm in Lucid with:
jg@jg-dsktp:~/g15tools/trunk/libg15$ ./bootstrap && ./configure && ./make
+ aclocal -I config
+ libtoolize --force --copy
./bootstrap: 1: libtoolize: not found
+ autoheader
+ automake --add-missing --copy
configure.in:8: installing `config/config.guess'
configure.in:8: installing `config/config.sub'
configure.in:10: installing `config/install-sh'
configure.in:10: installing `config/missing'
Makefile.am:2: Libtool library used but `LIBTOOL' is undefined
Makefile.am:2:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
Makefile.am:2:   to `configure.in' and run `aclocal' and `autoconf' again.
Makefile.am:2:   If `AC_PROG_LIBTOOL' is in `configure.in', make sure
Makefile.am:2:   its definition is in aclocal's search path.
Makefile.am: installing `config/depcomp'
+ autoconf
configure.in:16: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
jg@jg-dsktp:~/g15tools/trunk/libg15$ cd ../g15daemon
jg@jg-dsktp:~/g15tools/trunk/g15daemon$ cd ../libg15
jg@jg-dsktp:~/g15tools/trunk/libg15$ checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: Y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> Default Set of package docs
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ jg@jg-dsktp ]
1 -  Summary: [ Default Set of package docs ]
2 -  Name:    [ libg15 ]
3 -  Version: [ 20110723 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ libg15 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ libg15 ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make...Installing with install...

====== Installation results ===========================
make: *** No rule to make target `install'.  Stop.
****  Installation failed. Aborting package creation.
Cleaning up...OK
Bye.
 ===========================================


                                                                [URL="http://ubuntuforums.org/newreply.php?do=newreply&p=10536505"]
[/URL]Appreciate any ideas...JosephBus1:(  :guitar:  :(

You need to install libtool.

sudo apt-get libtool

---

### Post by mroughan on 2011-08-15
> **JosephBus1 said:**
> [B]QUOTE=Wild-Storm;10536505]you need to get the svn repository and compile the binaries yourself. the versions ubuntu provides in apt are outdated.

svn co  [https://g15tools.svn.sourceforge.net/svnroot/g15tools](https://g15tools.svn.sourceforge.net/svnroot/g15tools) g15tools

then cd into trunk/libg15 and run ./bootstrap, ./configure, make, checkinstall. 
do the same in g15daemon
after doing modprobe uinput
and running g15daemon the G keys weren't mapped to the Fx keys any more but i still didn't figure out, how i could use the macros on the G keys (like on the fly recording)[/B][B]
==================================================
Thanks for your message, Wild Storm...

I'm in Lucid,  Got through your commands  up to   ./configure  ... 

./configure      had error:                 E: Couldn't find package libusb
=======================================
The command  sudo apt-get install libusb    results in:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libusb
====================================
Synaptic says libusb-1.0-0 is installed, I re-installed but still the /.configure fails as above...
====================================

Any ideas?  Thx, JosephBus1

[/B][/QUOTE]

I found that install libusb-dev fixed that -- I guess then it can get the headers. I haven't tested the results yet, but at least I can compile now.

---

### Post by JosephBus1 on 2011-08-25
[B][SIZE=2]> **Wild-Storm said:**
> you need to get the svn repository and compile the binaries yourself. the versions ubuntu provides in apt are outdated.

svn co [https://g15tools.svn.sourceforge.net/svnroot/g15tools](https://g15tools.svn.sourceforge.net/svnroot/g15tools) g15tools

then cd into trunk/libg15 and run ./bootstrap, ./configure, make, checkinstall.
do the same in g15daemon
after doing modprobe uinput
and running g15daemon the G keys weren't mapped to the Fx keys any more but i still didn't figure out, how i could use the macros on the G keys (like on the fly recording)
$
$[/SIZE][/B]**[SIZE=2][COLOR=#000000]Restart AGAIN...[/COLOR][/SIZE]**[B][SIZE=2][COLOR=#000000]
$Complete Removal: g15 & 	g15tools pkgs[/COLOR][/SIZE][/B] 	**[SIZE=2][COLOR=#000000]$In Root Terminal, per 	Wild-Storm Instructions,[/COLOR][/SIZE]**  [B][SIZE=2][COLOR=#000000]svn co [https://g15tools.svn.sourceforge.net/svnroot/g15tools](https://g15tools.svn.sourceforge.net/svnroot/g15tools) g15tools

$cd into trunk/libg15 and ran ./bootstrap, ./configure, make, checkinstall.[/COLOR][/SIZE][/B]
 **[SIZE=2][COLOR=#000000]$ Installation of libg15 successful but [/COLOR][/SIZE]** 
 **[SIZE=2][COLOR=#000000]$ checkinstall insisted on a doc dir...even though I declined one...[/COLOR][/SIZE]**
 **[SIZE=2][COLOR=#000000]$ An attempt was made to build a Debian pkg for the doc dir & failed...[/COLOR][/SIZE]**
 [B][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/B]
[B][SIZE=2][COLOR=#000000]modprobe uinput 
[/COLOR][/SIZE][/B]
[B][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/B] 
 [B][SIZE=2][COLOR=#000000]$ Now for g15daemon,
cd g15tools/trunk/g15daemon[/COLOR][/SIZE][/B]
 **[SIZE=2][COLOR=#000000]./bootstrap    [/COLOR][/SIZE]** 
 **[SIZE=2][COLOR=#000000]bash: ./bootstrap: No such file or directory             $ is a bootstrap necessary here?[/COLOR][/SIZE]**
 **[SIZE=2][COLOR=#000000]./configure [/COLOR][/SIZE]**
 **[SIZE=2][COLOR=#000000]bash: ./configure: No such file or directory [/COLOR][/SIZE]**
 **[SIZE=2][COLOR=#000000]autoconf                                                 $ my attempt to build a valid 'configure' file[/COLOR][/SIZE]**
 **[SIZE=2][COLOR=#000000]configure.in:11: error: possibly undefined macro: AM_INIT_AUTOMAKE [/COLOR][/SIZE]**
 **[SIZE=2][COLOR=#000000]      If this token and others are legitimate, please use m4_pattern_allow. [/COLOR][/SIZE]**
 **[SIZE=2][COLOR=#000000]      See the Autoconf documentation. [/COLOR][/SIZE]**
 **[SIZE=2][COLOR=#000000]configure.in:16: error: possibly undefined macro: AC_PROG_LIBTOOL [/COLOR][/SIZE]**
 **[SIZE=2][COLOR=#000000]configure.in:60: error: possibly undefined macro: AM_CONDITIONAL [/COLOR][/SIZE]**
 **[SIZE=2][COLOR=#000000]./configure [/COLOR][/SIZE]**
 **[SIZE=2][COLOR=#000000]configure: error: cannot find install-sh, install.sh, or shtool in config "."/config [/COLOR][/SIZE]**
 **[SIZE=2][COLOR=#000000]===My  8/24/11 attempt======================[/COLOR][/SIZE]** 	[B][SIZE=2]Thanks to anyone knowledgeable who takes the time...:confused:
[/SIZE][/B] 	[B][SIZE=2]
[/SIZE][/B]

---

### Post by rocketman221 on 2011-09-09
jobcol,  how did you get it working? I have been working on it for 3 hours and nothing works. I followed Wild-Storms instructions and it unmapped the g keys from the f keys, but I still can't record any macros.

---

### Post by xxx-sm on 2011-11-06
Hello, 

  	 	 	 	 	 	  I've read your instructions but I can't execute the ./bootstrap command.  
 I get this error message:  
 ```

+ aclocal -I config
./bootstrap: 1: aclocal: not found
+ libtoolize --force --copy
./bootstrap: 1: libtoolize: not found
+ autoheader
./bootstrap: 1: autoheader: not found
+ automake --add-missing --copy
./bootstrap: 1: automake: not found
+ autoconf
./bootstrap: 1: autoconf: not found

``` 
 

 What is missing?

---

### Post by jcllings on 2012-05-05
> **xxx-sm said:**
> Hello, 

  	 	 	 	 	 	  I've read your instructions but I can't execute the ./bootstrap command.  
 I get this error message:  
 ```

+ aclocal -I config
./bootstrap: 1: aclocal: not found
+ libtoolize --force --copy
./bootstrap: 1: libtoolize: not found
+ autoheader
./bootstrap: 1: autoheader: not found
+ automake --add-missing --copy
./bootstrap: 1: automake: not found
+ autoconf
./bootstrap: 1: autoconf: not found

``` 
 

 What is missing?

Ya, these messages aren't very helpful. IMHO, they should say something like, "automake: Required but not found. Please install." 
OR even better: 
"automake: Required but not found. Do you wish to install? (Y/N): " 
OR perhaps something like:

"automake: Required but not found. Install with this command and then try again: sudo apt-get install automake"

...of course most helpful of all would be if someone just copied the packages and then fixed the dependencies on the source code. Then it would be fixed and available to everyone  automagically through a regular system update. Assuming of course, that I'm not wrong about what the problem is.

---

### Post by Toast2120 on 2012-05-09
***_[COLOR="Red"]WARNING[/COLOR]_***: discovered that doing something with the installs listed below with a G110 keyboard will freeze your grub screen with any button press on the G110. I tried booting to Windows to find that the Grub would freeze and the issue is the keyboard. Didn't notice as I usually just let grub time out into Ubuntu. Now booting with alternate keyboard. Haven't figured out the issue yet, despite removing the files I installed. Something was changed somewhere. Continue at you own risk!!!!!



Going to continue this topic with how far I've gotten because it seems like this is not entirely resolved for all users. Think I made some progress.

Following the doc here

[https://help.ubuntu.com/community/LogitechG15](https://help.ubuntu.com/community/LogitechG15)

I have installed all reccomended G15 dependencies found by running

sudo apt-cache search g15

After running the installation the gdaemon15 attempts to start and fails with the output

```
dpkg: error processing g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of g15macro:
 g15macro depends on g15daemon; however:
  Package g15daemon is not configured yet.
dpkg: error processing g15macro (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 g15daemon
 g15macro
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

However if you manually attempt to start the server by

```
/etc/init.d/g15daemon start
```

The server starts just fine and appears in a ```
service --status-all
``` output

So I went back and typed the advised

```
g15daemon --configure
```

with no error. However when I try to 

```

*****@*****:~/Downloads/libg15-1.2.7$ g15macro --configure
Sorry, cant connect to the G15daemon - retrying
Sorry, cant connect to the G15daemon - retrying
```

I get the idea that something isn't linked correctly, though I have no idea of what file to check.

---

### Post by Anthony1s on 2012-06-15
Hello,

Is anyone able to verify working programmable G keys and memory buttons for the G110?

I was following Wild-Storm's directions. Had to install automake and libtool to get ./bootstrap to work. After ./bootstrap, I ran ./configure, make, make install. Everything went fine, my G keys are no longer F keys, but I don't know how to assign or map the G keys. So they do nothing right now.

The guy above mentioned Grub problems when dual booting. I run Chameleon with 32bit 11.10, OXS Lion, and Win7 64bit. Chameleon launches Grub to launch Ubuntu. I'll reboot now and see if I have any problems and let everyone know.

Update: I messed around in Grub by pressing the arrows and return keys, everything still works as normal. Booting to OSX and Win7 with Chameleon are fine too. I only ran bootstrap and make from /trunk/libg15, I didn't do anything with g15daemon or modprobe uinput so maybe that's where his problem lies.

---

### Post by AI8W on 2013-01-15
> **GammaRay256 said:**
> 
I had tried compiling the G15Tools and G15Daemon (first without the patch), and then I noticed that there were actually packages in the repositories for them.  Unfortunately, installing the g15daemon package gives this error (I tried it on two different computers, one 64-bit [my computer], the other 32-bit - same error on both):
```

Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 g15daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

```It appears it can't find uinput... I'm not sure what to do there.  "sudo modprobe uinput" doesn't help.


Just curious why noone ever thought to do a simple
```
 sudo ln -s /dev/uinput /dev/input/uinput 
```to get it to work?

---

### Post by icebuntu on 2013-02-12
Anybody had any luck in making this keyboard to work?

I tried various build of g15daemon from svn but I only got as far as to stop making G keys from working as F keys, but after that they don't return any more codes.

---

### Post by JosephBus1 on 2013-02-19
[B]Re: Logitech , the Company...They disabled my acct & said I would have to buy another Logitech product before they would either cancel the acct ( so that I could create a new one ), or re-enable my original one!  So naturally, that is my last time I care to contact them. It's clear they are owned by Microsoft...

Re: the G110 KB, for whatever this is worth, I since bought a new desktop, win7 64-bit installed, with G110 Logitech s/w working OK... 

With Win7 as host, VMWare Player, & Linux Mint as guest, the Fn keys are working OK as seen from guest Linux  Mint...So far I'm now a happy camper...

In general, I'm hoping someone can report a "HowTo implement simple Linux KB macros for the G110" ...The usage would be to generate a character string for each Fn key. I would appreciate anyone posting here for that info...

Thanks,   JosephBus1   
[/B]

---

### Post by icebuntu on 2013-02-20
> **JosephBus1 said:**
> [B]
In general, I'm hoping someone can report a "HowTo implement simple Linux KB macros for the G110" ...The usage would be to generate a character string for each Fn key. I would appreciate anyone posting here for that info...

Thanks,   JosephBus1   
[/B]

That's the functionality I'm looking for, using the macro keys to run custom strings. If I can actually use M1-3 x FNkeys is even better. Changing color with changing M1-3 is even even better :)

---

### Post by russo on 2013-06-29
Hello

You should give a look at Gnome15 software ([http://www.russo79.com/gnome15](http://www.russo79.com/gnome15)).
It provides a suite of tools that allow you to program your G-Keys and to create macro-profiles that you can automatically activate according to the running application.

Note: I currently maintain this software and don't own a G110, so your mileage may vary a bit.

---

### Post by JosephBus1 on 2013-10-06
Hi Russo, Thx 4 Ur help last Month w/ G110 Macros...I've been away...Here is my situation...
I'm in Mint Olivia...

1) KB driver disconnected @ Logon
2) Logitect [COLOR=#ff0000]**G**[/COLOR] KB ( systray icon ) Configuration Properties - KB driver disconnected 
KB Tab  - Cycle screens not selected
Macros Tab - default is OK
Plugins Tab - G15 Daemon Compatibility, "Starts a Network server...
         If U R using a real g15daemon server, U will config this plugin to a different port"
Driver Tab - G15 Direct;  I set timeout to 0 ms...Not sure purpose of Timeout...

On upgrading Pkgs -
 sudo sh -c "echo deb [http://packages.russo79.com/debian/gnome15](http://packages.russo79.com/debian/gnome15) raring main > /etc/apt/sources.list.d/gnome15.list"
sudo apt-get update
results in:
W: Failed to fetch [http://www.gnome15.org/olivia/./Packages](http://www.gnome15.org/olivia/./Packages)  404  Not Found
I've noted that others experience this "fail to fetch" also...Thx 4 Ur Help, JosephBus1

---

