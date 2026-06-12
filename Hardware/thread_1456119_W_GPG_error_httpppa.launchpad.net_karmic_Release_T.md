---
title: "W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures could"
date: 2010-04-16
forum: Hardware
---

### Post by carolija on 2010-04-16
Hello i have a little problem on ubuntu server just don't know what is it exactly , any advice please ?

Thank you

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 620396F19C0042C8


Is that problem for this one ? 

```
nani@carolija:~$ sudo apt-get install debian-archive-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
nani@carolija:~$
```

```
nani@carolija:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.3kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
nani@carolija:~$
```

:confused:

---

### Post by carolija on 2010-04-16
```
nani@carolija:~$ sudo apt-get install -f
[sudo] password for nani: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.3kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
nani@carolija:~$
```

---

### Post by carolija on 2010-04-16
Damn i cant set up DNS on server coz of this and some more stuff ;/

Please help !

I guess u need to know this one too : 

> nani@carolija:~$ sudo dpkg --configure -a
nani@carolija:~$

---

### Post by carolija on 2010-04-16
Voila, done !


Like Ryton and benplanet said  just other name, in my case that was "flashplugin-nonfree" in his "Cinelerra" :

> Re: Help Removing Cinelerra
Quote:
Originally Posted by benplanet View Post
Ok I went back and deleted any lines pertaining to Cinelerra in sudo gedit /var/lib/dpkg/status

make sure you don't just delete any lines, but the whole paragraph.

SOLVED the issue. thanks.
Exactly as I said earlier.



```
nani@carolija:~$ sudo gedit /var/lib/dpkg/status
nani@carolija:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32bz2-1.0 lib32ncurses5 nspluginwrapper ia32-libs libc6-i386 lib32gcc1 lib32asound2 lib32z1 lib32stdc++6 lib32v4l-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
nani@carolija:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
nani@carolija:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 libc6-i386 nspluginwrapper
0 upgraded, 0 newly installed, 10 to remove and 11 not upgraded.
After this operation, 145MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 136683 files and directories currently installed.)
Removing nspluginwrapper ...
Removing ia32-libs ...
Removing lib32asound2 ...
Removing lib32bz2-1.0 ...
Removing lib32stdc++6 ...
Removing lib32gcc1 ...
Removing lib32ncurses5 ...
Removing lib32v4l-0 ...
Removing lib32z1 ...
Removing libc6-i386 ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
nani@carolija:~$
```

---

