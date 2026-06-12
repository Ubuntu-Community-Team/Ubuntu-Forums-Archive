---
title: "MonoDevelop IDE is not there in repo . what to do?"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by amarshukla123 on 2009-08-20
Hi,
I have recently switched to ubuntu 9.04 and I want to use monodevelop IDE but it doesn't come  by default.So When I tried to search in Synaptic manager I couldn't get monodevelop there and even I tried to install using terminal like this- 
sudo apt-get install monodevelop

then it gives me error saying- E: Couldn't find package monodevelop

Now how can I install it please help.

---

### Post by Copernicus1234 on 2009-08-20
Perhaps its named something else. Try "sudo apt-cache search monodev" and see what you get.

Edit: I just noticed I can see it and Im running 9.04. You probably need to add extra repositories. Check so that all repositories except source code is checked in the settings for the update manager.

---

### Post by amarshukla123 on 2009-08-20
Ya already I had checked them. Thats why I am wondering why its not showing monodevelop even other mono related libraries are there in ubuntu.I don't know whats wrong . Its really annoying.Any way to resolve this ?

---

### Post by Findarato on 2009-08-20
It is available in the repositories, I recently installed it myself. Did you try searching through the "add / remove" ? That's how I found it.

---

### Post by directhex on 2009-08-20
Under System/Administration/Software Sources, ensure you have the Universe repo enabled.

And click [here](apt:monodevelop) to install

---

### Post by amarshukla123 on 2009-08-20
I couldn't find anywhere . Something is wrong it seems with my machine. I installed it today only though. Anyways closing this thread as I am going to install from source the newest version.

---

### Post by directhex on 2009-08-20
> **amarshukla123 said:**
> I couldn't find anywhere . Something is wrong it seems with my machine. I installed it today only though. Anyways closing this thread as I am going to install from source the newest version.

You're gonna break everything, but it's your call.

---

### Post by amarshukla123 on 2009-08-20
No other way left as this dumb OS is not showing it in repos even all repos are enabled.Is any expert here who can help me to solve this problem .I can send any log or anything what is required but Please help me to resolve .

---

### Post by Copernicus1234 on 2009-08-20
Is it the OS that is dumb when the OS shows the package for all the rest of us? Or is it you that somehow have the wrong settings for your system? What do you think? :)

Anyway, there must be something with your software sources that is not configured correctly. The package is in there. But how to fix it? Well, maybe you can reset the repository settings to default installation settings.

---

### Post by Partyboi2 on 2009-08-20
> **amarshukla123 said:**
> No other way left as this dumb OS is not showing it in repos even all repos are enabled.Is any expert here who can help me to solve this problem .I can send any log or anything what is required but Please help me to resolve .
If you are still having problems installing the package from the Ubuntu repos can you open a terminal (Applications>Accessories>Terminal) and post your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by directhex on 2009-08-20
> **amarshukla123 said:**
> No other way left as this dumb OS is not showing it in repos even all repos are enabled.Is any expert here who can help me to solve this problem .I can send any log or anything what is required but Please help me to resolve .

What happened when you clicked my link?

---

### Post by amarshukla123 on 2009-08-20
Ok here is the content of sources.list


# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse

---

### Post by amarshukla123 on 2009-08-20
> **directhex said:**
> What happened when you clicked my link?


When I clicked at ur link it says Firefox doesn't know how to open apt.

---

### Post by directhex on 2009-08-20
> **amarshukla123 said:**
> When I clicked at ur link it says Firefox doesn't know how to open apt.

That's odd. The apt-url association should be put in place on a standard install.

From a console, how about "aptitude install monodevelop"?

---

### Post by amarshukla123 on 2009-08-20
> **directhex said:**
> That's odd. The apt-url association should be put in place on a standard install.

From a console, how about "aptitude install monodevelop"?

"Aptitude install monodevelop" also gave the same error package couldn't find but now anyhow I am able to install it so my problem is solved .

Thanks alot for replying but some guys just boast around showinf their passion towards a particular technology/OS but in knowledge they are FAKE.

Thanks alot to all who gave me positive replies:)

---

