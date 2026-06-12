---
title: "kernel upgrade question"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by towsonu2003 on 2005-12-22
Apt-get shows kernel is upgradable, but the linux-restricted-modules for that kernel are not. :confused:

I just don't want to download the update (dial up, 45MB, ~5 hours) just find out that it breaks the system in some way (or loose internet connectivity bc. my inmodem is stubborn) because the restricted modules were not upgraded :( 

Also, there is this thread: [http://ubuntuforums.org/showthread.php?p=596576#post596576](http://ubuntuforums.org/showthread.php?p=596576#post596576) , which suggests upgrading will cause problems. From that thread: [quote=city]The following packages have been kept back:
linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
I'm stuck[/quote]

Does anyone know anything about this? Anyone upgraded kernel (without linux-restricted-modules) as to the security announcement? Any comment appreciated...

---

### Post by towsonu2003 on 2005-12-23
bumping

---

### Post by az on 2005-12-23
Those are meta-packages.

Package: linux-restricted-modules-386 (2.6.12.16.1) [security] [restricted]Restricted Linux modules on 386.This package will always depend on the latest restricted modules available for 386. 

The actual package with the modules (linux-restricted-modules-2.6.12-10-386 (2.6.12.4-11.1)) will be upgraded.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=breezy&release=all)

So, linux-restricted-modules-386 depends on linux-restricted-modules-2.6.12-10-386 which is going from version 2.6.12.4-11.0 to version 2.6.12.4-11.1).  that does not affect linux-restricted-modules-386.

The only time linux-restricted-modules-386 would be changed is if there was a major change inthe kernel and inux-restricted-modules-2.6.12-10-386 went to 2.6.12-11 (which has already happened - breezy was released with a 2.6.12-9 kernel and the current kernel is 2.6.12-10.)

---

### Post by towsonu2003 on 2005-12-23
[QUOTE=azz]
The actual package with the modules (linux-restricted-modules-2.6.12-10-386 (2.6.12.4-11.1)) will be upgraded.
[/QUOTE]

If you did not write this, I was gonna assume everything was okay... But maybe not? Please correct me if I am misunderstanding, bc english is not my native language...

These package are the ones apt-get wants to upgrade: 
```

$  sudo apt-get -s upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  linux-headers-2.6.12-10 linux-headers-2.6.12-10-386
  linux-headers-2.6.12-10-686 linux-image-2.6.12-10-386
  linux-image-2.6.12-10-686
(...)
$

```

No modules being upgraded, at all. Is this supposed to happen? I am worried because I keep reading everywhere that if you change your kernel, you have to change your modules to match the new kernel...

If you need, here is my sources.list:
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
# deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

---

### Post by towsonu2003 on 2005-12-24
:-\" 

seeing that the number of kernel-problem-threads did not triple today (1 day after security release) I just upgraded and I am alive... Still don't understand it, but it seems my brain doesn't run linux ;)

I'm still wondering about this thread and the OP's problem though... ([http://ubuntuforums.org/showthread.php?p=596576#post596576](http://ubuntuforums.org/showthread.php?p=596576#post596576))

by the way, thanks azz, I really benefit from your responses and your santa hat.

---

### Post by BobSongs on 2005-12-24
I've noticed, since the last kernel upgrade, that getting to the desktop is taking a LOT longer than usual. Anyone else encountering this?

EDIT: Here's something I didn't add but thought I'd note for other users. Before the kernel upgrade I followed the HowTo to replace Metacity with XFCE. XFCE as a window manager is pretty cool. But as long as it was the window manager the boot was horribly slow.

Once I restored it to Metacity the boot returned to normal speed.

---

