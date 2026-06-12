---
title: "Qemu with the acceleration module"
date: 2005-12-02
forum: General Help
---

### Post by dmh-bidlah on 2005-12-02
Hi. I'm trying to compile qemu with the proprietary kqemu module, but unfortunately when chonfiguring I get this error:
```
ERROR: QEMU requires SDL or Cocoa for graphical output
```
So I thought that it's okay, I'll just install libsdl-dev.
But when doing ```
sudo apt-get install libsdl-dev
``` I get this error
```
The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
E: Broken packages
```
As I understand it is a problem with the repositories, yes?
Here is my /etc/apt/sources.list
```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## breezy-extras
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secundairy repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secundairy are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./

deb     http://people.debian.org/~daenzer/dri-trunk-sid/                ./

```
Thank you!

---

### Post by kairu0 on 2005-12-03
Try:

```
apt-get install libartsc0-dev
```

That error message doesn't necessarily mean that the libartsc0-dev package isn't available; it just means that it is required and you don't have it installed yet.

---

### Post by aysiu on 2005-12-03
Are you compiling qemu for some special reason? You don't like the version in the repositories?

---

### Post by dmh-bidlah on 2005-12-03
Thanks for the replies.
I'm compiling qemu myself to get the kqemu module support, AFAIK there is no other way to use the acceleration module. If there is, I would be glad to use it.
When I try to manually install libartsc0-dev i get
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libartsc0-dev: Depends: libartsc0 (= 1.4.3-0ubuntu1) but 1.4.92-0ubuntu1 is to be installed
E: Broken packages
```

---

### Post by adam.skinner on 2005-12-03
Here's the [Wiki HowTo]("https://wiki.ubuntu.com//WindowsXPUnderQemuHowTo").  You might try the [QVM86]("http://savannah.nongnu.org/projects/qvm86/"), as well.  It's the same as kqemu, but it only works on x86.

---

### Post by kairu0 on 2005-12-03
[QUOTE=dmh-bidlah]Thanks for the replies.
I'm compiling qemu myself to get the kqemu module support, AFAIK there is no other way to use the acceleration module. If there is, I would be glad to use it.
When I try to manually install libartsc0-dev i get
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libartsc0-dev: Depends: libartsc0 (= 1.4.3-0ubuntu1) but 1.4.92-0ubuntu1 is to be installed
E: Broken packages
```[/QUOTE]

Why don't you satisfy all those dependencies automagically by installing libartsc0-dev in synaptic?

---

### Post by dmh-bidlah on 2005-12-03
Synaptic does the same thing as apt-get. When I wan't to install either libsdl1.2-dev or libartsc0-dev i get an error. Only that Synaptic doesn't say what the error is. Could it possibly be a problem with the repositories themselves? 
Could any of you guys try to install either libartsc0-dev or libsdl-dev?

I need kqemu to run Win98 as a guest and not reboot the host which is actually acting as a server. It seems to me that the QVM86 is not as mature as kqemu, although I would gladly use it if possible, but from what I can understand it also requires qemu compilation.

EDIT: Disregard that, I just needed to force the version in Synaptic.

---

### Post by kairu0 on 2005-12-03
I can install both those packages in Synaptic with no errors. I am only using official repositories. Maybe you have added another repository that has a more current version of those packages?

---

