---
title: "Old laptop, too old for Ubuntu?"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by Protex on 2006-01-17
Hey there. I just got a laptop with these specs.

Pentium II Mobule 400MHZ
5.5gb HDD
64mb Ram

I'm assuming that Ubuntu is too much for it to handle, was wondering if anyone could reccomend an OS besides DSL? I've tried DSL and just overall don't like it.

Keep in mind that this laptop does not have net access so I'd need something that has all the packages I'll need right out of the box. Basically only need word processing and other things for school.

Thanks in advance.

---

### Post by Sef on 2006-01-17
Not necessarily too old.  But do a server install and then at the command line type this:

sudo apt-get update

sudo apt-get install xubuntu-desktop

at the command prompt: startx (it is like win in windows from the command prompt.

Note: there are other window managers you could, try like fluxbox, icewm, etc.

For other distros, try DSL, or FeatherLinux

---

### Post by Protex on 2006-01-17
[QUOTE=Sef]Not necessarily too old.  But do a server install and then at the command line type this:

sudo apt-get update

sudo apt-get install xubuntu-desktop

at the command prompt: startx (it is like win in windows from the command prompt.

Note: there are other window managers you could, try like fluxbox, icewm, etc.

For other distros, try DSL, or FeatherLinux[/QUOTE]

I can do those sudo apt-gets without an internet connection? Is there a way to burn the packages I need and just load them up?

---

### Post by az on 2006-01-17
If you can add at least another 64 megs of ram, it will run ubuntu just fine.

---

### Post by az on 2006-01-17
[QUOTE=Protex]I can do those sudo apt-gets without an internet connection? Is there a way to burn the packages I need and just load them up?[/QUOTE]

[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by Ozitraveller on 2006-01-17
I have Ubuntu running happily on a PII/400 with 389mb ram, 64MB video and 10 and 30 gb HD's. I have xubuntu and it also works well, but I'm waiting until xubuntu dapper comes out, there is still a few things to do yet.

And yes DSL, FeatherLinux or Puppy are also good options.

Ans also these too:

**HOWTO Ubuntu mini ram**
[http://ubuntuforums.org/showthread.php?t=42873](http://ubuntuforums.org/showthread.php?t=42873)

**Ubuntu Mini-RAM HOWTO**
[http://ubuntuforums.org/showthread.php?t=8338&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=8338&page=1&pp=10)

---

### Post by Michael Steinberg on 2006-01-17
Another good distro for older machines is STX, though its default desktop is rather dowdy:

[http://www.stibs.cc/stx/](http://www.stibs.cc/stx/)

---

### Post by Protex on 2006-01-17
[QUOTE=azz][https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)[/QUOTE]

I've decided to use the mini-ram how-to, but I still need to get the packages needed.

I've read the How-To you told me to, but I am not sure I understand it. After reading I still don't know where I am supposed to put the downloaded .deb packages. And the part it tells me about erasing packages from my UbuntuCD doesn't work, as the Ubuntu CD cannot be read in my OS for some reason (but it can be used on boot).

Have a more newbie-friendly tutorial?

---

### Post by az on 2006-01-17
[QUOTE=Protex]I've decided to use the mini-ram how-to, but I still need to get the packages needed.

I've read the How-To you told me to, but I am not sure I understand it. After reading I still don't know where I am supposed to put the downloaded .deb packages. And the part it tells me about erasing packages from my UbuntuCD doesn't work, as the Ubuntu CD cannot be read in my OS for some reason (but it can be used on boot).

Have a more newbie-friendly tutorial?[/QUOTE]

That page requires you have an internet-enabled ubuntu installation.  You can ask someone on this page for a custom cd:

[https://wiki.ubuntu.com/forum/GiveAway](https://wiki.ubuntu.com/forum/GiveAway)

That was an effort to share the spirit and the software of Ubuntu over the Hollidays and it worked better than last year!

I guess those who posted on the page are still willing to mail out custom cds for free.  I still am....  Ask.

---

### Post by Protex on 2006-01-17
[QUOTE=azz]That page requires you have an internet-enabled ubuntu installation.  You can ask someone on this page for a custom cd:

[https://wiki.ubuntu.com/forum/GiveAway](https://wiki.ubuntu.com/forum/GiveAway)

That was an effort to share the spirit and the software of Ubuntu over the Hollidays and it worked better than last year!

I guess those who posted on the page are still willing to mail out custom cds for free.  I still am....  Ask.[/QUOTE]

I have an internet enabled Ubuntu on the system I am using now, to talk to you. But I do not know how to download the packages I want on my new system and include them on a CD.

Sorry for the trouble. =(

---

### Post by Protex on 2006-01-17
Aye.

I guess I'll go with one of the other mentioned OS's here.

Thanks anyway, but I think I'll stick with Ubuntu on my desktop, and that's it. =D

---

### Post by az on 2006-01-17
[QUOTE=Protex] I do not know how to download the packages I want on my new system and include them on a CD.
([/QUOTE]


When you install something with apt, it downloads it to /var/cache/apt/archives.  The packages stay there even after you install them.  Apt-move collects them and puts them into an archive format.

---

