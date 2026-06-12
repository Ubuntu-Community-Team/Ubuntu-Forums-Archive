---
title: "dependencies problems"
date: 2008-09-11
forum: General Help
---

### Post by xGutsAndGloryx on 2008-09-11
The following packages have unmet dependencies:
  lha: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu9 is to be installed


i am having dependencies problems. i don't understand what's going on? i already have it installed. is it only compatible with the 2.6.1 version of the software?

---

### Post by Pro-reason on 2008-09-11
This generally happens if the repositories are not up to date.  Just wait a while, then refresh the list (“Reload” in Synaptic, or “sudo apt-get update” on the command line) and try again.

It can also happen if you have enabled extra repositories which have conflicting versions of things.

---

### Post by dai_vernon on 2008-09-11
> **xGutsAndGloryx said:**
> The following packages have unmet dependencies:
  lha: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu9 is to be installed


i am having dependencies problems. i don't understand what's going on? i already have it installed. is it only compatible with the 2.6.1 version of the software?

yes, you need to install the newer version.

Go into Synaptic and click 'reload' 'mark all upgrades' - hopefully it will be there.

---

### Post by Pro-reason on 2008-09-11
> **dai_vernon said:**
> yes, you need to install the newer version.

Go into Synaptic and click 'reload' 'mark all upgrades' - hopefully it will be there.

No, the message that he got indicated that the newer version of libc6 was not available.

Looking at Synaptic on my computer, I can see that I have libc6 version 2.7-10ubuntu3 installed.

xGutsAndGloryx, please give us the output of “uname -a” and “cat /etc/lsb-release”.

---

### Post by Pro-reason on 2008-09-11
If all else fails, do this:

```

cd /var/cache/apt/archives/
sudo wget http://www.opensourcemirrors.org/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu3_i386.deb
sudo dpkg -i libc6_2.7-10ubuntu3_i386.deb

```

But try other solutions first.

---

### Post by xGutsAndGloryx on 2008-09-12
xgutsandgloryx@xgutsandgloryx-laptop:~$ uname -a
Linux xgutsandgloryx-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
xgutsandgloryx@xgutsandgloryx-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
xgutsandgloryx@xgutsandgloryx-laptop:~$

---

### Post by Pro-reason on 2008-09-12
> **xGutsAndGloryx said:**
> xgutsandgloryx@xgutsandgloryx-laptop:~$ uname -a
Linux xgutsandgloryx-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
xgutsandgloryx@xgutsandgloryx-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
xgutsandgloryx@xgutsandgloryx-laptop:~$

Ah, so you are using an old version of Ubuntu.  The current version of libc6 is not available for it.  You can force its installation with the commands I gave above, but there is no guarantee it won't cause conflicts.

I don't know why the *lha* package that you are trying to install requires a package which is not available for Ubuntu Gutsy Gibbon.  Are you installing it in the standard way?

---

### Post by Pro-reason on 2008-09-12
Looking at the list of dependencies for *lha*, I can see that the [Hardy]("http://packages.ubuntu.com/hardy/lha") version depends on version >= 2.7-1, but the [Gutsy]("http://packages.ubuntu.com/gutsy/lha") version depends on version >= 2.6-1.

This makes me think that you are trying to install the Hardy version, on Gutsy.

If you are installing via Synaptic, please post the contents of */etc/apt/sources.list*.

---

