---
title: "What does this error mean?"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by Milkium on 2009-05-06
Hey, I'm running Ubuntu hardy heron. I'm trying to install galaxium. Everything goes well, until here. :(

```
checking for gcc... /usr/bin/gcc
checking for gmcs... /usr/bin/gmcs
checking pkg-config is at least version 0.9.0... yes
checking for MONO... no
configure: error: Please install mono version 1.2.4 or later to install Galaxium.
Please see http://www.mono-project.org/ to download latest mono sources or packages

```

---

### Post by pastalavista on 2009-05-06
You can install mono with Synaptic or use apt from the terminal
```
sudo apt-get install mono-runtime
```

---

### Post by Partyboi2 on 2009-05-06
An easier way to install galaxium is to add a 3rd party repo to your sources.list and install it, the advantage of this is that it will take care of all the dependencies for you.

```
gksu gedit /etc/apt/sources.list
``` At the bottom of the file add
```
deb http://ppa.launchpad.net/galaxium/ubuntu hardy main
deb-src http://ppa.launchpad.net/galaxium/ubuntu hardy main
```then save the changes and close gedit, then back in the terminal
```
sudo apt-get update && sudo apt-get install galaxium
```

---

### Post by Milkium on 2009-05-06
It tells me hat I already have the newest version of mono.

@Partyboi: That way just gives me the exact same error as in my original post. :/

---

### Post by Partyboi2 on 2009-05-07
I just check the repos I provided in my previous post and looks like they have dropped Hardy from them, sorry about that.
Going back to your original error message try installing libmono-dev
```
sudo apt-get install libmono-dev
```

---

### Post by xrecar on 2009-05-09
Even easier way to install:

**i386**
[http://ppa.launchpad.net/galaxium/ubuntu/pool/main/g/galaxium-svn/galaxium-svn_0.8~svn1399-0ubuntu1~jaunty1~ppa1_i386.deb](http://ppa.launchpad.net/galaxium/ubuntu/pool/main/g/galaxium-svn/galaxium-svn_0.8~svn1399-0ubuntu1~jaunty1~ppa1_i386.deb)

**AMD 64:**
[http://ppa.launchpad.net/galaxium/ubuntu/pool/main/g/galaxium-svn/galaxium-svn_0.8~svn1399-0ubuntu1~jaunty1~ppa1_amd64.deb](http://ppa.launchpad.net/galaxium/ubuntu/pool/main/g/galaxium-svn/galaxium-svn_0.8~svn1399-0ubuntu1~jaunty1~ppa1_amd64.deb)

Just Download, install and enjoy :)

---

