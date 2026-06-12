---
title: "Netbook graphic drivers for linux.."
date: 2011-01-09
forum: Hardware
---

### Post by Linux_noob84 on 2011-01-09
I am currently running ubuntu 10.04 on my ASUS Eee PC 1005HAB, and I would like to find a driver/graphic accelerator similar to the one I used to have for Windows 7 (previously on this machine).

I've checked Intel's website but there really isn't much of anything for linux graphic drivers.  

Other sites have come up with Windows-only solutions.

Does anyone have any ideas?  Is there a DirectX equivalent program? Is it possible to run drivers/accelerators through WINE?

---

### Post by mikewhatever on 2011-01-09
Hi again. Not trying to stalk you or anything, just thought I'd explain how things work with Intel graphics in Linux/Ubuntu. 
Intel doesn't provide installation packages for Linux distros from its web site, and neither do vendors like Asus, probably due to diversity of the Linux world. Instead, Intel graphics drivers are supplied by distros, for example, with Lucid, you must be using xserver-xorg-video-intel version 2.9.1, and you can verify it with the following command:
```
dpkg -l | grep xserver-xorg-video-intel
```

The latest driver available for Ubuntu through a testing launchpad repository is version 2.13. That said, Intel has released version 2.14 on Jan 8, so that the testing repository should be updated shortly.
If you think you'll benefit from the 'latest and greatest' then add the testing ppa and let it update. Make sure you read the "Important notice" and follow its instructions.
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Best of luck.

---

### Post by Linux_noob84 on 2011-01-09
> **mikewhatever said:**
> Hi again. Not trying to stalk you or anything, just thought I'd explain how things work with Intel graphics in Linux/Ubuntu. 
Intel doesn't provide installation packages for Linux distros from its web site, and neither do vendors like Asus, probably due to diversity of the Linux world. Instead, Intel graphics drivers are supplied by distros, for example, with Lucid, you must be using xserver-xorg-video-intel version 2.9.1, and you can verify it with the following command:
```
dpkg -l | grep xserver-xorg-video-intel
```The latest driver available for Ubuntu through a testing launchpad repository is version 2.13. That said, Intel has released version 2.14 on Jan 8, so that the testing repository should be updated shortly.
If you think you'll benefit from the 'latest and greatest' then add the testing ppa and let it update. Make sure you read the "Important notice" and follow its instructions.
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

Best of luck.

No I don't consider it stalking, I appreciate the help mike!

I'm assuming this code is something I have to enter into the terminal?  Last time I did so from a command line similar to this, I was put into the almost 2 day predicament of having to reinstall ubuntu...  though that was 10.10.

Is there somewhere that there are "basic terms" listed?  I have no idea what a ppa is, or a distro.

---Never mind, I'm seeing the explanations at the link you put up.  Thanks again!

---

### Post by Linux_noob84 on 2011-01-09
OK, the command verified that I do have 2.9.1 on this version, so that means I have to locate the driver address as the instructions tell me, if I'm reading them correctly...?

---I found this: [http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

---

### Post by mikewhatever on 2011-01-09
> **Linux_noob84 said:**
> OK, the command verified that I do have 2.9.1 on this version, so that means I have to locate the driver address as the instructions tell me, if I'm reading them correctly...?

---I found this: [http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

Hm ..., hope that works for you, though the howto is a bit dated.
A ppa is Personal Package Archive, and the link I posted above has all the info on how to add it to your software sources list and what to do then. I'd recommend using the info on the ppa page, rather then the howto.

---

