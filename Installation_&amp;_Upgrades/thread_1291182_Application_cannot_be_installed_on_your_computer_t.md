---
title: "Application cannot be installed on your computer type (i386). Please help..."
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2009-10-14
Hello everyone

I have a VAIO model VGN-BX197XP and decided to install on it, dual-boot 9.04. Everything went smoothly. I updated everything through the update manager, so my system is now up-to-date.

What is strange is that when I try to install **any** of the programs through "add remove programs" I get the following error:

[B]Application XXXXX XXXXXX cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.[/B]

I don't understand why! I have installed numerous times on different computers, but have never seen that.

Anyone has any idea?
Thank you
Ifaistos

---

### Post by dstew on 2009-10-14
In the Add/Remove Applications window, do you see a Preferences button on the lower left? If so, click it, and enable the "Downloadable from the Internet" sources.

---

### Post by Ifaistos on 2009-10-14
Thank you for your suggestion :-)

Unforunately I don't see such an option.  I went though to System > Administration > Software Sources and all the downloadable from internet sources are checked.

Any other idea?

---

### Post by earthpigg on 2009-10-15
hi,

i think the reason no one is responding is due to a collective "how the heck did you manage to do ***that***?!"


so, um.... how did you?

---

### Post by Ifaistos on 2009-10-15
I really have no idea !!

This is a fresh install!  Nothing weird.
I installed from the USB, everything went fine.

Grub Identified everything, Dual boot works great.  The Ubuntu Linux works great... I am writing this message from my firefox on Ubuntu.

I updated everything through Update Manager... everything went smoothly...

and then I tried to install new programs... first I tried restricted ubuntu extras and I thought that it would be only that... but it denies to install anything at all!!!

Mind you, than when I tried to open a page with flash, it told me that I need to install somekind of plugins, it searched and it gave me 3 different options, then installed the flash I chose and everything is fine.

I am buffled, as much as you are...  Any suggestion is welcome..

---

### Post by diesch on 2009-10-15
Does installing packages from the command line using 
```
apt-get install some_package
``` work?

What's the output of ```
dpkg-architecture 
```

---

### Post by Ifaistos on 2009-10-15
The command :

sudo apt-get install thunderbird... worked just great !!!

The only difference between the two commands is a space between "dpkg" and "-architecture"

**XXX@VaioLinux:~$ dpkg-architecture**
The program 'dpkg-architecture' is currently not installed.  You can install it by typing:
sudo apt-get install dpkg-dev
bash: dpkg-architecture: command not found

**XXX@VaioLinux:~$ dpkg -architecture**
dpkg: conflicting actions -c (--contents) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by diesch on 2009-10-15
The command is really "**dpkg-architecture" **(without space)**. **I didn't know it's not installed by default.It prints some information about what computer architecture apt thinks you have.
As apt-get worksthat doesn't seem to be the problem.

Looking at the source code of Add/Remove it seems that this error message is some kind of catch-all for when a application should be there but isn't. I guess it's a bug.

Do you get any messages if you start gnome-app-install in a Terminal and try to install something?

---

### Post by Ifaistos on 2009-10-16
You can read the code?!!! R.E.S.P.E.C.T.!!

How do I do that?

---

### Post by lostandcold on 2009-10-16
My wifes computer also has this problem.  She is currently using 9.10 (Beta) so I thought that might be he problem, but maybe not.

---

### Post by noway2 on 2009-10-19
I have seen this error pop up when I try to run an application that was compiled on a 32 bit system and uploaded to a 64 bit system.  Try getting the application from source and building it for your system.  Normally, usage of the correct repositories should prevent this sort of issue.

---

### Post by ram2500 on 2009-10-19
Call me behind the times, but I still use 32-bit everything as we are still not completely ready for the 64-bit transition, obviously, as both Windows, Linux (and everything else) still has a majority of 32bit apps, drivers and whatnot installed on the average 64bit PC. I have the maximum RAM that 32bit will allow me (3 GB), and so I can safely say I rarely touch the swap partition in a big way in Ubuntu, even when running six different OpenOffice windows, GIMP and having a ton of tabs in Firefox open, nonetheless, I fill my clipboard up. So, I don't see the justification of 64bit *yet*...

I think that having 32bit and 64bit versions on separate partitions would be the better idea. For some reason, after trying 64b Ubuntu, i386 versions of software did work, but some refused to install (insisting on amd64) - anyone know why? I know that in 64 bit Windows, I can even install an app from 1997 if I wanted to (definitely not 64b! :))...

---

### Post by earthpigg on 2009-10-19
> **ram2500 said:**
> I think that having 32bit and 64bit versions on separate partitions would be the better idea. For some reason, after trying 64b Ubuntu, i386 versions of software did work, but some refused to install (insisting on amd64) - anyone know why? I know that in 64 bit Windows, I can even install an app from 1997 if I wanted to (definitely not 64b! :))...

a 32bit .deb will insist on needing that architecture. if it's a non-free program that is only released in 32bit, sometimes, you can simply dissect and repackage the .deb to make it work: [http://ubuntuforums.org/showthread.php?t=1070885](http://ubuntuforums.org/showthread.php?t=1070885)

certain apps will also use 32 bit libraries that you can install for this specific purpose.

i've been using 64bit for some time now, works fine.

Ifaistos: i still have no idea how to help you. if i where in your shoes bumping this thread for so long with a broken system, to be honest, i would have backed up my /home and done a fresh install by now.

---

### Post by Ifaistos on 2009-10-20
I will try to do a fresh install... 
although I have a feeling that this will not solver the problem...

any suggestions as to what I should be careful off, or tweak during the installation?

Thanks

---

