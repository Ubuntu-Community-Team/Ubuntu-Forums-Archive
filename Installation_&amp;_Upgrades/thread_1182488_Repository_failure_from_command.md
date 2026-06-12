---
title: "Repository failure from command"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by kvk on 2009-06-09
Upgraded from Ibex to Jaunty.

Unable to boot into Gnome, initially from nVidia driver problems that have been resolved. At this point, unable to boot into Gnome due to (I think) some kernel issues.

At this point I need to complete the upgrade process (I think it was interrupted due to the original nVidia issue). I'm using the rt recovery kernel to boot into a root command prompt.

Running

```

sudo apt-get -f update

```

produces multiple examples of:

```

Err http://security.ubuntu.com jaunty-security Release.gpg
Could not resolve 'security.ubuntu.com'

W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg Could not resolve 'security.ubuntu.com'

```

This is repeated for a number of repositories, but not all the ones listed as operational in the sources file.

However, neither
```

apt-get update

```
nor
```

apt-get upgrade

```

produce any result. No new packages are downloaded or fixed, and the return is always "You may want to run apt-get update/upgrade to correct these problems".

I've checked the source file and made sure no repositories are commented out other than those specifically listed as being so for Jaunty.

I've tried

[CODE}
dpkg - --configure -a
[/CODE]

thinking that the upgrade might still be running in the background but no success.

Since I can't boot into Gnome, I can't access the package manager to play with things in there. I'm hoping that resolving this issue might also resolve my inability to boot into Gnome. Currently, it freezes upon entry of the password.

Thanks! And thanks to the folks who have helped with the other upgrade issues so far!!

---

### Post by kpkeerthi on 2009-06-09
You are probably not connected to the internet. Are you able to ping [www.google.com?](www.google.com?)

[http://ubuntuforums.org/showthread.php?t=571188]("http://ubuntuforums.org/showthread.php?t=571188")

---

### Post by kvk on 2009-06-09
Well, swat my hind with a melon rind!

I never would have thought of that, as my computer is hard jacked into the Net. But you are correct:

ping 64.208.34.100

produces:

Network is unreachable.

Running

sudo ifconfig

produces only a reference to the local loopback, and not the Ethernet connection.

I opened /etc/network/interfaces and added the lines

auto eth0
iface eth0 inet dhcp

and closed it. But I confess I don't know how to run the connection via the command prompt!

---

### Post by kvk on 2009-06-09
Addendum:

I checked my router and it shows the hard-connection as being functional, but that might simply means it can detect the computer at the other end of the line, not necessarily that packets are being tossed about.

---

### Post by kvk on 2009-06-10
Never mind- I'm a dork. :-p

Got it fixed and working.

---

