---
title: "Splashy Won't Install - broken package"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by lateralus01 on 2009-03-23
For some reason I can't install splashy:

```

mark@Ubuntu:~$ sudo apt-get install splashy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  console-common
The following NEW packages will be installed:
  splashy
0 upgraded, 1 newly installed, 0 to remove and 65 not upgraded.
1 not fully installed or removed.
Need to get 0B/1180kB of archives.
After this operation, 1831kB of additional disk space will be used.
(Reading database ... 113387 files and directories currently installed.)
Unpacking splashy (from .../splashy_0.3.13-3ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/etc/lsb-base-logging.sh', which is also in package lsb-base
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I don't know how to fix this, I've tried removing /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb so that it would download it again and that did nothing.  Then I tried compiling from source but ./configure won't work because it requires glib-2.0 which my system has but it's called something different in Ubuntu so yeah.

Anyone know what to do?
Ubuntu 9.04
Kernel 2.6.28

Thanks,
Lateralus01

---

### Post by Partyboi2 on 2009-03-25
Open a terminal (Applications>Accessories>Terminal) and try 
```
cd /var/cache/apt/archives
```
then 
```
sudo dpkg --force-overwrite --install splashy_0.3.13-3ubuntu1_i386.deb
```

Hopefully this will sort the problem out :)

---

### Post by Zachs Kappler on 2009-09-19
I'm getting this in Xubuntu, but it doesn't have dkpg, but gdebi, and the version of synaptic it has lacks a clear cache button. any other way to get it to retry installing it? For the life of me I can't find Usplash creation how to's for anything but it.

---

### Post by Partyboi2 on 2009-09-19
If you are getting the same error as the OP you should be able to open a terminal and change directory to where the splash deb you downloaded is, so if its on your Desktop use
```
cd ~/Desktop
```
then install the package with
```
sudo dpkg --force-overwrite --install splash*
```

---

### Post by pickarooney on 2009-09-20
This won't work as the dependent libsplashy won't install.
There seems to be a fundamental problem with Splashy in the repositories - you can't install it and you can't uninstall it completely either.

---

### Post by hazyumps on 2009-09-29
A MILLION THANKS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 12 hrs of my life spent digging through make files and here you are - 

Really though THANKS

---

### Post by steve19137 on 2010-01-06
omg! exactly what i needed! thanks!

---

### Post by KillerNumberX on 2010-01-16
Hi! I FIXED IT!! FINALLY!!!

Okay, I had given up and was looking up about using gedit instead of nano, and also how to open kate because I wanted to edit a file using kate from command line (terminal) ...

long story short, its SIMPLE

I ran the following command (in Terminal):

```
sudo aptitude install libgtksourceview
```essentially it discovered the inconsistencies relating to splashy, and the one/that the deb is, broken, and the failed dependencies;
ultimately it discovered the solution, which was to... wait for it... REMOVE libsplashy1-dev

so after I had put that command relating to libgtksource into Terminal, it ran, told me these things, and asked me if I wanted to remove it, I clicked YES (typed the letter y) and it finished up and NOW ALL THE REST OF EVERYTHING IS FIXED TOO!!!

-

NOTE: It may or may not be important to note, that I ran the command from root - I always run commands from root. Whenever I open Terminal, I type:

```
sudo -i
```

and then it prompts me for my password, which I do; this way I have absolute complete (root) privileges.

-

P.S. I'm running Kubuntu 9.10, fresh install, I used Wubi for the install and everything's been all set up for a day now. It is successfully Dual-Booted with Windows 7; if anyone has questions about this send me a message or direct me to the thread (better, then I only have to answer the question once!)

P.S.S. I'm running Windows 7 Ultimate, but immediately upon getting this Kubuntu, I am sold!!! I WANT TO USE UBUNTU AND I AM NEVER GOING BACK TO WINDOWS!!!

Firefox is TEN TIMES faster - it's the equivalent as if I did $3,000 worth of upgrades to my computer!!

Also it looks great (aesthetically)! Screw Windows for good! XD

---

