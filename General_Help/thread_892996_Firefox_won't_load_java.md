---
title: "Firefox won't load java"
date: 2008-08-17
forum: General Help
---

### Post by MarshyTheKid on 2008-08-17
I was trying to upload some pictures with Facebook and it starts loading the java then stops, saying applet not initialized

```

java.lang.NullPointerException
	at net.sourceforge.jnlp.NetxPanel.runLoader(NetxPanel.java:82)
	at sun.applet.AppletPanel.run(AppletPanel.java:380)
	at java.lang.Thread.run(Thread.java:636)
  PIPE: appletviewer wrote: status exception: java.lang.NullPointerException.
java.lang.NullPointerException
	at sun.applet.AppletPanel.run(AppletPanel.java:430)
	at java.lang.Thread.run(Thread.java:636)
  PIPE: appletviewer wrote: status Start: applet not initialized.
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback: setting status exception: java.lang.NullPointerException.
  PIPE: plugin read: status exception: java.lang.NullPointerException.
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback return
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback: setting status Start: applet not initialized.
  PIPE: plugin read: status Start: applet not initialized.
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback return

```
These are the errors I get when I load it.
Any help?

FYI, I'm on 64

---

### Post by jualin on 2008-08-17
Try installing the ubuntu-restricted-extras which comes with Java (propietary) and many other plugins that you may need in the future. To do this via Synaptic just look for the package or via terminal > sudo apt-get install ubuntu-restricted-extras Hope this helps!

---

### Post by MarshyTheKid on 2008-08-17
> **jualin said:**
> Try installing the ubuntu-restricted-extras which comes with Java (propietary) and many other plugins that you may need in the future. To do this via Synaptic just look for the package or via terminal  Hope this helps!

I already have ubuntu-restricted-extras installed.

---

### Post by oldsoundguy on 2008-08-17
down the page on these guides are tips for installing all sorts of things into Firefox.

As a matter of fact, the guides themselves are very handy to keep bookmarked in order to get all of your basic items in your build installed.

[http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=Wvs&q=+site:ubuntuguide.org+ubuntuguide.org&sa=X&oi=smap&resnum=1&ct=more-results](http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=Wvs&q=+site:ubuntuguide.org+ubuntuguide.org&sa=X&oi=smap&resnum=1&ct=more-results)

---

### Post by alzie on 2008-08-17
I'd check in synaptic package manager to see which java is currently installed by searching for java.

If its icedtea-java mark them for removal and apply
Then search for sun-java.
Mark sun-java6-plugin for install and apply.  It should automatically pick up sun-java6-jre and sun-java6-bin.

Personally I'm using sun-java5 because of some flash issues at a games site.  I don't know if this will be an issue for you.

I hope this helps.

---

### Post by MarshyTheKid on 2008-08-17
> **alzie said:**
> I'd check in synaptic package manager to see which java is currently installed by searching for java.

If its icedtea-java mark them for removal and apply
Then search for sun-java.
Mark sun-java6-plugin for install and apply.  It should automatically pick up sun-java6-jre and sun-java6-bin.

Personally I'm using sun-java5 because of some flash issues at a games site.  I don't know if this will be an issue for you.

I hope this helps.
Hmm. I had the icedtea installed
I can't find the java plugin though. I have bin and jre already installed.

---

### Post by alzie on 2008-08-17
Do you have restricted and multiverse repositories enabled in symantic?

You should have sun-java available if you do.

---

### Post by MarshyTheKid on 2008-08-17
> **alzie said:**
> Do you have restricted and multiverse repositories enabled in symantic?

You should have sun-java available if you do.

I have both enabled.
I have sun-java, but not sun-java plugin.
I have java6-bin and java6-jre enabled.

---

### Post by MarshyTheKid on 2008-08-17
Hmm. When I try to install sun-java6-plugin from the terminal I get

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

```

---

### Post by alzie on 2008-08-17
I just double checked my symantic,  you should have " sun-java6-plugin " listed there.

---

### Post by MarshyTheKid on 2008-08-17
Anyone know how I can get that package back in my symantic?

---

### Post by MarshyTheKid on 2008-08-18
Hmm. I'm trying to get to the package on ubuntus site and it is not loading. I'm wondering if that is why I can't download it, or what.

---

### Post by jualin on 2008-08-18
Can you post your sources list file. Go to the terminal and type > cat /etc/apt/sources.list
And also, what version of Ubuntu are you using?

---

### Post by MarshyTheKid on 2008-08-18
> **jualin said:**
> Can you post your sources list file. Go to the terminal and type 
And also, what version of Ubuntu are you using?

Hardy x64
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security multiverse

```

---

### Post by jualin on 2008-08-18
Your sources lists seem fine, maybe since you are using the 64 bit version of Ubuntu Java is having problems. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java"), maybe it could help you out.

---

### Post by MarshyTheKid on 2008-08-18
> **jualin said:**
> Your sources lists seem fine, maybe since you are using the 64 bit version of Ubuntu Java is having problems. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java"), maybe it could help you out.

:( I was afraid it might come to this. I was weary of using 64 Ubuntu because with Gutsy I had so many issues with Java and had to go that route. But I had heard that 64 bit Java was working for Ubuntu now so I gave it another shot.
I don't see how that would make a difference on whether or not I could get or see the package though. When I go to packages.ubuntu.com it is very slow and takes a long time to load a simple page.

I hadn't searched enough before posting. Apparently nobody else can get java to work on x64. I am tempted to just install 32bit Ubuntu and erase my amd64 rather than dealing with this everytime. At least this time I can get java on my machine, just not the java plugin. I don't know what the developers where thinking when they said that they were going to support Ubuntu and have a real release, then just leaving out amd64 plugins.

---

### Post by jualin on 2008-08-18
I thimk that the link I gave you tells you how to install 32 bit Java on 64 bit Ubuntu.

---

### Post by vgrisham on 2009-05-18
This has nothing to do with 32-bit vs 64-bit. I have both, and I get this problem occasionally on a few websites using Firefox.

---

