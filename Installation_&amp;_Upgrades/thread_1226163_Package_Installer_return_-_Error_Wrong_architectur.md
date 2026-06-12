---
title: "Package Installer return - Error: Wrong architecture 'm689'"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by crystaldart on 2009-07-29
I am trying to install KEXI software pakage (kexi_1.6.3-7_m68k.deb) manually on my PC (No Internet facility).

But the package installer returns [COLOR=Red]**Error: Wrong architecture 'm689' **[/COLOR].

Am new to Linux. Please lend me a hand to install this package.

Thank you all.

---

### Post by bryonak on 2009-07-29
Free/Open Source Software is usually available for many processor architectures, amongst others x86, AMD64, SPARC, ARM, Power, ...
Those are CPUs used in your cell phone, watch, ... (toaster ;))

x86 (also called i386) and AMD64 are the most widespread for **desktop computers and laptops**, so you'll want to use those packages that are compiled for your system.
That's x86 if you've installed Ubuntu 32 bit and AMD64 for Ubuntu 64 bit.
m68 is for Motorola processors and probably of little use to you.


As for Kexi... why not open the menu: System -> Administration -> Synaptic Package Manager.
There search for "kexi", mark it and hit apply ;)

*EDIT:*
Scrap that, I should read more precisely... download a x86 or AMD64 package from the [web front end]("http://packages.ubuntu.com/") of Ubuntu's repositories.
But keep in mind that you also have to install all the dependencies (marked red in the web repository), which might turn out quite a tedious task. This is called "dependency hell".
You could try to install Kexi on another machine and copy all the downloaded packages from the cache.

---

### Post by crystaldart on 2009-07-30
[FONT=Tahoma][SIZE=2]Thank you very much [/SIZE][/FONT][SIZE=2]bryonak. I really appreciate your help.

[/SIZE][COLOR=Red]***..You could try to install Kexi on another machine and copy all the downloaded packages from the cache. 		***[/COLOR]                   		  		  		 		 

[SIZE=2]1. don't I have to first retrieve and compile all the dependencies from the cache?

2. How do I find these downloaded packages?

3. Please instruct on the installation.

Thank you once again[/SIZE]

---

### Post by earthpigg on 2009-07-30
i think i may have missed something in this thread.

what is wrong with the version of kexi 1.6.3 in the repos?

edit, nvm, reread and got it.

1. retrieve, yes. compile, no. they will be .deb files located at /var/cache/apt/archives on the source computer that has internet access. this system will need to be *the same architecture* as the target machine. if that is not possible, let us know.

2. see #1.

3. double click and then click 'install'. dependencies will need to go before what depends on them. click around and see what works.

---

### Post by bryonak on 2009-07-30
Maybe I have to extend a bit on earthpigg's (correct) answer.


The majority of applications only has small dependencies, so you can simply install them with two or three packages.

Now the "problem" with Kexi is that it's a KDE (comes with Kubuntu) application, while you are probably using the Gnome (comes with standard Ubuntu) desktop environment.
So installing it on Ubuntu requires many KDE libraries and core functionalities, likewise installing Gnome applications on Kubuntu.
When I try to install it on my current system (Ubuntu/Gnome) it requires 200MB of KDE stuff.

You might want to search the forums for comparisons of those two desktop environments.

Compiling is something you should never be forced to do as a user. The package maintainers compile the source code for different architectures, package the resulting binaries and offer them via the repositories / on the internet.


As for installing Kexi, my first recommendation is to wire up that PC with the internet. Then you can simply install it via the package manager, which will automatically take care of all dependencies for you.

If you can't do that, and since installing so many dependencies by manually downloading them from the web is too cumbersome, the other solution would be to install Kexi via the package manager on another Ubuntu machine of the ***same** version (say 9.04) and architecture (64bit or 32bit)*.
The package manager on that computer would download all the dependencies and store them in it's cache. You can then copy the cache to the other machine and install the packages there.


I hope you're comfortable enough with the terminal, which is much more precise and simple for us to write... and usually faster for you to execute.
If not, write back and we might try to walk you through it graphically.

Open a terminal on a machine with internet access (and the same Ubuntu version/architecture as your other) and type:
```
sudo aptitude clean
```
This will clean the cache, so you don't mix up packages. Then type:
```
sudo aptitude install -d kexi
```
The '-d' will only download the packages (without installing) to the /var/cache/apt/archives folder.
Copy the files ending with **.deb** from that folder to your other PC.
You can clean the cache on your internet computer again with ```
sudo aptitude clean
```

On your other machine, put all the files in one folder, for example "foo" on your desktop.
Since installing every single one of them by klicking is way too slow, we'll use the terminal again.
Browse to that folder within the terminal with the 'cd' (change directory) command... that should be about:```
cd Desktop/foo
```
Then install all the packages in that folder with:```
sudo dpkg -i *
```

---

### Post by crystaldart on 2009-07-30
Thank you Earth Pigg. 

Bryonak, that was a very helpful lead. Thank you once again.

---

