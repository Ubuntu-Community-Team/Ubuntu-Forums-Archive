---
title: "Compiling whole/most of system from source."
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by Kirky_D on 2008-12-07
Hi there!

Is it possible to install a package the repositories by downloading the source then compiling it so it's optimised for my pc? I've looked into apt-build but it doesn't seem to be maintained any more.

Is it possible? Cheers

---

### Post by Claus7 on 2008-12-07
Hello,

it is possible.

It depends of cource mostly on what you want to install. It might be better to switch to a new version if you see that most of the applications you need are not supported.

What do you want to install from source?
Mostly what you have to do is :
./configure
make
make install

yet, if you are lucky this will work. In any other case you have to solve all the dependencies yourself! And sometimes this is a very hard task. There is also the dependency hell issue, which, if you face it, is based on the situation on how to solve it.

I would recommend you to install from source only packages that they are easily installed and that you are in great need of. For example vmd for visualizing molecules is a package that cannot be installed via synaptic. So installing it from source is the only option. The installation is not so difficult. 

Regards!

---

### Post by Kirky_D on 2008-12-07
Thanks for the reply. What i actually mean is when i download and install a file via synaptic, instead of simply copying the pre-compiled files onto my system I want to use synaptic (or apt or any command line tool) to download the source, compile it, then install it. I want my system optimised for my cpu.

It might be a bit of a hassle trying to find all my packages online and compiling manually.

---

### Post by Claus7 on 2008-12-07
Hello,

sorry, yet I do not get it. If you use synaptic you do not have to use anything else. It is supposed to have the packages configured and installed in such a way to your system that you should not have to care about. In other words, synapitc does the installation as better as possible to your system. 

The other way is to go to the download page of the package you want to install, download it and install it. 

Am I missing something? 

Regards!

---

### Post by Kirky_D on 2008-12-07
The installation is not the issue. All packages in synaptic are optimised for the i386 architecture(very old). I want to compile from source so the packages are optimised for my computer instead of a generic binary that works on all computers but is not optimised.

---

### Post by Kirky_D on 2008-12-09
bump

---

### Post by Claus7 on 2008-12-10
Hello,

and this is causing you so much trouble? In other words is like building your own distro. This is what I'm making out.

There are so many libraries you want to build on your own? Just go in their site and download them. As far as the architecture is concerned do ubuntu has also a 64 architecture, if this is what you are interested for?

There is nothing more I can think of...

Regards!

---

### Post by oldos2er on 2008-12-10
Synaptic cannot do what you want it to do; it can download the source for you, but you'll need to compile it yourself. Why not use a distro like Gentoo which is designed for this very thing?

---

