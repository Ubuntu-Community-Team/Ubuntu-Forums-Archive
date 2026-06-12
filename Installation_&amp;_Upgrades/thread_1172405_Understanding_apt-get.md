---
title: "Understanding apt-get"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by Mistoffeles on 2009-05-28
Coming from the RHEL/Fedora side, I am very accustomed to the easy and clean functionality of yum. I am used to being able to get a brief summary about a package by typing:

yum info packagename

or finding a package, or something included in a package, even when I don't have the exact name or even the package name at all using:

yum info partialname

or

yum provides somethingorother

This also allows me to make sure that I have both 32-bit and 64-bit libraries for something, in case I need them for whatever reason, and such reasons are not uncommon.

So how do I do these same things using apt-get?

For example I am looking for libpcap, and I can't for the life of me figure out what I need to do on Ubuntu server 9.04 to get it. I have already tried:

apt-get install libpcap

but this did not work. I know I have repository access as I have already installed emacs due to my extreme dislike of vi and variants of it.

---

### Post by SunnyRabbiera on 2009-05-28
Here is a decent page on the subject:

[http://aruljohn.com/info/apt/](http://aruljohn.com/info/apt/)

Personally I prefer apt over YUM

---

### Post by spiceminesofkessel on 2009-05-28
Try typing:
```
apt-cache show [packagename]
```

That gives you all information and dependencies for any package.

I would suggest you download the free e-book _Ubuntu Pocket Guide and Reference_ by Keir Thomas from [here]("http://www.ubuntupocketguide.com"). It has a chapter on software management and it explains the apt commands in decent detail.

---

### Post by sahabcse on 2009-05-28
Follow below url for package management in ubuntu

[http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html](http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html)

---

### Post by mcduck on 2009-05-28
"apt-cache search *something*" searches from packages
"apt-cache show *packagename*" prints information about the package

..and "sudo apt-get install/remove/update/upgrade/purge..." to actually do something with the packages.

---

### Post by kerry_s on 2009-05-28
create alias's for the commands to make your life easier.

```
alias !='sudo'
alias u='sudo apt-get update;sudo apt-get upgrade'
alias s='apt-cache search'
alias i='sudo apt-get install'
alias r='sudo apt-get remove --purge'
alias c='sudo apt-get clean'
alias ch='clear;history -c'
alias q='exit'
```

here's the "PS1=" that i use

```
PS1='\n	\e[0;34mApt-get\e[1;37m:: \e[1;33mu\e[0;32m=\e[1;37mupdate \e[1;33ms\e[0;32m=\e[1;37msearch \e[1;33mi\e[0;32m=\e[1;37minstall \e[1;33mr\e[0;32m=\e[1;37mremove \e[1;33mc\e[0;32m=\e[1;37mclean 
	\e[0;34mOther\e[1;37m:: \e[1;33mch\e[0;32m=\e[1;37mclear-history \e[1;33mq\e[0;32m=\e[1;37mexit 
\n[\e[0;31mCommand \e[1;37m@ \e[0;34m\w\e[1;37m]\n\e[0;32m>\e[1;37m '
```

---

