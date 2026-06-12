---
title: "'server' install using instlux and grub4dos"
date: 2005-12-17
forum: Installation &amp; Upgrades
---

### Post by timknauf on 2005-12-17
Hi everyone!

I'm attempting to do a server install of Breezy on an old laptop (a Toshiba Portege 3020ct). It has a PCMCIA CD drive, and there's no way to make the BIOS boot from CD. Even Smart Boot Manager is unable to recognise my CD drive.

Fortunately, last night, I was able to install Ubuntu using [Instlux]("http://www.sourceforge.net/projects/instlux"), as mentioned in the [InstallationFromWindows wiki]("https://wiki.ubuntu.com/Installation/FromWindows"). Since Instlux is designed for 2000/XP, and I have a 9x system, then booted to DOS and used [Grub4DOS]("http://grub4dos.sourceforge.net/") to boot the installer.

Everything went great from there - the installer found and used the drive no problem. Unfortunately, when I tried to use my system, I found that the computer was far too underpowered for the full Ubuntu experience (damn!).

I'd now like to try setting up Xubuntu, as detailed in the [InstallingUbuntu wiki]("https://wiki.ubuntu.com/InstallingXubuntu"). I would like to start with a server installation, as is recommended (in frustration, I must admit that I wiped my ext3 partitions last night, so I'll be starting again).

I can't for the life of me work out how to start a server installation, though! I don't get the normal prompt, like this:[IMG]http://shots.osdir.com/slideshows/517/1.gif[/IMG].

Instead, I go straight into the installer, like this: [IMG]http://shots.osdir.com/slideshows/517/2.gif[/IMG].

Is there some extra command I need to give to Grub? Something I need to put in my menu.lst file in order to indicate that I want a server install?

Thanks in advance, folks. It looks like a good community here.

---

