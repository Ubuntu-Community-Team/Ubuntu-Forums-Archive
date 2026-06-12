---
title: "Error message when trying to install packages"
date: 2008-11-26
forum: General Help
---

### Post by costre on 2008-11-26
When I am about to install selected upgrades / applications this pops up:

```
An error occurred.
The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 
```

When I try to remedy this by running the suggested command, this appears:

```

costre@costre-desktop:~$ sudo dpkg --configure -a
[sudo] password for costre: 
Setting up ufw (0.23.2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ufw (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted 
```

Suggestions?

---

### Post by bapoumba on 2008-11-26
Do you have any other dpkg instance or synaptic running ?

---

### Post by costre on 2008-11-27
I don't think so. It's the same right after reboot, when no such application should be running. 

"killall synaptic", or "killall dpkg" or such doesn't do anything. 

The only application that's set to start on login is update notifier, and I don't think that's what interrupting?

---

### Post by bapoumba on 2008-11-27
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=486843](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=486843)
Looks this is a dpkg bug

..And an ufw bug: 
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/262451](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/262451)
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/262451/comments/11](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/262451/comments/11)

Which version of ufw do you currently have installed?

---

### Post by costre on 2008-11-28
Followed the links, ended up doing this:

```
sudo dpkg -l | grep -v ^ii 
```

Lists all packages not installed correctly (rather removing all that are installed correctly (ii) )

In my case, ufw was listed as not working. 

I removed it using 

```
sudo dpkg --purge ufw
```

After that, synaptic was back to normal!

Allthough, ufw sees to be some sort of firewall. Oh, well ...

\\:D/=D>:mrgreen:

---

### Post by bapoumba on 2008-11-28
Glad to see you fixed it. I'll look about ufw. Did you install it or was it part of the basic Ubuntu install? (no time for searches right now, I should already be out of here ;))

---

### Post by costre on 2008-11-29
I did not install it on my own. It could have been indirectly installed, perhaps when I made my ethernet card share my internet connection to my LAN. Some application could have had it as a dependency, perhaps?

---

### Post by bapoumba on 2008-11-30
From what I read, looks like ufw (Ucomplicated Firewall) is installed by default for Ubuntu > Hardy, but not activated. It is an additional CLI tool to configure netfilter. There is a GUI, Gufw.
More here: [http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

I would try to reinstall it :)

---

