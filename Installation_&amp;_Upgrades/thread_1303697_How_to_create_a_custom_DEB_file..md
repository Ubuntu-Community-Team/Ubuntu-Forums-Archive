---
title: "How to create a custom DEB file."
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by p2bc on 2009-10-28
Is there a way (pretty sure there must be) to create a custom DEB file with all it dependencies all rolled up in one handy little package.

[For the reason why please check here.](http://ubuntuforums.org/showthread.php?t=1278535)

I know there is a way to do it for Apps, to create a installer file with all its dependencies.

Well for what I want it for, Wicd that won't work since Wicd is a python script.

And for the record I did try creating a custom install ISO, but the thing is on install Ubuntu wants Network Manager to be present, and Wicd and Network Manager don't play well with each other. I have tried several times, the install just locks up each and every time it gets to the network installation.

So short of having to cripple the network each and every time I do an install, I would like a single DEB file the I can keep on a USB thumb drive and be sure Wicd will install problem free every time. I am suspecting I will need it soon with 9.10 coming out tomorrow.

:)

Thx for the assist.

---

### Post by p2bc on 2009-10-28
Let me also clarify. I am not using a TAR file or source code, so using "checkinstall" would not work, at least I don't think so.

I want to create the DEb file from what is already installed.

---

### Post by bribera on 2009-10-28
I'd read this article:

[http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/How-to-make-deb-packages/](http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/How-to-make-deb-packages/)

It's a good starting point, and has links to additional resources so you can dig deeper.

Hope that helps!

---

### Post by Wiebelhaus on 2009-10-28
The [information you seek]("https://wiki.ubuntu.com/PackagingGuide/Basic?action=show&redirect=HowToBuildDebianPackagesFromScratch") grasshoppa.

---

### Post by dv3500ea on 2009-10-28
You need to create a folder somewhere on your file system with the name of your .deb file. Inside this you would put a sort of virtual file system for where you want to put all of your files. eg. if you had an executable python file called wicd which you want to be a command, you would add a folder called usr inside the folder you created then a folder called bin inside this usr folder then your wicd file inside this. Basically you pretend this parent folder is the root directory of your file system. You also need to add a DEBIAN folder which contains control information. 

You need an file called control that contains information such as dependencies example:
```

     Package: hello
     Priority: optional
     Section: devel
     Installed-Size: 45
     Maintainer: Adam Heath <doogie@debian.org>
     Architecture: i386
     Version: 1.3-16
     Depends: libc6 (>= 2.1)
     Description: The classic greeting, and a good example
      The GNU hello program produces a familiar, friendly greeting.  It
      allows nonprogrammers to use a classic computer science tool which
      would otherwise be unavailable to them.
      .
      Seriously, though: this is an example of how to do a Debian package.
      It is the Debian version of the GNU Project's `hello world' program
      (which is itself an example for the GNU Project).


```
[URL="http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/"]
SEE HERE[/URL] for more comprehensive information.

---

### Post by vinutux on 2009-10-28
[Deb Creator ]("http://debcreator.cmsoft.net/")|  Graphical way 

**[http://debcreator.cmsoft.net/]("http://debcreator.cmsoft.net/")**

---

### Post by p2bc on 2009-10-28
Well thx all, I have some reading. Hopefully easier to understand than [Debian New Maintainer Guide]("http://www.debian.org/doc/maint-guide/"), I was going a little stir crazy by page 4. :)

---

### Post by vinutux on 2009-10-28
> **p2bc said:**
> Well thx all, I have some reading. Hopefully easier to understand than [Debian New Maintainer Guide]("http://www.debian.org/doc/maint-guide/"), I was going a little stir crazy by page 4. :)

well good luck...........

---

