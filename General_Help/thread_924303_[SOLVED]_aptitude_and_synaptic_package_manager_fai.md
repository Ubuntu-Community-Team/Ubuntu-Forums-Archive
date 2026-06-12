---
title: "[SOLVED] aptitude and synaptic package manager failing!"
date: 2008-09-19
forum: General Help
---

### Post by SpaceMaster on 2008-09-19
Oh, dear Lord.  I've done it now.  Not sure how, either.  Synaptic Package Manager, regardless of what I'm trying to install, returns ```
 W: Failed to fetch http://archive.canonical.com/ubuntu/pool/partner/.../(package)
302 Found 
```
Aptitude is in similarly poor condition.  However, it builds the dependencies, and asks its normal confirmation
```
$ sudo apt-get install (package)
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
(package)
... and so on, until... 
Err http://archive.canonical.com/ubuntu/pool/partner/.../(package) 302 Found
Failed to fetch http://archive.canonical.com/ubuntu/pool/partner/.../(package) 302 Found

```
This happens for all packages.  occasionally, aptitude prompts me with ```
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing
```
So I update the package list, then run
```
sudo apt-get --fix-missing
```
but all I get is the help page for aptitude.  Other variations I've tried have been:
```
sudo apt-get -f
sudo apt-get -m
```neither of which have succeeded.  The only change I made to the computer this morning was resizing the root partition (/ was getting down to its last 700MB, so I took a bite out of my storage partition and allocated it to /).  I don't see how this would have anything to do with install packages.

oh, yes, I am connected to the network, on a LAN connection, and am able to ping things that are not my computer.  Running Ubuntu 8.04 (Hardy Heron) on a Dell Inspiron 9100

---

### Post by SpaceMaster on 2008-09-19
Oops.  Figured out that although I was connected, I had to logged into my ISP.  Did that and the problem went away.  Marking thread as solved.

Incidentally, what is the proper invocation of sudo apt-get --fix-missing?

---

