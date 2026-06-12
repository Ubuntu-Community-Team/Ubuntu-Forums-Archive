---
title: "VPS Ubuntu 8.04 Installation Didnt Come With APT"
date: 2008-10-31
forum: General Help
---

### Post by decivox on 2008-10-31
Hello,

I am new to linux and am in college for networking and stuff.  I am taking alot of networking courses and linux courses as a part of my program.  I just got a VPS to practice my linux skills and to try to host a web page and a game server.

When I try to install apache, or anything with apt-get it says command not found.  I checked my bin directory and there is no apt, and there are no apt folders for the repositories and stuff.

How can I install apt myself?  I am guessing since the Ubuntu installation was called Ubuntu 8.04 minimal, it didnt come with apt; which is silly because it seems it is a very useful tool.

I have been looking for a package to downlaod but i cant find one, or anything to a ".exe" equivalent (sorry i am much more familiar with windows.  I am not sure where to look tho and am hoping something is out there.

My linux prof says one good thing about linux is that it has an awesome community, so I decided to ask here.

Thanks in advance for all your help.

---

### Post by dasunsrule32 on 2008-10-31
Do you have dpkg and wget installed?

---

### Post by decivox on 2008-10-31
> **dasunsrule32 said:**
> Do you have dpkg and wget installed?

I have wget but not dpkg.

---

### Post by dasunsrule32 on 2008-10-31
[VPS Forum link](http://forums.vpslink.com/announcements/5341-os-template-updates-documentation.html)

> 
 We are in the process of rolling out new OpenVZ OS templates for all major distributions.

Package management utilities for updated templates on the following distributions will include a local repository (see below) by default to provide the fastest-possible download speeds:

    * CentOS - [http://mirror.vpslink.com/centos/](http://mirror.vpslink.com/centos/)
    * Debian - [http://debrepo.mirror.vpslink.com/debian/](http://debrepo.mirror.vpslink.com/debian/)
    * Fedora - [http://mirror.vpslink.com/fedora/](http://mirror.vpslink.com/fedora/)
    * Ubuntu - [http://mirror.vpslink.com/ubuntu/](http://mirror.vpslink.com/ubuntu/)


In addition to providing the latest packages and improved package management performance, we are also publishing our documentation for VPSLink OS templates - including lists of all installed packages and packages which have changed between template updates:

    * Arch Linux
    * CentOS 5.2
    * Debian 4.0
    * Fedora 8
    * Fedora 9
    * OpenSUSE
    * Ubuntu 7.04
    * Ubuntu 7.10
    * Ubuntu 8.04


The OS Template Information pages will be updated whenever we publish OS template changes.

We will add documentation for our Gentoo, Slackware, and Xen OS templates as updates are completed.
Reply With Quote
  #2 (permalink)  
Old 10-09-2008, 04:51 AM
DanL@VPSLink DanL@VPSLink is online now
Administrator
	  	
Join Date: Dec 2007
Posts: 536
Default
Note: If you are using a default installation of CentOS, Debian, Fedora, or Ubuntu and you would like to update your package manager to use the VPSLink repositories, here are several find/replace shortcuts (again, these will require that you be using the default package manager configuration):

CentOS and Fedora
Code:

sed -i -e's/^mirrorlist/#mirrorlist/' /etc/yum.repos.d/*
sed -i -e's/\/pub\/fedora\/linux\/releases/\/fedora/' /etc/yum.repos.d/*
sed -i -e's/^#?baseurl=http:\/\/[^\/]\+/baseurl=http://mirror.vpslink.com/' /etc/yum.repos.d/*

Debian and Ubuntu
Code:

sed -i -e's/http:\/\/[^\/]\+\/ubuntu/http:\/\/mirror.vpslink.com\/ubuntu/' /etc/apt/sources.list
sed -i -e's/http:\/\/[^\/]\+\/debian/http:\/\/debrepo.mirror.vpslink.com\/debian/' /etc/apt/sources.list



Looks like they have their own repos that they are using. You can add package management tools by looking at this post on their forums.

---

### Post by decivox on 2008-10-31
Thanks for the fast responses, but I am not sure exactly what you want me to do with all of that.  Am I just supposted to run the ubuntu command at the bottom? Because even if I do that I still dont have the apt program, or binary i guess its called.  Or on those mirror lists is it hosted there somewhere?

---

### Post by decivox on 2008-10-31
Ok so I did some looking and saw taht I had yum, so I guess they imaged my VPS with the wrong distro.  Thanks for the help tho guys

---

### Post by dasunsrule32 on 2008-10-31
> **decivox said:**
> Thanks for the fast responses, but I am not sure exactly what you want me to do with all of that.  Am I just supposted to run the ubuntu command at the bottom? Because even if I do that I still dont have the apt program, or binary i guess its called.  Or on those mirror lists is it hosted there somewhere?

You will have to follow the Ubuntu directions on their forums for their repos they are using. If you notice on the second to last command, it has it getting your apt/sources.list file. It is setting up your repos for you. So you will need to do that to get it going.

Either that, or download the unmodified Server edition of Ubuntu from ubuntu.com. That has the apt tools in it.

They are not using deb packages in their version. It appears they are using a binary installer, when looking in the repos, or even yum for that matter. I am not sure exactly what they have going on. You may want to check their forums a bit more.

If you absolutely need apt, you will need to download the packages for dpkg from debian.org, search for packages. It may be a bit tricky getting it setup, you may have a lot of manual installation. Then you will need to install apt after that.

---

### Post by dasunsrule32 on 2008-10-31
> **decivox said:**
> Ok so I did some looking and saw taht I had yum, so I guess they imaged my VPS with the wrong distro.  Thanks for the help tho guys

No, I looked at their repos, everything is using yum. They modified it that way.

---

