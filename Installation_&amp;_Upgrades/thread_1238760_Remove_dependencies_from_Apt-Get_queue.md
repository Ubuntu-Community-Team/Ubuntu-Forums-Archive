---
title: "Remove dependencies from Apt-Get queue"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by p2bc on 2009-08-12
*** Well my first thread, might have seen me around a bit on the boards, I composed this lengthy Thread a couple of days ago and lost it when I went to post it. So here goes a short version of that original composition. ***

I tried to install [FireWall Builder]("http://www.fwbuilder.org/") by downloading the DEB from the website. It failed with no explanation. 

I proceed to install it from the repository even though it was not current, by using:
```

sudo apt-get install fwbuilder

```It notified me that two dependencies were not install rather than actually installing them, found that weird at the time.
```

The following packages have unmet dependencies:
  fwbuilder: Depends: libfwbuilder-abi-3.0.2
             Depends: libfwbuilder8 but it is not installed
  fwbuilder-linux: Depends: libfwbuilder-abi-3.0.2
                   Depends: libfwbuilder8 but it is not installed
E: Unmet dependencies. Try using -f.

```So I tried -f and build-dep
```

sudo apt-get -f install fwbuilder
sudo apt-get build-dep fwbuilder
...
Unpacking libfwbuilder8 (from .../libfwbuilder8_3.0.2-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libfwbuilder8_3.0.2-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libfwbuilder.so.8', which is also in package libfwbuilder
Unpacking libfwbuilder-dev (from .../libfwbuilder-dev_3.0.2-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libfwbuilder-dev_3.0.2-1_i386.deb (--unpack):
 trying to overwrite `/usr/include/fwb-3/fwbuilder/inet_net.h', which is also in package libfwbuilder
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libfwbuilder8_3.0.2-1_i386.deb
 /var/cache/apt/archives/libfwbuilder-dev_3.0.2-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies

```So now if I do anything other than apt-get update I get  the error because the dependencies are still in the queue. I tried -clean, -autoclean, -purge, no good on the main package and the dependencies.
```

sudo apt-get purge fwbuilder
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  fwbuilder-linux: Depends: libfwbuilder-abi-3.0.2
                   Depends: libfwbuilder8 but it is not going to be installed
                   Depends: fwbuilder (= 3.0.2-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```So how do I remove them from the queue and get back to normal. As it is I managed to install FWBuilder on a VMware and found I did not like it. So now I just want to get ride of it.

Help Plz!!!

*** If you think this one not short, you should have seen the other one.  :) ***

---

### Post by wojox on 2009-08-12
Try:

```
sudo aptitude -f remove fwbuilder
```

---

### Post by p2bc on 2009-08-12
no good  :(

```

user@comp:~$ sudo apt-get -f remove fwbuilder
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  fwbuilder-linux: Depends: libfwbuilder-abi-3.0.2
                   Depends: libfwbuilder8 but it is not going to be installed
                   Depends: fwbuilder (= 3.0.2-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by p2bc on 2009-08-12
For those following along, I also just tried (DID NOT WORK):
```

user@comp:~$ sudo apt-get -f remove
[sudo] password for user:            
Reading package lists... Done         
Building dependency tree              
Reading state information... Done     
Correcting dependencies... Done       
The following packages were automatically installed and are no longer required:
  libopenal1 mplayer-skins libcap1 libdecoration0 mplayer metacity-common libgnome-menu2 libamrnb3 libamrwb3 libprotobuf3 liblzo2-2 libgnome-window-settings1
  libmetacity0 libemeraldengine0 libgnome-desktop-2-11 libfwbuilder8                                                                                         
Use 'apt-get autoremove' to remove them.                                                                                                                     
The following extra packages will be installed:                                                                                                              
  fwbuilder libfwbuilder8 libqt4-gui                                                                                                                         
The following packages will be REMOVED:                                                                                                                      
  fwbuilder-linux                                                                                                                                            
The following NEW packages will be installed:
  libfwbuilder8 libqt4-gui
The following packages will be upgraded:
  fwbuilder
1 upgraded, 2 newly installed, 1 to remove and 71 not upgraded.
82 not fully installed or removed.
Need to get 3468kB/4014kB of archives.
After this operation, 5558kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  fwbuilder
Install these packages without verification [y/N]? y
Get:1 http://archive.ubuntu.com jaunty-updates/main libqt4-gui 4.5.0-0ubuntu4.1 [2300B]
Get:2 http://www.fwbuilder.org jaunty/contrib fwbuilder 3.0.5-b1116-ubuntu-jaunty-1 [3466kB]
Fetched 3468kB in 5s (659kB/s)
Failed to fetch http://www.fwbuilder.org/deb/stable/./dists/jaunty/contrib/binary-i386/fwbuilder_3.0.5-b1116-ubuntu-jaunty-1_i386.deb Hash Sum mismatch
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
user@comp:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libopenal1 mplayer-skins libcap1 libdecoration0 mplayer metacity-common libgnome-menu2 libamrnb3 libamrwb3 libprotobuf3 liblzo2-2 libgnome-window-settings1
  libmetacity0 libemeraldengine0 libgnome-desktop-2-11 libfwbuilder8
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fwbuilder libfwbuilder8 libqt4-gui
The following packages will be REMOVED:
  fwbuilder-linux
The following NEW packages will be installed:
  libfwbuilder8 libqt4-gui
The following packages will be upgraded:
  fwbuilder
1 upgraded, 2 newly installed, 1 to remove and 71 not upgraded.
82 not fully installed or removed.
Need to get 3466kB/4014kB of archives.
After this operation, 5558kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  fwbuilder
Install these packages without verification [y/N]? y
Get:1 http://www.fwbuilder.org jaunty/contrib fwbuilder 3.0.5-b1116-ubuntu-jaunty-1 [3466kB]
Fetched 3466kB in 6s (504kB/s)
Failed to fetch http://www.fwbuilder.org/deb/stable/./dists/jaunty/contrib/binary-i386/fwbuilder_3.0.5-b1116-ubuntu-jaunty-1_i386.deb Hash Sum mismatch
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

```

---

### Post by kerry_s on 2009-08-12
use synaptic, click status & uninstall the broken package.

---

### Post by mc4man on 2009-08-13
You should remove that fwbuilder repo that you added to your sources.list.

> [http://www.fwbuilder.org](http://www.fwbuilder.org) jaunty/contrib 

---

### Post by p2bc on 2009-08-13
Sorry to say, I don't have Synaptic installed and can't install it because of the on going headach. I only use the terminal, and the "Add/Remove Progams" in the System Settings windows say is can't because of unresolved dependencies. Joy

---

### Post by Partyboi2 on 2009-08-13
Hi, can you post the output to
```
sudo apt-get -f install
```

---

### Post by p2bc on 2009-08-13
Mc4man:
I would be happy to remove the link but i figure i will have to install it before I can remove it, and I figure I might need repo before long.

[side note]
Just commented it out to see if it Ubuntu repo would over ride that one and "be more current and stable", but no luck.

---

### Post by p2bc on 2009-08-13
Partyboi2:
I did, but here it is again,
```

user@comp:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libopenal1 mplayer-skins libcap1 libdecoration0 mplayer metacity-common libgnome-menu2 libamrnb3 libamrwb3 libprotobuf3 liblzo2-2 libgnome-window-settings1
  libmetacity0 libemeraldengine0 libgnome-desktop-2-11 libfwbuilder8
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fwbuilder libfwbuilder8 libqt4-gui
The following packages will be REMOVED:
  fwbuilder-linux
The following NEW packages will be installed:
  libfwbuilder8 libqt4-gui
The following packages will be upgraded:
  fwbuilder
1 upgraded, 2 newly installed, 1 to remove and 71 not upgraded.
82 not fully installed or removed.
Need to get 3466kB/4014kB of archives.
After this operation, 5558kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  fwbuilder
Install these packages without verification [y/N]? y
Get:1 http://www.fwbuilder.org jaunty/contrib fwbuilder 3.0.5-b1116-ubuntu-jaunty-1 [3466kB]
Fetched 3466kB in 6s (504kB/s)
Failed to fetch http://www.fwbuilder.org/deb/stable/./dists/jaunty/contrib/binary-i386/fwbuilder_3.0.5-b1116-ubuntu-jaunty-1_i386.deb Hash Sum mismatch
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

```

---

### Post by p2bc on 2009-08-14
What are all of Synaptic's dependencies??? I just download Synaptic from the Ubuntu repo manually, and well it has dependencies, which I can't see because of this FWBuilder problem because it keeps trying to resolve it before doing any other queuries. It just tells me the same thing over and over.

---

### Post by mc4man on 2009-08-14
Too bad about not having synaptic.
Have you tried, with that 'crappy' repo enabled running 
sudo apt-get update 
and then see if it can fetch the newer fwbuilder 


((looking at this from eariler post
> Failed to fetch [http://www.fwbuilder.org/deb/stable/./dists/jaunty/contrib/binary-i386/fwbuilder_3.0.5-b1116-ubuntu-jaunty-1_i386.deb](http://www.fwbuilder.org/deb/stable/./dists/jaunty/contrib/binary-i386/fwbuilder_3.0.5-b1116-ubuntu-jaunty-1_i386.deb) [COLOR="Blue"]Hash Sum mismatch[/COLOR]
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
user@comp:~$ sudo apt-get -f install


(( which if you go directly to the repo, the packages show up here as  uninstallable due to either "The package might be corrupted or you are not allowed to open..."
I've never seen a repo or ppa say that about a direct download of a .deb


[http://www.fwbuilder.org/deb/stable/dists/jaunty/contrib/binary-i386/](http://www.fwbuilder.org/deb/stable/dists/jaunty/contrib/binary-i386/)

---

### Post by p2bc on 2009-08-14
Well I looked into the repo, and try setting up a new, key and all, and well this is what I got.  Pretty much the same thing.
```

...
Unpacking libfwbuilder8 (from .../libfwbuilder8_3.0.2-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libfwbuilder8_3.0.2-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libfwbuilder.so.8', which is also in package libfwbuilder
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libfwbuilder8_3.0.2-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What is an **error code (1)** mean???

---

### Post by mc4man on 2009-08-14
Usually that error means the same file is already installed and can't be overwritten (generally because it was installed from another package or means.

Did you or can you run sudo apt-get update?

Somethings to consider:

All the packages at your third party site (fwbuilder.org/) are 3.0.5....(hardy, intrepid, jaunty

Your fwbuilder.org repo does not have libfwbuilder8, nor libfwbuilder-dev, nor fwbuilder-linux. 

It has libfwbuilder_3.0.5....which has all the shared and static libraries (basically what libfwbuilder8, and libfwbuilder-dev have combined

and

fwbuilder_3.0.5 which has what's in fwbuilder-linux plus some add.

In other words fwbuilder.org repo packages and the ubuntu repo packages are 110% incompatible which each other

To install **any fwbuilder package from jaunty** you'll need to remove the 2 from fwbuilder.org **completely** and remove that repo from sources first ((if **any** of the 2 packages from fwbuilder.org were installed

(( if you look carefully at your posts you'll see jaunty packages trying to be installed along with the fwbuilder_3.05 from the other repo - won't work, plus your not fetching the fwbuilder.org anyway - see edit

**If libfwbuilder_3.x.x was installed** and you can only remove the fwbuilder.org repo packages by first updating them then you'll have to figure a way to do so. (to 3.0.5...

This seems to indicate it was (considering what I posted above about what was in libfwbuilder_3... 
> Unpacking libfwbuilder-dev (from .../libfwbuilder-dev_3.0.2-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libfwbuilder-dev_3.0.2-1_i386.deb (--unpack):
 trying to overwrite `[COLOR="Blue"]/usr/include/fwb-3/fwbuilder/inet_net.h[/COLOR]', which is also in package [COLOR="Blue"]libfwbuilder[/COLOR]


You probably can't go directly to fwbuilder.org repo and install because (at least here) they read as corrupted.
I believe that's because the .deb's have an extra file (_gpgorigin), so you'll need to update them through apt-get or aptitude

(( if I were you I'd get rid of that repo (fwbuilder.org ) and it's packages (if either of them were installed) one way or the other. (**almost 100% sure that at least libfwbuilder_3.x.x was and still is**
And if you get squared away install a graphical package manager, synaptic is best.

Some add. perspective

> I tried to install FireWall Builder by downloading the DEB from the website. It failed with no explanation.

It appears that that's not totally true, at the very least libfwbuilder_3.x.x was installed and is probably at the source of your problems.

> sudo apt-get build-dep fwbuilder

The fwbuilder.org packages are checkinstall packages. While they were created with install deps, they contain no build-dep info. When you ran apt-get build-dep the info from the jaunty repo ver,. was used which created add problems, errors

I would use aptitude instead of apt-get, try to remove libfwbuilder or update fwbuilder (with that repo source enabled if trying to update

Edit 
> Troubleshooting .deb repository access

After this, you should be  able to install and update fwbuilder packages using synaptic or aptitude.

Note that apt caches package information, so when we release new packages, they will not match cached data when you try to install them. Run apt-get update before you install or upgrade packages to refresh cached data. If you don't, you'll get "Size mismatch" error which is not very descriptive. Note that if you do this from the command line using apt-get, you'll notice that it suggests running apt-get upate, but unfortunately update manager cuts off this part of the error message. Just run apt-get update or aptitude update from the command line before doing update. 

---

### Post by p2bc on 2009-08-14
*** FIXED ***

Removed the FWBuilder.org from the repo, updated. and then "sudo apt-get -f install" and voila, actually hit 100%

Thank you, thank you!!!
Words escape me, don't know what to say....(seriously)...Thanks

---

### Post by p2bc on 2009-08-14
First thing I did after getting it fixed, was insatlling Synaptics, :D

---

### Post by mc4man on 2009-08-14
Good to hear, was just going to post that this 
```
sudo aptitude remove libfwbuilder
```
would of probably also fixed 
sometimes aptitude is better than apt-get 

> First thing I did after getting it fixed, was insatlling Synaptics

having synaptic will prove to be useful, would of fixed this in a min. or so

---

