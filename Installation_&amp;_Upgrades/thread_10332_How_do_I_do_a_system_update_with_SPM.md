---
title: "How do I do a system update with SPM?"
date: 2005-01-06
forum: Installation &amp; Upgrades
---

### Post by mcollins on 2005-01-06
Hi you all,

I just installed Ubuntu 4.10. During the install it prompted me if I wanted to download updates online. I hit "no" because I needed to configure my D-Link bridge using a browser first. So everything is up and running now, and I want to do a basic system update using the SPM. I understand this won't update to newer versions of my applications, which is fine. If it works don't mess with it right? But I would like to update the important stuff (security and patches). In Windows it was called "Critical Updates". So here is where I'm at: Install CD is still in my drive. The Repository is on the default one, the CD ROM one. I was told all I had to do was click Reload (it always says "Downloading file 4 out of 4). Then click Mark All Upgrades, which didn't select any packages. And so the Apply button is still greyed out. I have a feeling I'm supposed to be in another Repository. I don't think it's getting anything online. The other Repositorys have a URL listed, this one says CD ROM: (Ubuntu 4.10 etc...
It seems like a basic task, but I couldn't fine any "how to's" on it
Thanks in advance.

Matt

---

### Post by rider343 on 2005-01-06
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe 



deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports-staging main universe 
deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-extras contrib universe 


deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) warty-extras-staging contrib universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty-updates main multiverse universe restricted

---

