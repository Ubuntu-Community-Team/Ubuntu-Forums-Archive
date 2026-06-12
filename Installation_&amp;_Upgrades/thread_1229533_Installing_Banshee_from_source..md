---
title: "Installing Banshee from source."
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-08-02
This is what I get after I 'make' while installing banshee from sources.

```
de@RESEARCHGAMER:~/Desktop/banshee-1-1.4.3$ make
make  all-recursive
make[1]: Entering directory `/home/de/Desktop/banshee-1-1.4.3'
Making all in build
make[2]: Entering directory `/home/de/Desktop/banshee-1-1.4.3/build'
Making all in pkg-config
make[3]: Entering directory `/home/de/Desktop/banshee-1-1.4.3/build/pkg-config'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/de/Desktop/banshee-1-1.4.3/build/pkg-config'
Making all in m4
make[3]: Entering directory `/home/de/Desktop/banshee-1-1.4.3/build/m4'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/de/Desktop/banshee-1-1.4.3/build/m4'
make[3]: Entering directory `/home/de/Desktop/banshee-1-1.4.3/build'
no -out:gconf-schema-extractor.exe GConfSchemaExtractor.cs
/bin/bash: no: command not found
make[3]: *** [gconf-schema-extractor.exe] Error 127
make[3]: Leaving directory `/home/de/Desktop/banshee-1-1.4.3/build'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/de/Desktop/banshee-1-1.4.3/build'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/de/Desktop/banshee-1-1.4.3'
make: *** [all] Error 2
de@RESEARCHGAMER:~/Desktop/banshee-1-1.4.3$ 

```

Any ideas what's happening?

---

### Post by Sef on 2009-08-02
If you want to keep up with Banshee, here's its [PPA]("https://launchpad.net/%7Ebanshee-team/+archive/ppa").

---

### Post by dE_logics on 2009-08-02
I was wondering about compiling from source...

---

### Post by dlmarti on 2009-08-02
> /bin/bash: no: command not found

The command "no" was not found.

Never heard of this command, I would contact the banshee guys.

---

### Post by Partyboi2 on 2009-08-02
Hi, try installing the  mono-gmcs and mono-mcs packages and see if it works.

---

### Post by dE_logics on 2009-08-02
> **dlmarti said:**
> The command "no" was not found.

Never heard of this command, I would contact the banshee guys.

And what's that exe file above?

[QUOTE=Partyboi2]Hi, try installing the mono-gmcs and mono-mcs packages and see if it works.[/QUOTE]

They are not in the intrepid repos...I have to add Jaunty repos for them?

---

### Post by directhex on 2009-08-02
Intrepid, try mono-2.0-devel.

---

### Post by Partyboi2 on 2009-08-02
> **dE_logics said:**
> And what's that exe file above?



They are not in the intrepid repos...I have to add Jaunty repos for them?
They are in the intrepid repos, so you do not need to add Jaunty repos (which can cause breakages), make sure you have all the required repos enabled in Software Sources.

---

### Post by dE_logics on 2009-08-03
[QUOTE=Partyboi2]They are in the intrepid repos, so you do not need to add Jaunty repos (which can cause breakages), make sure you have all the required repos enabled in Software Sources.[/QUOTE]

I have mono-smcs as the closest match...no mono-gmcs or mono-mcs. Yes, I have the intrepid repos enabled.

[QUOTE=directhex]Intrepid, try mono-2.0-devel.[/QUOTE]

I have mono-tools-dlevel but no mono-2.0-devel

---

### Post by slakkie on 2009-08-03
apt-get build-dep banshee

---

### Post by directhex on 2009-08-03
> **dE_logics said:**
> I have mono-tools-dlevel but no mono-2.0-devel

Well that's lovely for you, but why would I have said it if it wasn't what I meant?

Your error is caused by a glitch in the upstream configure script.

It checks for a compiler, and displays output like this:
```
Checking for gmcs... no
```

It displays this because you don't have the compiler installed. However, instead of bailing out (as it should) it literally uses "no" as the compiler command.

As others have said, apt-get build-dep will take care of the build dependencies for the version of the package in your repository - which is usually close enough to the version you want to build.

---

### Post by dE_logics on 2009-08-03
> **slakkie said:**
> apt-get build-dep banshee

```
E: Build-Depends dependency for banshee cannot be satisfied because no available versions of package cli-common-dev can satisfy version requirements
```

---

### Post by dE_logics on 2009-08-03
> **directhex said:**
> Well that's lovely for you, but why would I have said it if it wasn't what I meant?

Your error is caused by a glitch in the upstream configure script.

It checks for a compiler, and displays output like this:
```
Checking for gmcs... no
```

It displays this because you don't have the compiler installed. However, instead of bailing out (as it should) it literally uses "no" as the compiler command.

As others have said, apt-get build-dep will take care of the build dependencies for the version of the package in your repository - which is usually close enough to the version you want to build.

You're right...no GMCS installed.

I'll install it and retry.

---

### Post by dE_logics on 2009-08-03
GMCS is not in the repos.

To give a generalization, nothing is in the repos.

---

### Post by directhex on 2009-08-03
> **dE_logics said:**
> GMCS is not in the repos.

To give a generalization, nothing is in the repos.

Your repos are broken then.

[http://packages.ubuntu.com/intrepid/mono-gmcs](http://packages.ubuntu.com/intrepid/mono-gmcs)

---

### Post by Partyboi2 on 2009-08-03
> **dE_logics said:**
> GMCS is not in the repos.

To give a generalization, nothing is in the repos.
Can you also post your sources.list as well so we can see if they are the cause of why you cannot install these packages.
```
cat /etc/apt/sources.list
```

---

### Post by dE_logics on 2009-08-03
```
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://dl.google.com/linux/deb/ stable non-free
# deb-src ftp://ftp2.fr.debian.org/debian/ stable main
# deb ftp://ftp.nerim.net/debian-marillat/ etch main
# deb ftp://sunsite.dk/mirrors/java-linux/debian/ sarge non-free
# deb ftp://ftp.debian.org/debian testing main contrib non-free
# deb http://security.debian.org/ sarge/updates main
# deb ftp://ftp.nerim.net/debian-marillat/ sarge main
# deb ftp://ftp.debian.org/debian unstable main contrib non-free
# deb http://security.debian.org/ stable/updates main
# deb ftp://ftp.debian.org/debian testing main contrib non-free
# deb ftp://ftp.nerim.net/debian-marillat/ etch main
# deb ftp://ftp.nerim.net/debian-marillat/ testing main
# deb ftp://ftp.nerim.net/debian-marillat/ unstable main
# deb ftp://ftp.tux.org/java/debian/ unstable non-free
# deb ftp://sunsite.dk/mirrors/java-linux/debian/ testing non-free
# deb http://pkg-kde.alioth.debian.org/kde-3.4.0/ ./
# deb ftp://ftp.nerim.net/debian-marillat/ etch main
# deb ftp://ftp.nerim.net/debian-marillat/ sid main
# deb http://ftp.debian.org/debian/ etch main
# deb http://security.debian.org/ etch/updates main contrib
# deb-src http://security.debian.org/ etch/updates main contrib
# deb http://debian.uchicago.edu/debian/ etch main contrib non-free
# deb-src http://debian.uchicago.edu/debian/ etch main contrib non-free
# deb http://www.debian-multimedia.org etch main
# deb http://www.debian-multimedia.org stable main
# deb-src http://www.debian-multimedia.org/ etch main
# deb http://ftp.us.debian.org/debian stable main contrib non-free
# deb-src http://ftp.us.debian.org/debian stable main contrib non-free
# deb http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
# deb-src http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
# deb http://ftp.debian-unofficial.org/debian stable main contrib non-free restricted
# deb-src http://ftp.debian-unofficial.org/debian stable main contrib non-free restricted
# deb http://ftp.us.debian.org/debian testing main contrib non-free
# deb-src http://ftp.us.debian.org/debian testing main contrib non-free
# deb http://security.debian.org testing/updates main contrib non-free
# deb-src http://security.debian.org testing/updates main contrib non-free
# deb http://non-us.debian.org/debian-non-US testing/non-US main contrib non-free
# deb http://ftp.debian.org/debian/ sid main contrib non-free
# deb http://ftp.us.debian.org/debian/ experimental main contrib non-free
# deb http://www.debian-multimedia.org experimental main
# deb http://gulus.usherbrooke.ca/debian-unofficial/ etch main contrib non-free restricted
# deb-src http://mentors.debian.net/debian unstable main contrib non-free
# deb http://mirror.noreply.org/pub/tor etch main
# deb-src http://mirror.noreply.org/pub/tor etch main
# deb http://www.backports.org/debian etch-backports main
# deb http://www.kiberpipa.org/~minmax/cin...ilds/pentium4/ ./
# deb-src http://mentors.debian.net/debian unstable main contrib non-free
# deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
```

Yeah I know, I added lots of other repos long ago.

---

### Post by Partyboi2 on 2009-08-03
Open a terminal and open your sources.list
```
gksu gedit /etc/apt/sources.list
```
add this line to the bottom of the file
```
deb http://archive.ubuntu.com/ubuntu/ intrepid main
```
also put a # infront of the cdrom line
```
[COLOR=Red]#[/COLOR]deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted

```
then save the changes and back in the terminal
```
sudo apt-get update
sudo apt-get install  mono-gmcs  mono-mcs
```

---

### Post by slakkie on 2009-08-03
> **dE_logics said:**
> ```
E: Build-Depends dependency for banshee cannot be satisfied because no available versions of package cli-common-dev can satisfy version requirements
```

I dont run 8.10, but have a look here:

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=cli-common-dev](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=cli-common-dev)

---

### Post by dE_logics on 2009-08-03
I installed that gcms package manually...and it compiled...thanks every one.

> **Partyboi2 said:**
> 
```
[COLOR=Red]#[/COLOR]deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted

```

Thanks, but I would preferred that Cdrom added to the repos.

---

### Post by slakkie on 2009-08-03
Why? You have all the up to date repo's online..

---

### Post by Partyboi2 on 2009-08-03
> **dE_logics said:**
> I installed that gcms package manually...and it compiled...thanks every one.



Thanks, but I would preferred that Cdrom added to the repos.
Well that is your choice. Just remember for the future that if you try to install packages that complain of missing dependencies its more then likely because you have your cdrom enabled as a repo. :)

---

