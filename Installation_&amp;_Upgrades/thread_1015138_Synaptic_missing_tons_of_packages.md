---
title: "Synaptic missing tons of packages"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by noahsatellite on 2008-12-18
I haven't been able to use Synaptic recently since it seems to be missing packages.  For instance, if I run:

```
sudo apt-get install rar
```

Then rar gets installed on my machine.  But if I search Synaptic for rar, it finds nothing.  This is just one of many, many packages that I want to install and Synaptic doesn't "see".  I've had to manually use apt-get instead.  The weirdest part is that I have the exact same installation on my laptop and everything works fine there.  I've tried running a Reload command in Synaptic (upper left hand corner) but that didn't help.

Any ideas?

Thanks,
Noah

---

### Post by jenkinbr on 2008-12-18
How are you searching for 'rar' in synaptic.

I've found the search feature added to the toolbar to be slightly buggy.  You may want to try using the more advanced search found by clicking the search button.  Make sure you set this so it searches descriptions and package names.

---

### Post by taurus on 2008-12-18
Which release are you running?

```
lsb_release -a
```

---

### Post by SunnyRabbiera on 2008-12-18
also for rar you may need to add the universal repositories.

---

### Post by jenkinbr on 2008-12-18
> **SunnyRabbiera said:**
> also for rar you may need to add the universal repositories.
rar is multiverse >>[http://packages.ubuntu.com/intrepid/rar](http://packages.ubuntu.com/intrepid/rar)

---

### Post by noahsatellite on 2008-12-18
**jenkinbr** - I've tried this to no avail

**taurus** - I'm running Ubuntu 8.10.

**SunnyRabbiera** - rar is just an example.  Other examples include: filezilla, comipizconfig-settings-manager, and lots of other stuff that the Synaptic on my laptop has no trouble seeing (and apt-get on this machine sees too).

Noah

---

### Post by oldos2er on 2008-12-18
Can you please post the output of "cat /etc/apt/sources.list"?

---

### Post by SuperSonic4 on 2008-12-18
apt and synaptic both refer to the same file.

I suspect it will be because Synpatic is set to show certain packages along due to a search filter

---

### Post by noahsatellite on 2008-12-18
without the comments:

```
deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

deb http://archive.canonical.com/ubuntu intrepid partner

deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-security multiverse
```

---

### Post by jpeterse on 2009-01-11
Hi

I have the same problem on my end.
I re-installed Ubuntu yesterday - a fresh install.
Before the reinstall Synaptic worked well, even the quick search worked well.

Now, it can't find a ton packages. Search for XEN (or "xen") comes back blank.

The problem is described in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797)

Run the command "sudo update-apt-xapian-index" in a terminal, and the index  the quick search is using is updated. (you may need to run this command again, if you add new repositories)

---

### Post by raul999 on 2009-01-31
Hi,
I had the same problem with Synaptic search and i fixed it the command.
Thanks a lot

---

### Post by Hiker Hauk on 2009-02-20
If
```
$ sudo update-apt-xapian-index
```has no effect,

completely update the package lists from a source, then

```
$ sudo rm -fr /var/lib/apt-xapian-index
$ sudo update-apt-xapian-index
```

---

### Post by chensamurai on 2009-04-15
> **noahsatellite said:**
> I haven't been able to use Synaptic recently since it seems to be missing packages.  For instance, if I run:

```
sudo apt-get install rar
```

Then rar gets installed on my machine.  But if I search Synaptic for rar, it finds nothing.  This is just one of many, many packages that I want to install and Synaptic doesn't "see".  I've had to manually use apt-get instead.  The weirdest part is that I have the exact same installation on my laptop and everything works fine there.  I've tried running a Reload command in Synaptic (upper left hand corner) but that didn't help.

Any ideas?

Thanks,
Noah

Hey I sorta had the same problem:
I had to resort to using apt-get and apt-cache search to find packages:

[http://ubuntuforums.org/showthread.php?t=1125833](http://ubuntuforums.org/showthread.php?t=1125833)

---

### Post by Dug. on 2009-04-26
> **Hiker Hauk said:**
> If
```
$ sudo update-apt-xapian-index
```has no effect,

completely update the package lists from a source, then

```
$ sudo rm -fr /var/lib/apt-xapian-index
$ sudo update-apt-xapian-index
```

Thanks. This worked for me.

---

