---
title: "sparc support discontinued?"
date: 2008-11-22
forum: General Help
---

### Post by davidmarkey on 2008-11-22
Had SPARC support been discontinued? the last 2 releases haven't had SPARC ports?

---

### Post by Sef on 2008-11-22
> Had SPARC support been discontinued? the last 2 releases haven't had SPARC ports?


Dapper had sparc support built in, but Hardy does not.

---

### Post by davidmarkey on 2008-11-23
So the official stance is come april next year, there will be no officially supported ubuntu releases for sparc?

---

### Post by Sef on 2008-11-23
Yes, that is correct for the desktop.  Desktop updating expire June 2009, and server updating expires June 2011.

---

### Post by liquidfunk on 2008-11-24
Use Debian and customize it to your liking. That supports Sparc.

---

### Post by stream303 on 2008-12-22
> **davidmarkey said:**
> Had SPARC support been discontinued? the last 2 releases haven't had SPARC ports?

They have moved to the ports directories.  It looks like Kubuntu with KDE-4 and Xubuntu have dropped them.  However:

Kubuntu KDE-3:
[http://cdimage.ubuntu.com/kubuntu/ports/releases/8.04.1/release/](http://cdimage.ubuntu.com/kubuntu/ports/releases/8.04.1/release/)

Ubuntu:
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

As just one example.  Navigate up the tree for Intrepid 8.10 even.

OK, so you may not see the live-desktop installer, but certainly you can get the "alternate" which will just use an ncurses/text based installer but will provide a full X gui after the first reboot.

Of course there is the server, which you can do a DIY install of X if you like.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Even though the docs are mainly for Intel, I have used them very successfully on PPC macs if you filter out some irrelevant parts, but on the whole can get one up and running very fast with a server + minimal X.  I'm sure much of it applies to sparc too with obvious architecture-specific directions taken into consideration.

Perhaps get a release going, download all your favorites, and be sure to back up your apt-cache when support goes away.  You should still be good for a while depending on the depth of your security needs.  I use Aptoncd to backup the apt-cache for convenience - and it backs up to more than just cd's.

The repositories have also moved.  See about half-way down the release notes page:

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

The only issue here is that for many, the fix supplied is missing a trailing slash

So while their example shows this fix:

```
deb http://ports.ubuntu.com/ubuntu-ports hardy main restricted
deb http://ports.ubuntu.com/ubuntu-ports hardy-security main restricted
```

You may want to add a trailing slash after ubuntu-ports:

```
deb http://ports.ubuntu.com/ubuntu-ports/  hardy main restricted
deb http://ports.ubuntu.com/ubuntu-ports/  hardy-security main restricted
```

If these aren't properly configured in the first place.  When upgrading a long time ago, these showed up in the "third party" tab of the Software Sources dialog, and not in the main tab.

Hope this helps!

---

### Post by macintosh on 2008-12-26
Yes I like SPARC but like all chip's Intel is getting so good that RISC and even PPC are grinding to a halt even in servers.

---

### Post by stream303 on 2008-12-27
Ah, this may be true, but the point here is that getting Ubuntu up and running on Sparc or PPC transcends commercial viability.

The emphasis now is on community ports - a community of like minded devs and users that hate to see useful hardware go to waste.  Perhaps our platforms don't quiet meet the current metric of turning into media/televison platforms, but for those interested in *nix for it's own sake, it can still shine.

The funny thing is that we have come full circle - that is, with community-support, we get a taste of what Dennis Ritchie first envisioned at Bell Labs - a great OS to share among those who like it.

One thing I've mentioned before in the PPC forum, was that one alternative is to run our parent distro, Debian - not as a total replacement, but *in addition to*.  That way, bug reports can be placed solidly upstream, with the hope that they trickle back down, if community-supported bugs here just don't seem to have the resources to be dealt with at Ubuntu:

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

We share enough similarities, that a Debian Sparc user could help out an Ubuntu Sparc user, and visca versca.

In the end, does it really matter if a new sysadmin is learning vi or emacs for the first time on Intel, Sparc, or PPC?  Nope.

Could a general-purpose machine for the basics be made from a Sparc and be given to those in need?  Sure!

Maybe I'm succumbing to the holiday spirit. :)

---

### Post by 60hbe16es52 on 2009-01-12
how much about a [nike shoes](http://www.smkings.com) ??every one know??

---

### Post by gameover129 on 2009-02-11
potiskanje, tako lepo temo dobro delovno mesto

---

