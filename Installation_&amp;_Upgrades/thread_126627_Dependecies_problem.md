---
title: "Dependecies problem"
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by wizzkid on 2006-02-07
Hi!

I was trying to install the scim-chinese but i got unmet dependencies. i tryied to install scim and was successful but unusable :( its just not working.

Here's the result of installation:
wizz@wizzl:/etc/apt$ sudo apt-get install scim-chinese
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  scim-chinese: Depends: scim (>= 1.0.2) but it is not going to be installed
                Depends: scim (< 1.1) but it is not going to be installed
E: Broken packages
wizz@wizzl:/etc/apt$       


Here's my sources.list for reference

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy main restricted 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-updates main restricted 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy universe multiverse 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy universe multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team
## Official backports
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse  

## Security Updates
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe 

#KDE 3.5 Upgrade (Breezy)
deb [http://kubuntu.org/packages/kde35/](http://kubuntu.org/packages/kde35/) breezy main 

## PLF - [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free 
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free 

## Ubuntu China
deb [http://archive.ubuntu.org.cn/ubuntu-cn/](http://archive.ubuntu.org.cn/ubuntu-cn/) breezy main 



Hope you could help!

---

### Post by lol on 2006-02-07
Hi,

I am not sure this will solve your problem, but the current version of SCIM in Breezy is no good. You should try the following instead:

[LIST]
[*]Remove all currently SCIM related packages
[*]Add "deb-src [ftp://ftp.XX.debian.org/debian/](ftp://ftp.XX.debian.org/debian/) unstable main non-free contrib" to your /etc/apt/sources.list. Remplace XX by the mirror of your choice, i.e. [ftp://ftp.jp.debian.org/debian/](ftp://ftp.jp.debian.org/debian/) if you are in Japan.
[*]Try to run 'apt-build build-source scim'. You will get an error telling that the site is not authentified.
[*]run "gpg --keyserver wwwkeys.eu.pgp.net --recv-keys XXXXXXXX" where XXXXXXXX is the key of the server you are using (see the error message of the previous step)
[*]gpg --armor --export XXXXXXXX | sudo apt-key add -
[/LIST]

You can now use the Debian Sid source repository.

[LIST]
[*]sudo apt-build build-source scim scim-anthy
[*]Go into /var/cache/apt-build/repository and run 'sudo dpkg -i *.deb' to install all the packages
[/LIST]

(Taken from this thread:[http://www.ubuntuforums.org/showthread.php?t=59985](http://www.ubuntuforums.org/showthread.php?t=59985) )

Last thing: you may also have to run 'apt-build build-source scim-chinese' to build the chinese module, if it still exist in version 1.4 of SCIM (I don't know about that, I use SCIM for Japanese).
This whole process will upgrade SCIM to version 1.4 and may solve your dependency issue at the same time.

Good luck.

---

### Post by lol on 2006-02-07
you can also have a look at this thread:
[http://www.ubuntuforums.org/showthread.php?t=76985&highlight=scim+apt-build](http://www.ubuntuforums.org/showthread.php?t=76985&highlight=scim+apt-build)

---

### Post by wizzkid on 2006-02-08
Solved using FCITX chinese input server.

---

