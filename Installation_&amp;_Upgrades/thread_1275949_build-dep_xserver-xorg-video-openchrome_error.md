---
title: "build-dep xserver-xorg-video-openchrome error"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by ctsdownloads on 2009-09-26
Here is what I am trying to do - it's been done my tons of people, I am working with a clean install, so I am unclear as to why I am running into problems.

```

sudo apt-get install build-essential subversion autoconf automake1.9 libtool
sudo apt-get build-dep xserver-xorg-video-openchrome
svn checkout http://svn.openchrome.org/svn/trunk openchrome
cd openchrome*/src
wget http://launchpadlibrarian.net/24709429/km400_panel.patch
patch -p1 < km400_panel.patch
cd ..
./autogen.sh --prefix=/usr
make
sudo make install
sudo dpkg-reconfigure -phigh xserver-xorg
```

With my sources.list enabled and updated, I get....


```
sudo apt-get build-dep xserver-xorg-video-openchrome

E: Unable to find a source package for xserver-xorg-video-openchrome
```

So logically, I try this:

```
sudo apt-get install xserver-xorg-video-openchrome

xserver-xorg-video-openchrome is already the newest version.
xserver-xorg-video-openchrome set to manually installed.
```

build-essential subversion autoconf automake1.9 libtool are all installed -I triple checked this....please help, I have spend DAYS trying to troubleshoot this. Google is giving me nothing on the error whatsoever.

All repos provided are enabled from sources.list with apt-get update/upgrade already run. I have run multiple times with apt-get install -f and yes, my Internet connection works fine. What the hell could be causing me to have issues with build-dep xserver-xorg-video-openchrome?

---

### Post by rreese6 on 2009-09-26
Would you mind posting your sources.list here?
And have you checked Ubuntu packages to see if there is a source package for your version?

There was an interesting bug report talking about the openchrome driver causing problems with a wireless card. one user is using the propriety VIA driver for Chrome 9 to fix his issue in Juanty. He also states that there is not source for OpenChrome for Jaunty...Not sure that is right, but Google isn't turning up much yet.
Here is the bug report:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/331952]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/331952")
Look at post #27 to start.

And here is a blog with some interesting reading...seems like the last person got it to work:
[http://www.rummik.com/blog/2009/05/via-chrome9-hc-ubuntu-904-3d-hardware.html](http://www.rummik.com/blog/2009/05/via-chrome9-hc-ubuntu-904-3d-hardware.html)

Sorry I don't have a direct answer for you.

---

### Post by ctsdownloads on 2009-09-26
Appreciate the post. Yeah, the Ubuntu 9.10 alpha 6 is not even able to avoid tossing up errors the entire way. I tried it, not looking good for me at all.

I would post my sources.list, but being it is from a command line...not sure how that is going to work as typing out everything would take days. It's a default list from 7.10, up'd to 9.04. SCR's, etc.

Here is what is going on:
[http://ubuntuforums.org/showthread.php?t=930121](http://ubuntuforums.org/showthread.php?t=930121)

Same notebook, same exact problem, the ONLY CD (tested over 20 different types/styles with five ISO downloads, chsums verified) and 7.10 upward is the only way to go. Alternate Cds for 8.04 up all fail with this config. OpenChrome should have never been, the old VIA option worked and Ubuntu dumped. Sadly...

---

### Post by ctsdownloads on 2009-09-26
Being as both Puppy Linux 4.3 (brand new) and PCLinuxOS 2009 both work fine with the Via chipeset, I am leaving Ubuntu to my other PCs not relying on a sloppy openchrome release.

Thanks

---

### Post by rreese6 on 2009-09-26
I see you are going down the path I did with one of my servers.
I could never get the OpenChrome to be stable with 3D and Resolution.
My fix was to grab an Nvidia card and use that. I am not he guy to resolve the OpenChrome issue... I have been reading looks like most people are using the svn of openchrome to do their compiling.
Sorry I can 't be more help

---

### Post by ctsdownloads on 2009-09-26
> **rreese6 said:**
> I see you are going down the path I did with one of my servers.
I could never get the OpenChrome to be stable with 3D and Resolution.
My fix was to grab an Nvidia card and use that. I am not he guy to resolve the OpenChrome issue... I have been reading looks like most people are using the svn of openchrome to do their compiling.
Sorry I can 't be more help

Tried both a svn patch method and a raw wget download/untar of the open crome driver. In both cases, it required build-dep xserver-xorg-video-openchrome to work instead of giving me  E: Unable to find a source package for xserver-xorg-video-openchrome .

As highlighted in my first post, I just need to understand how everything can be installed yet I am still failing to see success with build-dep. 

Another guy pointed out a lack of a repo in the sources.list, but I un-commented all of them in a new install...

---

