---
title: "enable kde3 only repositories on Jaunty"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by zenkaon on 2009-04-21
Hello all,

In a few days I am going to be upgrading to ubuntu 9.04, really looking forward to it. I used to be a kde man, from 1999 onwards until kde4 came out, when I switched to gnome crying "Why did they break kde??:("

I have heard that there will be a kde3 remix of kubuntu, which is great in my opinion as kde4 is no way near ready.

I still prefer some kde apps, like kdevelop (which wants konsole), amarok, digikam, k3b etc. and I want the kde3 versions. In ubuntu 8.10 I have been using kde4 apps and I really want to go back to the stable, reliable, familiar kde3 versions.

So my question is this, how do I configure aptitude to only look at the kde3 repositories and completely ignore the kde4 ones? So when I 
```

sudo aptitude install amarok kdevelop

``` 
I get the kde3 versions.

---

### Post by apparle on 2009-04-21
You can check this news
[https://wiki.kubuntu.org/Kubuntu/Kde3/Jaunty](https://wiki.kubuntu.org/Kubuntu/Kde3/Jaunty)
I don't know how to do what you  have asked .
I searched in packages.ubuntu.com and didn't find old amarok.
But KDE4.2.x is pretty stable, give it another chance.

---

### Post by zenkaon on 2009-04-21
Hi apparle,

Fair enough, kde4.2.x may be stable. I am pretty much convinced that I'm going to be using gnome as my desktop for the foreseeable future, but with some KDE apps - the most important of which is kdevelop. I don't like the look and feel of KDE4 apps (personal taste) and just want to stick to KDE3.

For example, in 8.10 kdevelop has no konsole as konsole has moved to KDE4 and this version doesn't work in the KDE3 kdevelop. I've tried the KDE4 version of kdevelop but I don't like the look and feel.

I want to carry on with the advances in ubuntu, I really like what is happening to gnome. At the same time I want to cling onto KDE3 for as long as possible. My personal preference would be that KDE 3.5.10 repositories stay an option for a long long time to come (ubuntu 11.04 at least)

---

### Post by louieb on 2009-04-21
Just a thought. Once you get the KDE3 version of the apps installed, open Synaptic, select the app, then Package>Lock version.  
This should prevent those apps from being upgraded when you move to Jaunty.

---

### Post by zenkaon on 2009-04-21
Hi louieb,

I will certainly do that. I think I am going to go for a fresh install on my work machine as I want to use the ext4 filesystem. I've been using the beta 9.04 on a test machine and am liking the filesystem. Also, my work machine has upgraded distributions a few times now and feels a bit cluttered. I always like a fresh install - nice and lightweight.

I'd ideally like no KDE4 packages whatsoever on the fresh install, KDE3 only. I imagine that I have to edit /etc/apt/sources.list but it's what to put in there and what to remove that is the question.

---

### Post by madscientist159 on 2009-04-22
> **zenkaon said:**
> Hello all,
So my question is this, how do I configure aptitude to only look at the kde3 repositories and completely ignore the kde4 ones? So when I 
```

sudo aptitude install amarok kdevelop

``` 
I get the kde3 versions.

All the KDE3 apps now have a -kde3 suffix appended.  For example, to install the KDE3 version of Amarok from now on, you would install amarok-kde3 instead of amarok, kdevelop becomes kdevelop-kde3, etc.  Then, just remove the KDE4 version of those apps (amarok and kdevelop in this example).

For all kinds of KDE3 info, take a look at this Wiki page:
[https://wiki.kubuntu.org/Kubuntu/Kde3/Jaunty](https://wiki.kubuntu.org/Kubuntu/Kde3/Jaunty)

Enjoy!:)

---

### Post by zenkaon on 2009-04-23
Thanks madscientist159,

great news, nice and easy. 

kde3 is dead, long live kde3

---

### Post by luke2760 on 2009-04-26
Where are those in the repos? I see amarok, and amarok-kde4, which seem to be the same package. Do I have to download the remix RC cd and install off that?

---

### Post by Nxx on 2009-06-24
deb [http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu](http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu) jaunty main

---

