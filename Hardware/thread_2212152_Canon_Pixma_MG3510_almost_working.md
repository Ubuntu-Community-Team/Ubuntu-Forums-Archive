---
title: "Canon Pixma MG3510 almost working"
date: 2014-03-19
forum: Hardware
---

### Post by Argard on 2014-03-19
Hi guys,

I bought a Canon Pixma MG3510 printer a few days ago and it's possible to download the printer drivers (src and bin) from the Canon site. (+ point)
I installed the bin drivers in 13.10 ubuntu and it seems that installed correctly (+ point). 
But the first drawback was the apparmor. For some reason it didn't let me send data from the computer (through "lpr -Pmg3500 document.pdf") to the printer (wi-fi connection). I disabled the apparmor (I could add an exception, but it's faster this way) and the data went to the printer. Now, when I print something, the power light blinks for some time, about a 30 seconds, and after this time it went back to the permanent and all fine green light. But there's one problem: the printer didn't print anything (- point)

If anyone here had a similar problem, let me know. I'm open to suggestions. Thanks.
ps1: I tried to search the forum before, the keywords: mg3510 and pixma mg3510, but the search didn't brought anything useful.
ps2: I will try to compile the driver from src, but this could take time because I don't have the tools (build-essentials, kernel-headers, cmake, etc ...) in this computer.
ps3: Complain to canon website will take more time than ask in the forum :-) (forum rules)

---

### Post by pdc on 2014-03-19
Canon supply the printer driver for the MG3500 series devices .........in .deb format; (ie for debian based distros, and Ubuntu is one of those); (as well as in rpm format for ..opensuse etc)

so the simplest way is to install the .deb package; Canon supply an install script; so that script determines if your system is 32bit or 64bit; and installs the correct drivers;

so here on a Mint forum 

[http://forums.linuxmint.com/viewtopic.php?f=49&t=162769](http://forums.linuxmint.com/viewtopic.php?f=49&t=162769)

I describe how to install the deb packages for both the printer side of the device, and the scanner side .........

If you copy and paste 

> [COLOR="#FF0000"]dpkg -l | grep cnijfilter[/COLOR]

into a terminal, it is asking what packages are installed 

can I suggest you remove what you have installed: with the command 

> [COLOR="#FF0000"]sudo dpkg -P cnijfilter[/COLOR]

and then install as per the advice above; using the deb packages produces a working device

(If you don't want to remove what is already installed, you need some way to recognise which driver you want to use ......)

Hopefully some of this is of help best wishes

---

### Post by Argard on 2014-03-20
Hi pdc,

Thanks for your detailed answer, I really appreciated!
I managed to install the drivers through the steps described in the mint forum before. Scanner drivers too. But they didn't work perfectly. I'm kind looking for a way to debug the printer errors, since it receives data and doesn't print anything. dmesg only give the host errors, not the errors of the printer (It should be a way to do that...) 

But I will follow your advice and remove the result of canon automatic script and install the specific x86_64 deb driver. 
When I get home, I will try it and post the result.

Thanks for your time :)

---

### Post by pdc on 2014-03-20
if you want to work through debugging ............. [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

you will see in this that a command to list problem jobs is

> [COLOR="#FF0000"]cupsctl LogDebugHistory=999999[/COLOR]

_________________________________________________________________________________

> [COLOR="#0000FF"]But they didn't work perfectly[/COLOR].

........ are you able to tell us in more detail ..............

---

### Post by Argard on 2014-03-21
Good morning (gmt -3) pdc,

I obtained success installing the printer driver doing as you said:
1- Purging all installed packages from the automatic installer
2- Installing the packages directly through the *amd64.deb files ("sudo dpkg -i *amd64.deb"). 
3 -Configured the printer through the system-config-printer wizard (just this). It recognizes the printer and install the printer driver correctly. The linux driver supports the double side print (super cool/economic stuff).
4 - The scanner, not so necessary for me, will wait a little bit. But I will do as you said.
5 - Thanks for your time and attention.

---

### Post by pdc on 2014-03-22
great; glad to know the printer side is working; the scanner setup is very quick too

---

