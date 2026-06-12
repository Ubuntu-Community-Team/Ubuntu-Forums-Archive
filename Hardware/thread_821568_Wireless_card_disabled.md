---
title: "Wireless card disabled?"
date: 2008-06-07
forum: Hardware
---

### Post by Spunkbubble on 2008-06-07
Hi, I'm new to the whole linux experience, but looks really good. I have a higher spec PC running Vista (yeah rubbish I know) and Ubuntu 7.10 on another older PC.

Anyway, I have a Belkin 802.11g 54mbps network card, and am trying to use it to set up an internet connection, which will be vital for me if I'll be sticking with Ubuntu. I've done some checks, spent hours browsing tutorials and the like, and I think I've narrowed down the problem.

The system recognises the card, apparently the drivers are fine, I've tweaked my wireless settings for manual connection, but when I look at the information for the card, it's listed as disabled. I haven't done anything as far as I know to disable it, so is this a default setting? From what I gather it's hard if not impossible to enable it... or is this just talk? If there's a way to enable it, then I'm all ears since I think that's the problem, but bear in mind I'm a total noob, so keep it sinple if possible please! :)

---

### Post by Spunkbubble on 2008-06-07
Bump. Anybody ever heard of how to fix this problem? I'm assuming that I'm not the only person to encounter this?

---

### Post by Spunkbubble on 2008-06-07
bump

---

### Post by Spunkbubble on 2008-06-07
bump

---

### Post by Unix_Slayer on 2008-06-07
> **Spunkbubble said:**
> Hi, I'm new to the whole linux experience, but looks really good. I have a higher spec PC running Vista (yeah rubbish I know) and Ubuntu 7.10 on another older PC.

Anyway, I have a Belkin 802.11g 54mbps network card, and am trying to use it to set up an internet connection, which will be vital for me if I'll be sticking with Ubuntu. I've done some checks, spent hours browsing tutorials and the like, and I think I've narrowed down the problem.

The system recognises the card, apparently the drivers are fine, I've tweaked my wireless settings for manual connection, but when I look at the information for the card, it's listed as disabled. I haven't done anything as far as I know to disable it, so is this a default setting? From what I gather it's hard if not impossible to enable it... or is this just talk? If there's a way to enable it, then I'm all ears since I think that's the problem, but bear in mind I'm a total noob, so keep it sinple if possible please! :)

Have you tried to install Ndiswrapper, and tried to install the .inf from the windows cd that came with the adapter?

---

### Post by Spunkbubble on 2008-06-07
I did try installing Ndiswrapper, but to be honest I don't even know if I installed it correctly, let alone how I'm actually meant to *use* it. I followed several tutorials, but most of the time I encountered a problem somewhere between step #1 and step #2. 

I couldn't run the installation disc that came with the adapter on Ubuntu, but it functions correctly on Vista. If I could transfer the .inf from the Vista PC to the Ubuntu, where could I find it? Where should I put it? And what exactly is a .inf file anyway?

---

### Post by Unix_Slayer on 2008-06-07
> **Spunkbubble said:**
> I did try installing Ndiswrapper, but to be honest I don't even know if I installed it correctly, let alone how I'm actually meant to *use* it. I followed several tutorials, but most of the time I encountered a problem somewhere between step #1 and step #2. 

I couldn't run the installation disc that came with the adapter on Ubuntu, but it functions correctly on Vista. If I could transfer the .inf from the Vista PC to the Ubuntu, where could I find it? Where should I put it? And what exactly is a .inf file anyway?

You have to think differently in Linux vs Windows. The .inf should be on the install cd from the adapters manufacturer. You'll see a drivers folder, and inside that folder should be a list of Win2ooo, WinXP, WinVista, Win98, and so forth. Put the cd in, and just copy that WinXP folder over to linux. Copy it to your Documents directory in your home directory. For instance, my home directory is /home/slayer/Documents The .inf file is instructions to your wireless adapter card to tell it what it should be doing, and why it's here. Sort of instructions. Install ndiswrapper. Open ndiswrapper, and it will have a button [add device]. That's when it will ask for the .inf. You point it to where you copied it to. As simple as that.

---

### Post by Spunkbubble on 2008-06-08
Ok, well I had a look in the drivers folder on the CD, but the only items contained were 'bcm43xx.cat', 'bcmwl5.inf', and 'bcmwl5.sys'. Since 'bcmwl5' is the only .inf I copied that to my desktop, and stuck it in my documents folder.

However, when I attempted to install Ndiswrapper I had a problem. I downloaded the compressed version, tranferred it to the Ubuntu via memory stick, then decompressed. The instructions on the website said to run "make distclean" first of all, but when I do this happens:

```
make -C driver clean
make[1]: Entering directory '/home/myname/Desktop/ndiswrapper-1.53/driver'
rm -f *.o *.ko .*.cmd *.mod.c *.symvers modules.order *~ .\#*
rm -f *_exports.h win2lin_stubs.h
rm -rf .tmp_versions
make[1]: Leaving directory '/home/myname/Desktop/ndiswrapper-1.53/driver'
make -C utils clean
make[1]: Entering directory '/home/myname/Desktop/ndiswrapper-1.53/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory '/home/myname/Desktop/ndiswrapper-1.53/utils'
rm -f *~
rm -fr ndiswrapper-1.53 ndiswrapper-1.53.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory '/home/myname/Desktop/ndiswrapper-1.53/driver'
[COLOR="Red"]make[1]: *** No rule to make target 'distclean'. Stop.
make[1]: Leaving directory '/home/myname/Desktop/ndiswrapper-1.53/driver'
make: *** [distclean] Error 2[/COLOR]
```

No rule to make target 'distclean'? What have I done wrong here?
By the way since I don't have internet access on the other PC this is manually written, there may be typo's.

---

### Post by Spunkbubble on 2008-06-08
bump

---

### Post by Unix_Slayer on 2008-06-08
> **Spunkbubble said:**
> Ok, well I had a look in the drivers folder on the CD, but the only items contained were 'bcm43xx.cat', 'bcmwl5.inf', and 'bcmwl5.sys'. Since 'bcmwl5' is the only .inf I copied that to my desktop, and stuck it in my documents folder.

Yup.... Those are what we are looking for.

> **Spunkbubble said:**
> However, when I attempted to install Ndiswrapper I had a problem. I downloaded the compressed version, tranferred it to the Ubuntu via memory stick, then decompressed. The instructions on the website said to run "make distclean" first of all, but when I do this happens:

```
make -C driver clean
make[1]: Entering directory '/home/myname/Desktop/ndiswrapper-1.53/driver'
rm -f *.o *.ko .*.cmd *.mod.c *.symvers modules.order *~ .\#*
rm -f *_exports.h win2lin_stubs.h
rm -rf .tmp_versions
make[1]: Leaving directory '/home/myname/Desktop/ndiswrapper-1.53/driver'
make -C utils clean
make[1]: Entering directory '/home/myname/Desktop/ndiswrapper-1.53/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory '/home/myname/Desktop/ndiswrapper-1.53/utils'
rm -f *~
rm -fr ndiswrapper-1.53 ndiswrapper-1.53.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory '/home/myname/Desktop/ndiswrapper-1.53/driver'
[COLOR="Red"]make[1]: *** No rule to make target 'distclean'. Stop.
make[1]: Leaving directory '/home/myname/Desktop/ndiswrapper-1.53/driver'
make: *** [distclean] Error 2[/COLOR]
```

No rule to make target 'distclean'? What have I done wrong here?
By the way since I don't have internet access on the other PC this is manually written, there may be typo's.

You shouldn't run distclean. You said you already installed ndiswrapper before? Try doing this in a terminal window.

```
sudo apt-get install ndiswrapper
```

I'm not sure if it's in the depositories. If you already installed ndiswrapper before with no errors. In a terminal window type this:

```
sudo ndiswrapper
```

Let me know if it worked.

Make note of this link: ===> [http://ndiswrapper.sourceforge.net/joomla/]("http://ndiswrapper.sourceforge.net/joomla/")

---

### Post by Spunkbubble on 2008-06-08
The first command got a response of "E: Couldn't find package ndiswrapper", and the second "sudo: ndiswrapper: command not found". I'm not sure the first time I attempted installation before anything actually got installed since there were a lot of errors.

---

### Post by Unix_Slayer on 2008-06-08
> **Spunkbubble said:**
> The first command got a response of "E: Couldn't find package ndiswrapper", and the second "sudo: ndiswrapper: command not found". I'm not sure the first time I attempted installation before anything actually got installed since there were a lot of errors.

Go to this link===> [http://ndiswrapper.sourceforge.net/joomla/]("http://ndiswrapper.sourceforge.net/joomla/")

And re-install the ndiswrapper like your doing it for the first time. If you can't run ndiswrapper, it's not installed.

---

### Post by Spunkbubble on 2008-06-09
Thanks, I'll take a look at this and have another go when I get home.

---

### Post by Spunkbubble on 2008-06-09
Attempting a fresh installation still returned the same results of "No rule to make target 'distclean'. Stop.", then "E: couldn't find package ndiswrapper". Proceeding and using the 'make install' command gave me a list of processes, and seemed to be running ok until shortly after "Building modules, stage 2." At this point, the only information given was a long string of lines starting with "loadndisdriver.c:xx:xx: error" and "loadndisdriver.c:xx:xx: warning" where x are different numbers. Mostly these seemed to refer to files that apparently should be present in ndiswrapper-1.53/utils (there are only 4 file in there). Re-downloading still didn't include any of these files.

---

### Post by Unix_Slayer on 2008-06-09
> **Spunkbubble said:**
> Attempting a fresh installation still returned the same results of "No rule to make target 'distclean'. Stop.", then "E: couldn't find package ndiswrapper". Proceeding and using the 'make install' command gave me a list of processes, and seemed to be running ok until shortly after "Building modules, stage 2." At this point, the only information given was a long string of lines starting with "loadndisdriver.c:xx:xx: error" and "loadndisdriver.c:xx:xx: warning" where x are different numbers. Mostly these seemed to refer to files that apparently should be present in ndiswrapper-1.53/utils (there are only 4 file in there). Re-downloading still didn't include any of these files.


Did you ./configure it first? Then you make. Then you make check. If everything goes alright, then you make install. Use sudo in front of the make, make check, and make install. Just look for errors before you make install. If there are errors, look in the config.log file in that directory. Either paste it up here, or tell me the main errors for compiling.

---

### Post by Spunkbubble on 2008-06-09
> **Unix_Slayer said:**
> Did you ./configure it first?

./configure? That wasn't in the instructions, so I didn't do that. Assuming that's a command, where do I execute it from? When I just type ./configure inside the ndiswrapper folder I'm told "No such file or directory".

---

### Post by Unix_Slayer on 2008-06-09
> **Spunkbubble said:**
> ./configure? That wasn't in the instructions, so I didn't do that. Assuming that's a command, where do I execute it from? When I just type ./configure inside the ndiswrapper folder I'm told "No such file or directory".


Open the README file in the directory. If there is a configure file in green [xterm after ls], then you need to ./configure first.  But you can go to the Adept Manager, type in ndis.... and Ubuntu will install it for you. This will make it easier on you.

---

### Post by Spunkbubble on 2008-06-10
> **Unix_Slayer said:**
> Open the README file in the directory. If there is a configure file in green [xterm after ls], then you need to ./configure first.  But you can go to the Adept Manager, type in ndis.... and Ubuntu will install it for you. This will make it easier on you.

I'm not sure I understand what you're getting at here. I can open the README, which has some basic information and links, but what does that have to with the rest? I'm not seeing a configure file anywhere under ndiswrapper or in any subdirectories, where did you mean specifically to search for it? What do you mean by 'xterm after ls'? And is ./configure a command? Is Adept Manager a program? Where can I find it?

Sorry to be a pain, but I have to ask you to dumb down a bit more for my poor little noobie brain :confused:

---

### Post by Unix_Slayer on 2008-06-11
> **Spunkbubble said:**
> I'm not sure I understand what you're getting at here. I can open the README, which has some basic information and links, but what does that have to with the rest? I'm not seeing a configure file anywhere under ndiswrapper or in any subdirectories, where did you mean specifically to search for it? What do you mean by 'xterm after ls'? And is ./configure a command? Is Adept Manager a program? Where can I find it?

Sorry to be a pain, but I have to ask you to dumb down a bit more for my poor little noobie brain :confused:

It's on the start menu. It might be called "Add and Remove Programs".

---

### Post by stchman on 2008-06-11
> **Spunkbubble said:**
> Hi, I'm new to the whole linux experience, but looks really good. I have a higher spec PC running Vista (yeah rubbish I know) and Ubuntu 7.10 on another older PC.

Anyway, I have a Belkin 802.11g 54mbps network card, and am trying to use it to set up an internet connection, which will be vital for me if I'll be sticking with Ubuntu. I've done some checks, spent hours browsing tutorials and the like, and I think I've narrowed down the problem.

The system recognises the card, apparently the drivers are fine, I've tweaked my wireless settings for manual connection, but when I look at the information for the card, it's listed as disabled. I haven't done anything as far as I know to disable it, so is this a default setting? From what I gather it's hard if not impossible to enable it... or is this just talk? If there's a way to enable it, then I'm all ears since I think that's the problem, but bear in mind I'm a total noob, so keep it sinple if possible please! :)

Is this wireless card internal or PCMCIA type?  If yes give us an lspci output in this thread.

---

### Post by ubume2 on 2008-06-11
Hi, I don't know if this will help you or not. I am using 8.04 LTS.  I have a Belkin wireless USB adapter, not a card. I use 128 bit WEP encryption. I tried the how to here:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

The contents of that howto did get me to my final solution.  I think my driver is native to a couple of the more recent versions of Ubuntu, so using ndiswrapper probably got in the way of a solution for me.

Tried ndiswrapper, installing drivers, blacklisting and all that. I couldn't get it to go.  Finally, with my experience on Dapper, I ignored  Network Manager. Uninstalled the drivers installed by ndiswrapper, and uninstalled ndiswrapper.

I eventually got my wireless to work on bootup.

You have to edit /etc/network/interfaces and /etc/rc.local. I believe that part is covered in the how to.

```
$ iwconfig
``` and see what your valid device is.

My valid device is eth1 so I entered this in /etc/network/interfaces:
auto eth1
iface eth1 inet dhcp

do sudo gedit /etc/network/interfaces    to get there.

Then in /etc/rc.local I added the following:
dhclient -r eth0
ifconfig eth1 up
iwconfig eth1 essid "2WIRE900"
iwconfig eth1 encryption on
iwconfig eth1 key a1b2c3d4e5 ASCII
#iwconfig <interface> mode Managed  # I did not need this
dhclient eth1

I saved the file. At first it didn t work. I had to change the first line
from #!/bin/sh -e           to
#!/bin/bash             to get it work.

I don't know why that change did it, but it worked for me.  I had internet on reboot.

Edit: Before rebooting I gave rc.local its permissions. $chmod +x rc.local

---

### Post by Unix_Slayer on 2008-06-11
Things are funny sometimes in linux. I bought a USB adapter for one of my systems. [Hawking Technologies - HWug1] I installed KUbuntu, and it found the adapter right away. Worked the first time I booted.

---

