---
title: "Amazing Long-Standing Intrepid Kernel Bug Causes Soft Lockups"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by nutznboltz on 2009-05-01
Ladies and Gentlemen, see the amazing long-standing Intrepid Kernel Pagecache Bug...

See _[Linus Torvalds use a four-letter word about this bug]("http://lkml.org/lkml/2009/1/5/307")_.

See a list of six bug reports dating from Intrepid Alpha release to the current Intrepid release now:

[u][268215]("https://bugs.launchpad.net/bugs/268215")
[289158]("https://bugs.launchpad.net/bugs/289158")
[300329]("https://bugs.launchpad.net/bugs/300329")
[303064]("https://bugs.launchpad.net/bugs/303064")
[312163]("https://bugs.launchpad.net/bugs/312163")
[348218]("https://bugs.launchpad.net/bugs/348218")[/u]

All of them describe soft lockups while running Intrepid 2.6.27-* kernels (less than 2.6.27-14)

Wonder how something of this magnitude has gone on so under-reported?

Help by testing the proposed 2.6.27-14 kernel that contains Linus' fix:

**Desktop Interpid version**
> 
/etc/apt/sources.list.d/proposed.list contains:

```
deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed main
```

/etc/apt/preferences contains:

```
Package: *
Pin: release a=intrepid-security
Pin-Priority: 990

Package: *
Pin: release a=intrepid-updates
Pin-Priority: 900

Package: *
Pin: release a=intrepid-proposed
Pin-Priority: 400
```

```
sudo aptitude update

sudo aptitude -t intrepid-proposed install linux-image-2.6.27-14-generic

and maybe if you have the need for the kernel headers as well:

sudo aptitude -t intrepid-proposed install linux-headers-2.6.27-14-generic
```

The base header package will be pulled in automatically.

reboot into new kernel

Unfortunately, update-manager will pester you about other intrepid-proposed packages. To stop this comment out the intrepid-proposed apt repository and "sudo aptitude update" again. The kernel will not downgrade because of the /etc/apt/preferences configuration.

/etc/apt/sources.list.d/proposed.list will contain:

```
# deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed main
```
```
sudo aptitude update
```


**Server Interpid version:**
> /etc/apt/sources.list.d/proposed.list contains:

```
deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed main
```

/etc/apt/preferences contains:

```
Package: *
Pin: release a=intrepid-security
Pin-Priority: 990

Package: *
Pin: release a=intrepid-updates
Pin-Priority: 900

Package: *
Pin: release a=intrepid-proposed
Pin-Priority: 400
```

```
sudo aptitude update

sudo aptitude -t intrepid-proposed install linux-image-2.6.27-14-server linux-image-server
```

and maybe if you have the need for the kernel headers as well:

```
sudo aptitude -t intrepid-proposed install linux-headers-2.6.27-14-server
```

The base header package will be pulled in automatically.


Thanks :)

---

### Post by upchucky on 2009-05-01
ummm, what is your point? intrepid never was a long term supported release and is still beta

---

### Post by nutznboltz on 2009-05-01
> **upchucky said:**
> ummm, what is your point? intrepid never was a long term supported release and is still beta

I'm trying to encourage people to test the intrepid-proposed kernel mostly.

Also, your implict idea that kernel 2.6.27 is an Ubuntu Intrepid invention is false.  2.6.27 is not and never was a beta kernel.

---

