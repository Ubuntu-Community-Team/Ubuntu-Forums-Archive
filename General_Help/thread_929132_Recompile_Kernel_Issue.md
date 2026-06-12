---
title: "Recompile Kernel Issue"
date: 2008-09-24
forum: General Help
---

### Post by NuNn DaDdY on 2008-09-24
I am trying to recompile my kernel with little or no modules installed on it.  However I am running into issues doing this because when I run my 'lsmod' command, the modules listed there don't match what is in the 'make menuconfig' configuration.  Is there a simpler way of going about this rather than just trial and error which is tedious due to the length of compiling the kernel.  Thanks.

---

### Post by DagMan on 2008-09-25
This post [http://sudan.ubuntuforums.com/showpost.php?p=3478720&postcount=19](http://sudan.ubuntuforums.com/showpost.php?p=3478720&postcount=19) has a link that points to a perl script that will look at all the loaded modules, then write a config file that only uses them.  The drawbacks are that things that aren't in use that you will need are taken out.  For example when you plug in a usb stick formatted to fat32, the OS loads the modules needed to use the usb device and to read and write to the file system.  When you plug in a joystick, same thing, printer etc.  This will probably also take out your ability to firewall and say for example that you're currently using one type of encryption for your wireless but another module handles another type.  If you need to connect elsewhere then you might have a problem.  Stuff like that.
The good news is that when you have a small kernel, recompilation to add things goes way quicker than doing the whole thing, so as long as you keep the source hanging around you can always add things that you find you forgot to enable after running the script.  Best thing when running it is to plug in every conceivable device that you might use though, then go through the menu before compiling and look for things that you might think you'lle miss, for example the ability to read cd's and dvd's needs to be enabled in filesystems if you don't have one mounted while doing it.
Some things, like sound, you're going to need to either enable in the kernel you compile or build the modules afterward no matter what you do.

---

