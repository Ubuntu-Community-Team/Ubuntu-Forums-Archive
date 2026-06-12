---
title: "Install in Toshiba Satellite A60."
date: 2014-09-19
forum: Hardware
---

### Post by negora on 2014-09-19
Hello:

I've had a hard time installing Xubuntu 14.04 in a Toshiba Satellite A60 laptop. So hard that I have been unable to do it and I've had to "install" it from a disk image, taken from a virtual machine, using Clonezilla. SquashFS reported errors everytime that I used the installer, regardless the used media (DVD, USB or ISO file).

Now the problem is that it throws several segmentation faults while I'm using it. The RAM module has just been replaced because it was faulty. The hard disk has been replaced two days ago because it had started to fail too. So the new parts are OK. I've tested them with Memtest86+ and Smart Tools and fsck respectively, just in case... The buit-in RAM module hasn't errors either. So I can't understand why it's failing now :/ .

I remember that I had similar problems in the past, with previous versions of Xubuntu, Kubuntu, etc. But, since I've replaced that parts, I can't be sure if that problems had the same origin or were totally different.

The computer has been working with Windows 7 for the last months. It hasn't reported any error nor it has shown the typical blue screens. But I haven't tested the laptop with it as much as with Xubuntu, so I don't know if it's just a coincidence... Could it be that the drivers in Linux have some old and unresolved problems with specific parts of this hardware?

Thank you.

---

### Post by sudodus on 2014-09-22
After two days I found your thread without a reply, so I'll try to help you get started. I have a Toshiba and my daughter has one, and they work well with Xubuntu for us, but they are newer, from 2010 with core2duo and from 2013 with Intel i5 processors.

I saw the specs via the internet, but I guess and hope you have more RAM, than shown there (256 MB). Xubuntu needs 1 GB RAM to work well, and Lubuntu needs 512 MB to work well, but also to install from a desktop iso file.

For an old computer it is a good idea to start with an older but still supported version of Ubuntu or flavour of Ubuntu or a community re-spin. Some drivers in 14.04 LTS have dropped support for old hardware. ***So I recommend 12.04 LTS***. Unfortunately Xubuntu 12.04 LTS end of life is April 2015 (only 7 months to go). You can try it, and then opt for changing to something else, but I suggest that you try several iso files based on Ubuntu 12.04:

for example Bento, Bodhi, LXLE, Linux Mint 13, which promise support until April 2017.

Another alternative is *kansasnoob*'s [Precise Gnome Classic Tweaks]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks"), that I have made work in an older computer (with a Pentium II cpu at 400 MHz and 192 MB RAM). That installation was done with the [One Button Installer]("https://help.ubuntu.com/community/OBI"), which needs less RAM than the conventional installers. Another light-weight alternative is the Lubuntu alternate iso file, but it can only install Lubuntu 14.04 LTS. (Lubuntu 12.04 had no long time support, it has passed end of life). Precise Gnome Classic Tweaks is not really useful for real tasks in that old computer, but it works :-P

Soon [ToriOS]("http://torios.org/") will be released. It is made for old computers and the first version is based on Ubuntu 12.04 LTS.

-o-

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

See also

[Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

