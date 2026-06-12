---
title: "Ubuntu Kickstart Documentation"
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by adelcambre on 2006-01-16
My organization is beginning the transition process from Centos Linux to Ubuntu.  

It is required that we are able to do unattended installs with the ubuntu kickstart system.  There appears to be virtually zero documentation on what options are available in the kickstart on ubuntu.  When using the mini.iso to kickstart our test box, it ignores the nfs line, and installs using http from archive.ubuntu.com rather than our local mirror.  It seems most of what we put in the post install doesnt work.  

What would really help is documentation on what is possible and what isnt.  We are flying blind and most things we try dont work. 

Thanks.

---

### Post by adelcambre on 2006-01-17
I emailed the installer maintainer and found the docs.  In case someone else is looking, I figured I would post it here as well.

The link has also been added to the wiki page.

[http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s06.html#id2519042](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s06.html#id2519042)

---

### Post by Robert Citek on 2006-01-31
[QUOTE=adelcambre]I emailed the installer maintainer and found the docs.  In case someone else is looking, I figured I would post it here as well.

The link has also been added to the wiki page.

[http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s06.html#id2519042](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s06.html#id2519042)[/QUOTE]

Thanks, adelcambre.  I thought I'd post my ks.cfg and instructions as a sample for others:

1) insert the Ubuntu 5.10 CD into the CD-ROM
2) at the boot prompt, type:
```
linux ks=http://cwelug.org/~rwcitek/ubuntu/ks.cfg
```
The ks.cfg file contains this:
```
install
cdrom
lang en_US.UTF-8
langsupport --default en_US.UTF-8 en_US.UTF-8
keyboard us
mouse none
skipx
network --device eth0 --bootproto dhcp
rootpw 123456
firewall --disabled
selinux --disabled
authconfig --enableshadow --enablemd5
timezone US/Central
bootloader --location=mbr

clearpart --all --drives=hda
part /boot --fstype ext3 --size=200 --ondisk=hda
part / --fstype ext3 --size=1024 --grow --ondisk=hda
part swap --size=96 --grow --maxsize=2000 --ondisk=hda
reboot

%packages
@Base

%post
```

Apparently @Base doesn't mean the same thing under Ubuntu as it does under RedHat or CentOS.  Anyone have hints on how to do a minimal install?

I'm also working on getting Ubuntu installed over the net using Knoppix, but haven't had as much luck.  Here are my notes so far:

[http://www.cwelug.org/cgi-bin/wiki.cgi?Ubuntu_5.10](http://www.cwelug.org/cgi-bin/wiki.cgi?Ubuntu_5.10)

Regards,
- Robert
[http://www.cwelug.org/](http://www.cwelug.org/)

---

### Post by de_doughboy on 2006-01-31
Here is the link to Chris's article about doing a minimal RAM system install. I found it very useful despite being dated. The real trick is to get to root prompt so that you can run individual install commands or scripts. I am not too keen on using the automatic menu install procedure because they usually fall over somewhere along the way. The scripts given above rely on the fact that you already have an Internet connection, but what if you don't?

If all else fails you might want to try creating the GO LIVE -CD first. I found that it is very straight forward and has worked for all my legacy PCs. Once you have Ubuntu running with go live you can walk around the system and view the user manual and documents.  Don't forget to read all the documents like the quick start guide to get a feel for the common attributes and menu features. 

Here is what I did to kickstart my P1 as a minimal RAM file server using the install CD, not GO LIVE:
1) After downloading the iso file. Use Nero-Express to create a  Breezy-installCD. That is a one step process that either works or doesn't from a windows PC. 

2) You may have to change the bios settings to boot from CD-ROM if that has not been done before get technical help to change the settings.

3) Plug in your network DSL cable or LAN!! Else it won't be detected.

4) Once the Ubuntu splash screens come up and you get the boot>  prompt
asking you to press enter. Key in the following

boot>server mem=256M 
5) Enter your server's PC ID name. What you are going to call it?
Some folks keep with the code names to know which servers are running what. Like "BreezyP1", etc. 

6. Follow the install menu until you get to the user console >$ then follow Chris's outline.

Some legacy PCs will fork when you try to load all the software packages, even if you have a big HD. Usually they hang during the configuration process or installing remaining packages to disks. 

 
de.doughboy \\:D/

---

### Post by UbuWu on 2006-01-31
[QUOTE=adelcambre]
What would really help is documentation on what is possible and what isnt.  We are flying blind and most things we try dont work. 
[/QUOTE]

Did you know about the gui program system-config-kickstart that is installable through synaptic?

---

### Post by de_doughboy on 2006-01-31
It's mostly trial an error on this end too. After some testing I finally realized that USB drives
mounting occurs automatically.  I just plugged in my thumb drive, and was surprised by
ICON popping up on my splash mat. It would have been nice to know that ahead of time
then I could have skipped burning a new the CD, and just booted off the
the HD or lapmate. If you have a portable drive plug it in and  just sit back, and then 
watch the partitions pop in no need to flush around trying to mount It. :cool:
Perhaps a features document would help us out. I read the release notes and they didn't say anything about this. So give me a clue about how to use the synaptic? I can't find that in the user manual either, but I found INITSCRIPT. Is it cool like that? :cool:

---

### Post by de_doughboy on 2006-02-01
I've found these two sites to be very useful too for help with geting past Linux boot script problems

HOW 2 to Mount a FS ....
[http://www.freeos.com/articles/4491/](http://www.freeos.com/articles/4491/)


HOW 2 BUILD LINUX ON 2MB
Linux documentation Project.html
[http://en.tldp.org/HOWTO/4mb-Laptops.html](http://en.tldp.org/HOWTO/4mb-Laptops.html)

Are there any others you know about for my tool box? 

Oh yes these came from IT Toolbox website.\\:D/

---

