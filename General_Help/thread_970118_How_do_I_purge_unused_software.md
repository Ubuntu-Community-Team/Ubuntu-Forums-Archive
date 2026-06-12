---
title: "How do I purge unused software?"
date: 2008-11-03
forum: General Help
---

### Post by ardchoille42 on 2008-11-03
I'm currently on Kubuntu 8.04 and I don't install anything outside of the official repositories.

```

[~ @ ian]$ sudo aptitude install wmaker
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  libwraster3
The following NEW packages will be installed:
  libwraster3 wmaker
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2521kB of archives. After unpacking 6627kB will be used.
Do you want to continue? [Y/n/?]

```
As you can see installing wmaker with aptitude will also install libwraster3


```

[~ @ ian]$ sudo apt-get install wmaker
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libwraster3
Suggested packages:
  asclock menu wmaker-data
The following NEW packages will be installed:
  libwraster3 wmaker
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2521kB of archives.
After this operation, 6627kB of additional disk space will be used.
Do you want to continue [Y/n]?

```
As you can see installing wmaker with apt-get will also install libwraster3


```

[~ @ ian]$ sudo aptitude purge --purge-unused wmaker
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  wmaker{p}
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 6423kB will be freed.
Do you want to continue? [Y/n/?]

```
But, purging and using the --purge-unused switch with aptitude will not purge libwraster3 as stated in man aptitude:

--purge-unused
Purge packages that are no longer required by any installed package. This is equivalent to passing &#8220;-o Aptitude::Purge-Unused=true&#8221; as a command-line argument.


```

[~ @ ian]$ sudo apt-get purge --auto-remove wmaker
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  wmaker*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 6423kB disk space will be freed.
Do you want to continue [Y/n]?

```
But, purging and using the --auto-remove switch with apt-get will not purge libwraster3 as stated in man apt-get

--auto-remove
If the command is either install or remove, then this option acts like running autoremove command, removing the unused dependency packages. Configuration Item: APT::Get::AutomaticRemove.


```

[~ @ ian]$ sudo aptitude purge wmaker libwraster3
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  libwraster3{p} wmaker{p}
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 6627kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 124556 files and directories currently installed.)
Removing wmaker ...
Purging configuration files for wmaker ...
rmdir: failed to remove directory `/etc': Directory not empty
rmdir: failed to remove directory `/etc/X11': Directory not empty
Removing libwraster3 ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

```
I finally had to do it manually and it worked - it's a good thing I always copy the output of installs to a text file just in case. The trouble with this is some folks don't memorize the list of packages installed and some installs can be quite complicated.

And I'm not sure why, during the uninstall, it tried to remove /etc and /etc/X11 as that would be disastrous and shouldn't have even been attempted.

The package managers are our lifeline and users should be able to trust that they will work as advertised.

UPDATE:
I have learned that I can do:
```

sudo apt-get autoremove

```
to remove unused packages. If the switches were removed by a dev, then the man page needs to be updated as many of us rely on man pages to work on our system. If the man pages aren't correct then it's possible to damage the system. If the --purge-unused and --auto-remove switches weren't removed, why don't they work in Hardy when they worked well in previous releases?

---

### Post by Yellow Pasque on 2008-11-04
> And I'm not sure why, during the uninstall, it tried to remove /etc and /etc/X11 as that would be disastrous and shouldn't have even been attempted.

It tried to remove those dirs because they're a part of the data.tar.gz archive in the .deb file. As you can see, rmdir won't remove empty directories, so no harm is done.

---

