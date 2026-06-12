---
title: "How do I fix my Intel Graphics Update Tool?"
date: 2018-04-04
forum: Hardware
---

### Post by jacatone on 2018-04-04
I'm using Ubuntu 16.04 LTS 64-bit. I'm experiencing video tearing during playback. When I run the Intel Integrated video update tool, I get the dependency error shown below. How do I fix this?

---

### Post by mörgæs on 2018-04-05
Please post the output from ```
apt-cache policy libgtk-3-0
```

---

### Post by jacatone on 2018-04-05
jacatone@HP-Compaq:~$ apt-cache policy libgtk-3-0
libgtk-3-0:
  Installed: 3.10.8-0ubuntu1.6
  Candidate: 3.10.8-0ubuntu1.6
  Version table:
 *** 3.10.8-0ubuntu1.6 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.10.8-0ubuntu1.4 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
     3.10.8-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
W: Duplicate sources.list entry [http://www.deb-multimedia.org/](http://www.deb-multimedia.org/) jessie/main amd64 Packages (/var/lib/apt/lists/www.deb-multimedia.org_dists_jessie_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://www.deb-multimedia.org/](http://www.deb-multimedia.org/) jessie/non-free amd64 Packages (/var/lib/apt/lists/www.deb-multimedia.org_dists_jessie_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://www.deb-multimedia.org/](http://www.deb-multimedia.org/) jessie/main i386 Packages (/var/lib/apt/lists/www.deb-multimedia.org_dists_jessie_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://www.deb-multimedia.org/](http://www.deb-multimedia.org/) jessie/non-free i386 Packages (/var/lib/apt/lists/www.deb-multimedia.org_dists_jessie_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
jacatone@HP-Compaq:~$

---

### Post by monkeybrain20122 on 2018-04-06
Since you said you are on Ubuntu 16.04 why are you having all trusty repositories?
```
$ apt-cache policy libgtk-3.0
libgtk-3-0:
  Installed: 3.18.9-1ubuntu3.3
  Candidate: 3.18.9-1ubuntu3.3
  Version table:
 *** 3.18.9-1ubuntu3.3 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.18.9-1ubuntu3 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
libgtk-3-0-dbg:
  Installed: (none)
  Candidate: 3.18.9-1ubuntu3.3
  Version table:
     3.18.9-1ubuntu3.3 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
     3.18.9-1ubuntu3 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
```



For your original issue I don't recommend using intel's installer, I would use [this]("https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa") for intel cards.

---

### Post by jacatone on 2018-04-06
Not quite sure what I'm supposed to do with this link? Where does it say how to update drivers?

---

### Post by monkeybrain20122 on 2018-04-06
> **jacatone said:**
> Not quite sure what I'm supposed to do with this link? Where does it say how to update drivers?

Instructions are on the page, just type in the terminal

```
sudo add-apt-repository ppa:paulo-miguel-dias/pkppa

sudo apt-get update


```

But I think you should sort out your repository mess first; why do you have Trusty repositories while you said you are on Xenial? Your libgtk-3.0 is much older than xenial's version, that is what caused your error in the first place. Secondly Debian multimedia ppa is not for Ubuntu and may break your system, what do you need from there? Should remove it from your sources list.

---

### Post by jacatone on 2018-04-06
I thought I was using v16.04. Must be an older one. What do I do after the update?

---

### Post by monkeybrain20122 on 2018-04-07
Oops, still need to run 

```
sudo apt ugrade
```

to upgrade the driver, then reboot.

---

### Post by jacatone on 2018-04-09
Didn't make any difference.

---

### Post by Yellow Pasque on 2018-04-09
> **jacatone said:**
> Didn't make any difference.

The PPA being discussed doesn't have any packages for Trusty/14.04

The Intel graphics tool is more for distro maintainers and packagers than end users.

It's probably time for a fresh install of 18.04 (and don't try to mix Debian repos in it), or give more details on what desktop you're using and what program and output you're using for video playback. Updating the video driver may not be the magical solution you're looking for.

---

### Post by logix2 on 2018-04-12
The Intel Graphics Update Tool has been [discontinued]("https://01.org/linuxgraphics/downloads/update-tool") recently. Moreover, Ubuntu versions older than 17.04 are not supported for quite a while by this tool, so I would recommend not using it.

---

### Post by jacatone on 2018-04-19
Tried newer versions of Ubuntu. Has the same problem. Previously had Win 8.1 on this machine and didn't have this issue.

---

