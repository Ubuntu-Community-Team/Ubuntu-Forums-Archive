---
title: "Minetest Help"
date: 2013-07-08
forum: Hardware
---

### Post by jjhinch on 2013-07-08
Hi

I've got Minetest 0.4.3 installed and running through the Ubuntu Software Center a while back.

This is now really old, and does not work with the servers running newer versions, and i want to upgrade to the current version, 0.4.7.  I do not know how to download and install/run the program via terminal/other means.

Would be very greatfull for some step by step instructions......

Thanks

---

### Post by Cheesehead on 2013-07-08
Fascinating, since 0.3.1 is in 12.04, 12.10, and 13.04 repositories.
0.4.7 is in pre-release testing for 13.10

You have three options:
1) You can look for a PPA with a newer release of Minetest. PPAs are unsupported software, and may risk breaking your system. However, this option is much more convenient than compiling yourself.

2) You can try downloading the 0.4.7 deb from [http://packages.ubuntu.com](http://packages.ubuntu.com), and install it manually.** Warning**: Trying to install packages intended for a different release of Ubuntu is not supported, and seriously risks breaking your system.

3) You can compile the latest version of Minetest using the instructions at [http://dev.minetest.net/Compiling_Minetest](http://dev.minetest.net/Compiling_Minetest) . This route is (opinion) safer than PPAs, and *much* safer than mismatched packages. It can, however, be much more tedious, and perhaps a bit scary if you have never compiled before.

---

### Post by jjhinch on 2013-07-09
Thx. i have copied and pasted the minetest folder (called "recipe-0.4.7-0ppa1") into /usr/share.    pls could i have the terminal commands for what to do next/how to run it.

Thank you very much for your help

---

### Post by Cheesehead on 2013-07-09
If it's a PPA, you don't copy-and-paste it.
You add the PPA to your Software Sources, and then you install it normally using the package manager.

For example, to add the version of Minetest 0.4.7 at [https://launchpad.net/~minetestdevs/+archive/stable](https://launchpad.net/~minetestdevs/+archive/stable),
```
sudo apt-get autoremove minetest           # Prevents confusion between the versions
sudo add-apt-repository ppa:minetestdevs/stable 
sudo apt-get update
sudo apt-get install minetestc55
```
Warning:
PPAs are not supported software. If they cause a problem, contact the PPA owner. 
PPAs should be disabled before you upgrade your system. If you don't, the upgrade may go horribly wrong.
PPAs are intended for testing. When the next version of Ubuntu is released, check for the software in the Ubuntu Repositories instead or re-adding the same PPA.

---

### Post by jjhinch on 2013-07-09
I've installed it, and when i tried to run it, the program closed, and wont run.

This is what the terminal says

hinchliffe@hinchliffe-OEM:~$ minetest
Irrlicht Engine version 1.7.2
Linux 3.2.0-49-generic #75-Ubuntu SMP Tue Jun 18 17:40:13 UTC 2013 i686
Creating X window...
Visual chosen: : 39
Using renderer: OpenGL 3.3.0
GeForce 9400 GT/PCIe/SSE2: NVIDIA Corporation
OpenGL driver version is 1.2 or better.
GLSL version: 3.3
Loaded texture: /usr/share/minetest/textures/base/pack/menu_header.png
Segmentation fault (core dumped)

ive got no idea what to do now......

Thanks

---

### Post by Cheesehead on 2013-07-09
First, how -exactly- did you install Minetest? Did you follow the example (including autoremove)? Did you skip any steps?
Did you get any error messages? (You can find old error messages in /var/log/apt/term.log)

*PPAs are not supported software*, so the support you can get for a PPA in this forum is limited.
For example, I am unable to reproduce your crash. I'm running the 12.10 version of that PPA, and it works great for me.

---

### Post by jjhinch on 2013-07-10
I did the commands


sudo apt-get autoremove minetest
sudo add-apt-repository ppa:minetestdevs/stable 
sudo apt-get update


and then when i tried to do the command sudo apt-get install minetestc55, it  said there was and error message. i then went into the ubuntu software centre and it said there was some other minetest related things installed. i went to remove them, and then it said that they were already removed.Next i told the program i had just got to install. this went ok, so i tried to run it. then it happened

---

### Post by Cheesehead on 2013-07-10
Don't try to use Software Center to fix a package error that you don't understand.
Package management errors are important. It's the system trying to tell you "**Stop! You're about to break me!**"

Instead, stop and search-engine the error text. Or ask here. We can help.

Let's find out if you broke your system (risk of using a PPA):
Does update-manager work? Or does it error or otherwise fail?

If your package system is broken, then we need to fix that first. Let us know.
If your package system works great (whew, mop brow), then we need to find the EXACT error message when you tried to 'apt-get install minetestc55'. We already told you where to find old apt-get error messages....

---

