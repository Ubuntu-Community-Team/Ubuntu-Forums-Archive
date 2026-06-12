---
title: "AMD Catalyst 14.6 Beta Driver in Ubuntu 12.04"
date: 2014-09-18
forum: Hardware
---

### Post by crazybear on 2014-09-18
Help! Having multi-problems. Have been through no boot; booting into tty1 terminal only; now two out of three monitors working and the two working ones are not a desktop, but clones. Seem not to be able to install the new drivers. Getting many error messages that I don't understand. Also, on the internet I found 3 [!] slightly different instructions on how to install these...and don't know which to trust. Can't tell what is currently installed along the lines of CCC, if any and am having very hard time using the computer. Also get a message of it being in low graphics mode and don't know how to get out of this. They well could be related. Someone please help me know how to install the new drivers. I recently upgrated the VGA card and it needs these new drivers and they are supposed to work in both 12.04.4 and 14.04. I have 12.04.4
Here are some of the recent error messages:
   ~/Downloads/fglrx-14.20$ sudo chmod +x amd-driver-installer*.run 
 [sudo] password for peter-and-crazybear:  
 xxxxxxxxxxx:~/Downloads/fglrx-14.20$ sudo sh *.run --buildpkg Ubuntu/precise 
 Created directory fglrx-install.odjBLu 
 Verifying archive integrity... All good. 
 Uncompressing AMD Catalyst(TM) Proprietary Driver-14.20........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................ 
 ===================================================================== 
  AMD Catalyst(TM) Proprietary Driver Installer/Packager  
 ===================================================================== 
 Generating package: Ubuntu/precise 
 Resolving build dependencies... 
 Continuing package build 
 Package build failed! 
 Package build utility output: 
 Cleaning in directory . 
 Can't exec "debian/rules": Permission denied at /usr/bin/debuild line 1327. 
 debuild: fatal error at line 1326: 
 couldn't exec debian/rules: Permission denied 
 dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security 
 dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2 
 dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security 
 dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2 
 dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro 
 dpkg-buildpackage: source package fglrx-installer 
 dpkg-buildpackage: source version 2:14.200-0ubuntu1 
 dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html> 
  dpkg-source --before-build fglrx.uUWjka 
 dpkg-buildpackage: host architecture amd64 
  debian/rules build 
 Can't exec "debian/rules": Permission denied at /usr/bin/dpkg-buildpackage line 529. 
 dpkg-buildpackage: error: debian/rules build failed with unknown exit code -1 
 Removing temporary directory: fglrx-install.odjBLu 
 xxxxxxxx:~/Downloads/fglrx-14.20$

---

### Post by maxinstuff2 on 2014-09-18
The first time I tried to generate the packages it failed and in the log it listed what to install in what order.

Maybe look in the folder to see if such a log was generated?
```
cd ~/Downloads/fglrx-14.20
ls
```

---

### Post by crazybear on 2014-09-19
> **maxinstuff2 said:**
> The first time I tried to generate the packages it failed and in the log it listed what to install in what order.

Maybe look in the folder to see if such a log was generated?
```
cd ~/Downloads/fglrx-14.20
ls
```

Thanks, I'll look...but my problems have been greatly compounded since I wrote that... Then I had two screens [mirrored] I could use. Now I have only the tty1 terminal, and can not boot into Ubuntu. I've gotten many error messages and all are upsetting. There were so many, I didn't write them all down. I tried using a different recipe on the internet to re-install the HWE hardware update [which may or may not be causing parts of the problem - it certainly was even before I changed the VGA card!. I also got a strange warning that no monitors were detected...when three are connected and working - and were before in the original set up. So, I fear the xorg config file [?] or similar are also no good now. I'm really at a loss as to what to do first and how to attempt this. I'm using a cloned disk. The other, which I won't touch until I get this figured out - if I do - only has one level of problems. The current disk has several now....as I admit to not  knowing exactly what I'm doing and how to proceed. Before the change in the VGA card, I had to use a lower kernel than the new one [which had the HWE update], as the whole visual appearance and speed of Ubuntu had greatly degraded - rather than improved. Using the older kernel, things were normal. Now, it doesn't matter and I don't even know if I should first go into the new or old [I guess new...but?????] kernel and try to repair things. 

Anyway, I'll look in the folder and see if a log was generated...likely a few...as I tried to re-install a few times...all with various error messages that were not specific enough [to me] to know what to do next....and I'll report back. Would someone tell me what file records how many monitors are to be in the configuration and how to go about amending it if it doesn't mention any of the three I have attached to the VGA card. They work fine in Windoz, but I hate Windoz...and it has none of my important files nor programs.

---

### Post by crazybear on 2014-09-19
I see no log file, but then I'm not sure and not good at navigation 'blind' using only a terminal. there seemed to be 'doc' in that folder, but try as I might I didn't know how to read it. I tried again a few things and noted the error messages. The driver install starts to go well...then it stops with 'permission denied at line 529' and then it deletes the temp file and I'm back to where I started...only I'm actually further back then when I started......but I digress. I also had in the past [not now in tty1 terminal] gotten a message screen saying I was in 'low graphics mode'. Any suggestions for a next step. The driver is unpacked and sitting there, but I can't get it to do anything....and can't actually start Ubuntu....only have the tty1 terminal. I'm exhausted, having just typed and typed for an hour....pppffft!

---

### Post by crazybear on 2014-09-19
OK, making slow progress...but no time to celebrate. I got back into Ubuntu after a days research and endless false steps and attempts. However, I have three monitors mirrored and can't seem to find a way to get them to be one desktop, as before. Also, I'm quite sure if I try to build the new 14.20 driver, the same series of events will befall me. Oh, and no, there was no error report other than that I posted above during one attempt of many. Anyone have any ideas. Best I can figure out, my Radeon HD 7970 needs the newer Catalyst drivers for Linux and they should work on my 12.4.5 [in theory].

---

### Post by crazybear on 2014-09-19
OK, making slow progress...but no time to celebrate. I got back into Ubuntu after a days research and endless false steps and attempts. However, I have three monitors mirrored and can't seem to find a way to get them to be one desktop, as before. Also, I'm quite sure if I try to build the new 14.20 driver, the same series of events will befall me. Oh, and no, there was no error report other than that I posted above during one attempt of many. Anyone have any ideas. Best I can figure out, my Radeon HD 7970 needs the newer Catalyst drivers for Linux and they should work on my 12.4.5 [in theory].

Addendum......just edited xorg.conf [I think] via commands for aticonfig I found online - and it seems to be working....with but one problem...which I had before I changed the VGA card. This has to do with the slowness of anything graphic [windows move slooooowly and with tearing, etc.], I believe due to the new HWE 'update' [or downgrade?]. Questions: How can I repair the slow response to anything graphic with this new HWE 12.04.5 and [2] would things be better with the Catalyst 14.6 Beta Driver - and if so, how in the world do I get it installed - as I've tried over and over and get errors and it never works and I get lost in the tty world [which at least I now know how to get out of, I think...]?! Any ideas, suggestions, fixes appreciated.

---

### Post by crazybear on 2014-09-20
I seem to be having a conversation with myself here. Has no one else had this or a similar problem? The HWE problem is outlined here [http://www.wilderssecurity.com/threads/ubuntu-12-04-4-hardware-updates-to-12-04-5-hwe-problem.366108/](http://www.wilderssecurity.com/threads/ubuntu-12-04-4-hardware-updates-to-12-04-5-hwe-problem.366108/) 
However, I didn't find any answers there that solved my problem. I'm currently using the standard AMD Catalyst driver, but am told and see on the internet on both Linux and AMD sites, I should be using the newer Beta 14.6 driver - but am unable to install it without errors and my computer crashing - needing several hours work to get it back [the first time was several days...]. I don't know if  the problems are related or two separate problems. Oddly, before the new video card, things were slow on visuals [with tearing and other such artifacts] in the new kernels. I noticed this morning that now it is slow on all kernels.....so not making great progress...only have recovered my ability to look at ubuntu. Using Windoz holding my nose this VGA card is fast and gives perfect visuals. With Ubuntu it is not yet doing so - in fact is worse now than the older card before. What to do? Thanks for any ideas.

---

### Post by crazybear on 2014-09-21
Seems there IS a BIG problem, and I'm surprised I seem to be the only one effected or talking about it. Look here: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1355041](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1355041)
**fglrx dependencies had conflicts in 12.04.5(kernel 3.13)**

and here:                                                   [B]Proprietary driver does not available for AMD graphic cards on 12.04.5 
[SIZE=2][https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1352843](https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1352843) 
[although I experience more problems than reported here].[/SIZE][/B]

Now, short of the bug being fixed [whenever that will be....] is there a work around? I can't find it yet. Thanks.

---

### Post by QIII on 2014-09-21
Hello!

I'm a bit bleary-eyed as it is pretty late here and may have just completely missed it, but I don't see anywhere in the thread or the bug report if this issue occurs when just using the .run file directly or if it only occurs when trying to build a package from it.

Have you tried just running it raw?  (There are some drawbacks, like having to uninstall it before allowing kernel upgrades and reinstalling after -- since dpkg is not used).

If that doesn't work, a "work around" (possibly an undesirable one) might be to upgrade to 14.04.1 and see if the issue persists.

---

### Post by crazybear on 2014-09-21
Long list of HWE problem posts on internet here [https://startpage.com/do/search?query=problems+with+HWE+12.04.5&cat=web&pl=chrome&language=english](https://startpage.com/do/search?query=problems+with+HWE+12.04.5&cat=web&pl=chrome&language=english)

---

### Post by crazybear on 2014-09-21
> **QIII said:**
> Hello!

I'm a bit bleary-eyed as it is pretty late here and may have just completely missed it, but I don't see anywhere in the thread or the bug report if this issue occurs when just using the .run file directly or if it only occurs when trying to build a package from it.

Have you tried just running it raw?  (There are some drawbacks, like having to uninstall it before allowing kernel upgrades and reinstalling after -- since dpkg is not used).

If that doesn't work, a "work around" (possibly an undesirable one) might be to upgrade to 14.04.1 and see if the issue persists.

I so NOT understand some of your post. I have tried two ways to install driver - sh and run. I'm not sure what you mean by build a package from it, but it is likely beyond my abilities. I also don't know what 'running it raw' means - I think that may mean the two ways I ran it [?]. I have tried REPEATEDLY upgrading to 14.04 and all attempts ended in complete failure - an unusable disk. I'm staying where I am for now. The AMD site states that is will work on both Ubuntu 12.04 and 14.04 with some caveats about what must be installed and 'on'. The only one I didn't understand was POSIX shared memory is required [for 3D applications]. Thanks for the reply, but not sure we are speaking at same level [me likely a lot less saavy on Ubuntu and Linux]. I just ran it again the two ways. One does nothing. The other gives the same error log [with no missing dependencies mentioned]. By the way, I can't find a way to open it to look at line 1326/7.

[COLOR=#0000cd]NOTE: If your system has logged the missing packages required for installation, install them in the order as per the log file to resolve package-dependency issues.[/COLOR]
[COLOR=#0000cd]Package build failed![/COLOR]
[COLOR=#0000cd]Package build utility output:[/COLOR]
[COLOR=#0000cd]Cleaning in directory .[/COLOR]
[COLOR=#0000cd]Can't exec "debian/rules": Permission denied at /usr/bin/debuild line 1327.[/COLOR]
[COLOR=#0000cd]debuild: fatal error at line 1326:[/COLOR]
[COLOR=#0000cd]couldn't exec debian/rules: Permission denied[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: source package fglrx-installer[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: source version 2:14.200-0ubuntu1[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>[/COLOR]
[COLOR=#0000cd] dpkg-source --before-build fglrx.BAdg4j[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: host architecture amd64[/COLOR]
[COLOR=#0000cd] debian/rules build[/COLOR]
[COLOR=#0000cd]Can't exec "debian/rules": Permission denied at /usr/bin/dpkg-buildpackage line 529.[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: error: debian/rules build failed with unknown exit code -1[/COLOR]
[COLOR=#0000cd]Cleaning in directory .[/COLOR]
[COLOR=#0000cd]Can't exec "debian/rules": Permission denied at /usr/bin/debuild line 1327.[/COLOR]
[COLOR=#0000cd]debuild: fatal error at line 1326:[/COLOR]
[COLOR=#0000cd]couldn't exec debian/rules: Permission denied[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: source package fglrx-installer[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: source version 2:14.200-0ubuntu1[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>[/COLOR]
[COLOR=#0000cd] dpkg-source --before-build fglrx.B70rtx[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: host architecture amd64[/COLOR]
[COLOR=#0000cd] debian/rules build[/COLOR]
[COLOR=#0000cd]Can't exec "debian/rules": Permission denied at /usr/bin/dpkg-buildpackage line 529.[/COLOR]
[COLOR=#0000cd]dpkg-buildpackage: error: debian/rules build failed with unknown exit code -1[/COLOR]
[COLOR=#0000cd][Error] Generate Package - error generating package : Ubuntu/precise[/COLOR]

---

### Post by crazybear on 2014-09-21
The first 'offending' line of the install script when I open it is in ancient Egyptian, and 'says': _\ECK\DFoF\DA\D0\993\CEV\C6\F7c&#14037;\D6\C3\FD\E6\8C/\97a\BE\D9\FDs\D2\EE\FF\B7\F8~\BE\8F\95e8,L\9B\A6e\E6\8C\D3t$\8D~\88\D7RM\FC\D6\F0\8C9\FE\A0\A7=p\B5x\9D\8C\A6\D2E\962Jn\97\E4\C9\D3\FC\E8\BBL\D0Q\F7\E58(\BA\854&#1576;\E7\96
....but nowhere yet do I know what programs or dependencies are needed; why it won't install.....

---

### Post by crazybear on 2014-09-25
Have made no progress....everything very slow in Ubuntu 12.04.5 with my old fglrx driver and new vga card [best I can figure]. I wonder if [this bug]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1355041") is related to the one I'm having installing the new drivers? Really could use some ideas.....

---

### Post by andrew102 on 2014-09-25
Hi Everyone - I don't think an upgrade to 14.04 will help you.

I tried three times to get the AMD 14.6 beta driver to work and it always booted to a black screen.

There are several things you need to check before you even get started:

1. You might get message about a log file: check it /usr/share/ati/fglrx-install.log (this is usually about unmet dependencies)
2. There is a bug in one of the .sh scripts can't remember where but it generated by the installer do a vi search  :%s/[[


Then it still won't work.

---

### Post by crazybear on 2014-09-29
Well, things have developed, but not always in a good way. I finally figured out how to upgrade to 14.04 [yes, for me too it led to a blank screen....but after a few days work got past that]. In 14.04 this driver installed with NO problems and is a wonderful driver for my VGA card! I'm having other huge issues in 14.04, however, so still trying to get this installed in 12.04, from which I write this now. 14.04 was working yesterday; today there are NO panels, so can't select any programs. I think for me and many 14.04 only works with a clean install [for me that would mean taking a week from my intense work to get it back to looking something like what I have now in 12.04 - but the driver I'm using in 12.04 is driving me crazy - everything from moving a window to typing is glacially slow - as if I didn't have the fastest processor and one of the fastest vga cards. Here is the install log from 12. 04 - which makes NO sense to me, I hope it does to someone else!

NOTE: If your system has logged the missing packages required for installation, install them in the order as per the log file to resolve package-dependency issues.
Package build failed!
Package build utility output:
Cleaning in directory .
Can't exec "debian/rules": Permission denied at /usr/bin/debuild line 1327.
debuild: fatal error at line 1326:
couldn't exec debian/rules: Permission denied
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:14.200-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.BAdg4j
dpkg-buildpackage: host architecture amd64
 debian/rules build
Can't exec "debian/rules": Permission denied at /usr/bin/dpkg-buildpackage line 529.
dpkg-buildpackage: error: debian/rules build failed with unknown exit code -1
Cleaning in directory .
Can't exec "debian/rules": Permission denied at /usr/bin/debuild line 1327.
debuild: fatal error at line 1326:
couldn't exec debian/rules: Permission denied
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:14.200-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.B70rtx
dpkg-buildpackage: host architecture amd64
 debian/rules build
Can't exec "debian/rules": Permission denied at /usr/bin/dpkg-buildpackage line 529.
dpkg-buildpackage: error: debian/rules build failed with unknown exit code -1
[Error] Generate Package - error generating package : Ubuntu/precise

---

### Post by crazybear on 2014-09-29
OK...finally...I got the new AMD Catalyst Beta driver installed on 12.04.5! It was NOT easy and I'm not exactly sure what finally did 'the trick'. I can tell you I went over and over trying to install all the listed dependencies [some are NOT listed in synaptic nor are they available as written!!! - beware. I think -but am far from sure- that the key is to make sure that POSIX Shared Memory is enabled...I had to look up the command for that. Then it built the driver and is working so far without problems - and without the SLOWness that the other drivers were creating. Things seem to be OK now....fingers crossed - as I've only had an hour or two with it.

---

