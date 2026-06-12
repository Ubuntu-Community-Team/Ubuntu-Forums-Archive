---
title: "Dpkg Completely Screwed?"
date: 2008-09-02
forum: General Help
---

### Post by TSHNOFX on 2008-09-02
Well, today, I decided to wipe my XP installation after I just plain got pissed off at the naziness of microsoft. Well, I of course downloaded everything I would need to get my wireless card working, which paid off, because it is working(on it now). The only thing is(I did this twice, and another time on Linux Mint, an ubuntu derivative) whenever I attempt to install large packages, it will somehow, some way, fail to install, for no apparent reason, and it won't completely uninstall, so I have go in and wipe every trace of it myself. If anyone might have any solution to this, I wouldn't mind.

sample:```
Setting up gettext (0.17-2ubuntu1) ...
install-info: unrecognized option `--description='
	Try `install-info --help' for a complete list of options.
dpkg: error processing gettext (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libcvsservice0 (4:3.5.9-0ubuntu1) ...

Setting up kdevelop (4:3.5.1-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 gettext
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/home/aaron# 

```

Then, watch what happens when I try to remove:
```
132004 files and directories currently installed.)
Removing gettext ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gettext (--remove):
 subprocess pre-removal script returned error exit status 1
install-info: unrecognized option `--description='
	Try `install-info --help' for a complete list of options.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gettext
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now, I have to go in and clean it alll out. :(. Anyways, like I said before, if anyone has had this problem, and solved it, I wouldn't mind you telling me.

---

### Post by iaculallad on 2008-09-02
In your terminal, what happens if you issue the commands below:

```
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by TSHNOFX on 2008-09-02
I actually have a script that I had written up with those commands in one of my many attempts to fix this. Same result as the second code box.

---

### Post by iaculallad on 2008-09-02
What about doing:

```
sudo apt-get -u install gettext 
```

then:

```
sudo dpkg --purge gettext
```

and:

```
sudo apt-get update
```

---

### Post by TSHNOFX on 2008-09-02
Codebox #2 again. I know this didn't happen when I had gutsy on my old computer :/. I'm going to bed for tonight, I'll more than likely be on tomorrow afternoon.

---

### Post by iaculallad on 2008-09-02
> **TSHNOFX said:**
> Codebox #2 again. I know this didn't happen when I had gutsy on my old computer :/. I'm going to bed for tonight, I'll more than likely be on tomorrow afternoon.

Whew... what about:

```
sudo dpkg --force-depends --force-remove-reinstreq --purge gettext
```

---

### Post by TSHNOFX on 2008-09-02
Removing it isn't the problem, it's the fact that it happens over and over again. To remove it, I have to manually go in and wipe out everything, but, it works.

Perhaps there are broken packages? This happened with..what was it..libidn11-dev when I was test installing kubuntu-desktop.

Perhaps I have something installed that I shouldn't have? I have wicd with the b43 firmware and stuff, no other way to connect to the internet without linuxant driverloader(not free). I installed build-essential(this is more or less a psp dev environment, among other things), ssh, gftp, and a few other things right as soon as I got the internet working.

Perhaps there is a specific package that I have installed that is causing this? If there is an easy method of showing you all of the packages I've installed, now would be the time to tell me.

It's multiple packages, a significant amount actually, and it baffles me as to why it does this. I used a virtual box initially(just to test this distro, make sure it's stable, ect) and everything was green light, so I ridded of linux mint(Same problem, which is why I said the wicd and what not) and got ubuntu. If there are any compatibility problems with anything, I wouldn't mind knowing.

---

### Post by ltracy on 2008-09-30
I'm having a similar problem now.  I've been running hardy for quite awhile with no trouble, and now I'm getting the following

<code>
 1
 2
 3
 4
 5
 6
 7
 8
 9
10
11
12
13
14
15
16
17
18
19
20
21
22

	

Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 172115 files and directories currently installed.)
Preparing to replace util-linux 2.13.1-5ubuntu2 (using .../util-
linux_2.13.1-5ubuntu3_i386.deb) ...
install-info: No dir file specified; try --help for more information.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing /var/cache/apt/archives/util-linux_2.13.1-5ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
install-info: unrecognized option `--description=System V interprocess communication facilities'
	Try `install-info --help' for a complete list of options.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/util-linux_2.13.1-5ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing util-linux (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
</code>

from update manager.  I've attempted the above solution with no effect.  Anyone have other suggestions?

---

