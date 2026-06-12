---
title: "APT constantly breaking - bzip2 error"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by sphilli8 on 2009-04-17
So, I'm just sick to death of my apt breaking every single #&*%ing day. I just want to upgrade to intrepid now. I was going to wait until Jaunty comes out and upgrade then, but I'm sick of it. Unfortunately, I can't upgrade until I fix my apt....So if anyone can help me with the problem below that would be sweet.

```
sphilli8@sphilli-top:~$ sudo apt-get update
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_AU
Hit http://au.archive.ubuntu.com hardy Release.gpg
Ign http://au.archive.ubuntu.com hardy/main Translation-en_AU
Hit http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_AU
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_AU
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_AU
Ign http://security.ubuntu.com hardy-security/universe Translation-en_AU
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_AU
Hit http://security.ubuntu.com hardy-security Release
Ign http://au.archive.ubuntu.com hardy/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com hardy/universe Translation-en_AU
Ign http://au.archive.ubuntu.com hardy/multiverse Translation-en_AU
Hit http://au.archive.ubuntu.com hardy-updates Release.gpg
Ign http://au.archive.ubuntu.com hardy-updates/main Translation-en_AU
Ign http://au.archive.ubuntu.com hardy-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com hardy-updates/universe Translation-en_AU
Ign http://au.archive.ubuntu.com hardy-updates/multiverse Translation-en_AU
Hit http://wine.budgetdedicated.com edgy Release.gpg
Ign http://wine.budgetdedicated.com edgy/main Translation-en_AU
Hit http://au.archive.ubuntu.com hardy Release
Ign http://packages.medibuntu.org hardy/non-free Translation-en_AU
Hit http://packages.medibuntu.org hardy Release
Hit http://archive.canonical.com hardy Release
Hit http://wine.budgetdedicated.com hardy Release.gpg
Ign http://wine.budgetdedicated.com hardy/main Translation-en_AU
Hit http://wine.budgetdedicated.com edgy Release
Hit http://au.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://packages.medibuntu.org hardy/free Packages
Ign http://archive.canonical.com hardy/partner Packages
Hit http://wine.budgetdedicated.com hardy Release
Hit http://au.archive.ubuntu.com hardy/main Packages
Hit http://au.archive.ubuntu.com hardy/restricted Packages
Hit http://au.archive.ubuntu.com hardy/main Sources
Hit http://au.archive.ubuntu.com hardy/restricted Sources
Hit http://au.archive.ubuntu.com hardy/universe Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://archive.canonical.com hardy/partner Packages
Ign http://wine.budgetdedicated.com edgy/main Packages
Hit http://au.archive.ubuntu.com hardy/universe Sources
Hit http://au.archive.ubuntu.com hardy/multiverse Packages
Hit http://au.archive.ubuntu.com hardy/multiverse Sources
Get:1 http://au.archive.ubuntu.com hardy-updates/main Packages [430kB]
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Ign http://wine.budgetdedicated.com hardy/main Packages
Hit http://wine.budgetdedicated.com edgy/main Packages
Hit http://wine.budgetdedicated.com hardy/main Packages
Hit http://au.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://au.archive.ubuntu.com hardy-updates/main Sources
Hit http://au.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://au.archive.ubuntu.com hardy-updates/universe Packages
Hit http://au.archive.ubuntu.com hardy-updates/universe Sources
Hit http://au.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://au.archive.ubuntu.com hardy-updates/multiverse Sources
99% [1 Packages bzip2 0]
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://au.archive.ubuntu.com hardy-updates/main Packages
  Sub-process bzip2 returned an error code (2)
Fetched 430kB in 5s (77.2kB/s)
W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/                                                              binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used                                                               instead.
sphilli8@sphilli-top:~$

```

When I try to open Adept Manager I get the message.> The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.
I was getting this message even *after* I fixed the last problem (yesterday) and "apt-get update" wasn't returning any errors. I don't know what the hell's going on with that, but if anyone can tell me how to do a version upgrade from console that would be sweet too.

spanks
Steve

---

### Post by lemming465 on 2009-04-19
The first thing to try is **sudo aptitude clean** to clear out any damaged cached files that are getting in your way.  If that doesn't fix the problem, try switching to a different mirror server.  You can either edit /etc/apt/sources.list by hand, or use the "Download from ..." dropdown in Synaptic -> Settings -> Repositories on the Ubuntu sources tab.

For a console based update, you have to switch the version in /etc/apt/sources.list (something like sudu perl -ie 's/hardy/intrepid/g;' ...) and then run something like "sudo aptitude full-upgrade".  If you have GUI available, "sudo update-manager -d" will be easier.

Note that you can't upgrade directly from hardy to jaunty, you have to go through intrepid along the way.

---

### Post by sphilli8 on 2009-04-22
Thanks for the advice, I ended up getting a CD to work and upgrading that way. Unfortunately the APT was still constantly breaking after the upgrade, and I narrowed the problem down to damaged hardware. Most likely the motherboard. Grrr.

---

### Post by lemming465 on 2009-04-23
In the mid-1990's a classic hardware test was compiling a linux kernel from source.  That tended to severely stress the CPU, cache, memory, disk controller, and hard drive.  If there was any flakey hardware anywhere, you'd see segmentation fault errors.

> Most likely the motherboard
Check for bad capacitors (misshapen or discolored).  Some years ago there were problems with fake Chinese electrolytes; the industrial espionage against the Japanese vendors had missed a key stabilizing ingredient.

---

