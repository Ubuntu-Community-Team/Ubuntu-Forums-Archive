---
title: "How to upgrade 6.06.2 LTS to 8.04.1 LTS server w/o net access?"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by baekgaard on 2009-01-09
I have a server without network access (and no X/GUI) that I want to upgrade from 6.06.2 LTS to 8.04.1 LTS.

I thought this would be the simplest thing in the world, but alas -- no ;-(:confused:

Mounting the cdrom and trying to run the upgrade (sh /cdrom/cdromupgrade) causes an error as the apt module cannot be imported into python. Apparently that part of python never was installed on this particular server/version?

How can this be done?

Can I simply add the cdrom to the apt/sources.list file and run a dist-upgrade? Or am I without any luck now?


-- Per.

(There is a slightly longer but perfectly valid explanation on why the server is without network access -- short version is that a disk copy is running on a newer machine where the network card appears not supported by 6.06, in case someone wonders).

---

### Post by Liviu-Theodor on 2009-01-09
I understand why you want to upgrade from CD, but it seems you have two ways: one to fresh install the Ubuntu Server 8.04.1, the other to use the Alternate CD to upgrade, as described here, [https://help.ubuntu.com/community/HardyUpgrades]("https://help.ubuntu.com/community/HardyUpgrades"). Maybe you used another cd, and this is the reason for the errors?

---

### Post by baekgaard on 2009-01-09
Thanks for commenting.

> **Liviu-Theodor said:**
> I understand ... use the Alternate CD to upgrade, as described here,[ https://help.ubuntu.com/community/HardyUpgrades]("https://help.ubuntu.com/community/HardyUpgrades"). Maybe you used another cd, and this is the reason for the errors?

That is what I'm doing, using the ubuntu-8.04.1-alternate-i386.iso image.

That link you quote says to use gksu (or the equivalent kde thing), but since it is a server install with no gnome nor kde or even an X server, obviously it should be done with a sudo or as root instead.

Hence, I'm just logging in as root, mount the alternate cdrom and run the cdromupgrade. This is what I get on my screen:

# mount /dev/cdrom /cdrom -o ro
# sh /cdrom/cdromupgrade
Traceback (most recent call last):
  File "/tmp/tmp.6ojVS4/hardy", line 3, in ?
    from DistUpgradeController import DistUpgradeController
  File "/tmp/tmp.6ojVS4/DistUpgradeController.py", line 25, in ?
    import apt
ImportError: No module named apt
#

It obviously makes no difference whether I type sudo or sh when running as root.

There is no apt module in /usr/lib/python2.4, which is where it should be, I guess.

So since it is broken to do via the cdromupgrade, the question is if there would be another way (such as changing the repository to hardy in /etc/apt/sources.list and running a apt-get distupgrade or something...)?

Or some way of fixing the problem easily, like installing an additional package or fixing the issue otherwise?


-- Per.

---

### Post by baekgaard on 2009-01-09
[Duplicate posting removed, caused by server "POST error" problem]

---

### Post by baekgaard on 2009-01-09
Hm... I ventured to install a couple of packages (xfer via USB from another PC: python-apt, python2.4-apt and also later on python-gnupginterface) and ran the upgrade process again.

After a while it did: "Calculating the changes" and came up with a segfailt:

/cdrom/cdromupgrade: line 32: 5584 Segmentation Fault $TMPDIR/$CONDENAME -- cdrom "$cddirname".

Not sure what to do now ;-( not exactly what I had expected when upgrading from one LTS to another.

:confused:


-- Per.

---

