---
title: "Is there anyway to get a list of everything installed on my computer?"
date: 2008-10-20
forum: General Help
---

### Post by /////// on 2008-10-20
Ehh title says it all, is there anyway (like a terminal command or something) to list all the applications that I have installed on my computer? I want a list of applications that I installed not ones that come with the OS for example, I can't just get it to list all the apps in say /usr/bin that would give me far to much applications.

---

### Post by roycebarber.com on 2008-10-20
I'm a noob to Linux, but the only way I get a list of installed programs is to go to the Add/Remove program in Ubuntu, and click the drop-down box that lists "View Installed Applications Only" or somethint like that.

---

### Post by leg on 2008-10-20
I am pretty sure you can get that information out of synaptic but not completely sure how.

---

### Post by /////// on 2008-10-20
I don't think that will work because that wouldn't list the programs which I installed from say source code

---

### Post by jespdj on 2008-10-20
You can get a list of installed packages with the command:
```
dpkg -l
```
(that's a lower case L).

This will not list software that you installed manually by compiling code from source and running for example "sudo make install"; that software isn't registered in a list anywhere on the system, so there's no way to get a list of software that you installed that way.

---

### Post by sethvath on 2008-10-20
dpkg --get-selections > ~/Desktop/installed-software.log

This saves a list of your installed software as a log file on your desktop. 

To install the same list of software on a new computer:

dpkg --set-selections < ~/Desktop/installed-software.log
dselect

---

### Post by Yellow Pasque on 2008-10-20
> This will not list software that you installed manually by compiling code from source and running for example "sudo make install"; that software isn't registered in a list anywhere on the system, so there's no way to get a list of software that you installed that way.
I just wanted to add that software built from source can be "inventoried" in the packaging system by using checkinstall [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by /////// on 2008-10-20
sethvath I noticed that dpkg --get-selections also lists some system files, if say I was to install all the packages using this method from 8.04 to 8.10 would that work?

---

### Post by sethvath on 2008-10-20
I was about to do a clean install of intrepid, could test it out for you while I'm at it. 

I do not forsee any issue upgrading the listed system files since the version number in intrepid is higher than what you have in hardy - nothing will be downgraded unless you specifically choose to do so. 

Be back in a few hours after reinstalling and I'll revert to you on how it goes.

---

### Post by /////// on 2008-10-20
thanks

---

### Post by sethvath on 2008-10-20
Ok I have a fresh install, everything works as intended. If its a new system make sure you have dselect installed first. sudo apt-get install dselect

sudo dselect, choose option 3: install and upgrade wanted packages.

---

### Post by jenaniston on 2010-01-29
> **jespdj said:**
> You can get a list of installed packages with the command:
```
dpkg -l
```

Also note . . .
if you are in a terminal and want to pause the screen from scrolling . . . use the variation -
```
dpkg -la | less
```This allows *you* to do the scrolling with the arrow keys or space bar - rather than have it whiz by to the end of the list . . .

enter <q> to quit back to terminal prompt.

---

