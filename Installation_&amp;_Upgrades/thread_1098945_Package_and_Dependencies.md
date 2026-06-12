---
title: "Package and Dependencies"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by masterchief1995 on 2009-03-17
Hi I don't have an internet connection on my desktop but I do have an internet connection to a family desktop. When I install a program on ubuntu I always download the .deb package and install it using
```
sudo dpkg -i package_name.deb
```
I am fine with this but my problem is that the package usually required A LOT of dependencies. So I was wondering if there is a way to download a program with all of the dependencies packaged with it.

This would help me out a lot and save me so much time and frustration. Thanks in advance!:D

---

### Post by wylfing on 2009-03-17
The short answer to your question is Yes, it is possible to do this.

The process is not going to be fun, but after the first time through you'll probably do OK. I recommend installing the 'apt-doc' package and reading /usr/share/doc/apt-doc/offline.html for starters. (The 'apt-doc' package shouldn't require any dependencies you don't already have.)

HTH

---

### Post by manishtech on 2009-03-17
A simple way is to download the packages on the family desktop without installing it. When you hit Apply, there is a checkbox named "Download packages only".

Now use AptonCD to make an iso of offline repo, take it in your flash drive along with aptoncd.deb file.

Install this .deb file using this command. Now open aptoncd and choose restore and choose the iso you made. All the files will be restored to the apt cache of the system where you dont have net connection. Now try installing the main software, all dependencies will be selected automatically.

---

### Post by Partyboi2 on 2009-03-17
Another good program to install packages and all their dependencies for a offline machine is [[COLOR=Blue]Keryx[/COLOR]]("http://keryx.betaserver.org/")

---

### Post by masterchief1995 on 2009-03-18
I understand the keryx and never knew that existed but, the family computer is running windows XP and I can't convince them to at least dual boot. Also our linksys wireless adapter doesn't work with linux.
Thanks for keryx but is there anything for XP?:D

---

### Post by oldos2er on 2009-03-18
> **masterchief1995 said:**
> I understand the keryx and never knew that existed but, the family computer is running windows XP and I can't convince them to at least dual boot. Also our linksys wireless adapter doesn't work with linux.
Thanks for keryx but is there anything for XP?:D

 From the Keryx tutorial:

Because it is written in Python, and utilizes wxWidgets for it’s interface, Keryx can run on Linux, OSX and Windows. Pre-compiled binaries for Windows are included in the download

---

### Post by EXCiD3 on 2009-03-18
Keryx runs on ANY OS. You first run it on your offline machine, then you can use the Windows binary version to gather the updates. Give it a shot, I can help with any issues you've got with it since I made it. :)

---

### Post by masterchief1995 on 2009-03-19
I will try that

---

### Post by Bartender on 2009-03-22
It's taken me a few days to familiarize myself, but Keryx appears to be working for me.
Set it up on a thumb drive, created projects for two different Ubuntu 8.10 PC's, then took the thumb drive to a Windows PC with broadband and was able to get some packages.  Haven't tried to download to the Ubuntu PC's yet but expect it to work out.
If you want to use the Keryx GUI you need to install "python-wxversion" package to your Ubuntu PC.
  
There's also a project to include Keryx in the PortableApps suite.
[http://portableapps.com/node/18191](http://portableapps.com/node/18191)  
It's not quite ready for prime time yet, but close.

Keryx is a wonderful invention for those of us who've been beating our heads against the wall at home with dial-up, but have access to broadband somewhere else (school, library, work, etc.)

---

