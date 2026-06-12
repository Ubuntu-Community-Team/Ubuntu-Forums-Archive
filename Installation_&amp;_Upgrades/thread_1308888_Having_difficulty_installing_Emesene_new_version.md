---
title: "Having difficulty installing Emesene new version"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Shahnawaz on 2009-11-01
Hi, I'm new to Ubuntu, I just switched to Ubuntu yesterday and after a hard time, I'm able to run my webcam and can run some unsupported music and videos by installing codecs and installing real player.

But now I want to use Emesene 1.5-1, and I'm getting this error, when I'm installing Emesene 1.5-1 from repositories of Synaptic Package Manager.

When I add this, nothing happens:
deb [http://mirrors.kernel.org/ubuntu](http://mirrors.kernel.org/ubuntu) Karmic Koala

But when I replace Karmic Koala with karmic main universe, it comes in the list but after refreshing, I get this error:

Failed to fetch [http://cz.archive.ubuntu.com/ubuntu/dists/Karmic/Koala/binary-i386/Packages.gz](http://cz.archive.ubuntu.com/ubuntu/dists/Karmic/Koala/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.rootguide.org/ubuntu/dists/Karmic/Koala/binary-i386/Packages.gz](http://mirror.rootguide.org/ubuntu/dists/Karmic/Koala/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.kernel.org/ubuntu/dists/Karmic/Koala/binary-i386/Packages.gz](http://mirrors.kernel.org/ubuntu/dists/Karmic/Koala/binary-i386/Packages.gz)  404  Not Found [IP: 130.239.17.6 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I tried installing the older version of Emesene from Ubuntu Software Center, but it doesn't support webcam and it asked me to install libmimic
I tried to install the newer version from .deb file, but it recommend me to install from channels.

Thanks for your help in advance.

---

### Post by basotl on 2009-11-02
> **Shahnawaz said:**
> Hi, I'm new to Ubuntu, I just switched to Ubuntu yesterday and after a hard time, I'm able to run my webcam and can run some unsupported music and videos by installing codecs and installing real player.

Have you set up the Medibuntu repository? It's great for resricted codecs.

> **Shahnawaz said:**
> But now I want to use Emesene 1.5-1, and I'm getting this error, when I'm installing Emesene 1.5-1 from repositories of Synaptic Package Manager.

When I add this, nothing happens:
deb [http://mirrors.kernel.org/ubuntu](http://mirrors.kernel.org/ubuntu) Karmic Koala

Where did you get that repo from? it doesn't look familar. As an FYI normally it would just end with karmic.

> **Shahnawaz said:**
> But when I replace Karmic Koala with karmic main universe, it comes in the list but after refreshing, I get this error:

Failed to fetch [http://cz.archive.ubuntu.com/ubuntu/dists/Karmic/Koala/binary-i386/Packages.gz](http://cz.archive.ubuntu.com/ubuntu/dists/Karmic/Koala/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.rootguide.org/ubuntu/dists/Karmic/Koala/binary-i386/Packages.gz](http://mirror.rootguide.org/ubuntu/dists/Karmic/Koala/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirrors.kernel.org/ubuntu/dists/Karmic/Koala/binary-i386/Packages.gz](http://mirrors.kernel.org/ubuntu/dists/Karmic/Koala/binary-i386/Packages.gz)  404  Not Found [IP: 130.239.17.6 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Your pointing that to a repo line that doesn't exist.

I would install it from the source tarball [http://www.emesene.org/download.html](http://www.emesene.org/download.html) or use aMSN.

Thanks for your help in advance.[/QUOTE]

---

### Post by Shahnawaz on 2009-11-02
> **basotl said:**
> Have you set up the Medibuntu repository? It's great for resricted codecs.

Yes, I do. I've installed medibuntu-keyring, amrnb, libammb3, and w32codecs from it.

> Where did you get that repo from? it doesn't look familar. As an FYI normally it would just end with karmic.I got this repo from the same website you gave me. Like, I opened [http://www.emesene.org/download.html](http://www.emesene.org/download.html) 
and then I clicked on 
[Ubuntu (1.5) you can use the Debian package meanwhile ]("http://packages.ubuntu.com/karmic/emesene")
It showed this page:
[http://packages.ubuntu.com/karmic/emesene](http://packages.ubuntu.com/karmic/emesene)
I scrolled down the window, and clicked on **all** under Download Emesene and it showed another page with a list of mirrors. This is the page:
[http://packages.ubuntu.com/karmic/all/emesene/download](http://packages.ubuntu.com/karmic/all/emesene/download)
I tried all the mirrors of Asia and a few more.


> Your pointing that to a repo line that doesn't exist.Maybe, I don't know how to install that repo from that website.

>  I would install it from the source tarball [http://www.emesene.org/download.html](http://www.emesene.org/download.html) or use aMSN. I tried aMSN, it wasn't working and it hanged, because I've like more than 1500 contacts in my MSN, so whenever I tried to log in, I had to keep accepting add requests. It took hours but the add requests still showing up. But now I've made another new MSN email, and tried to log on with it. I even tested my webcam, and my friend could see me. But haven't tried to see somebody on cam on aMSN yet.

Thanks for your help.
Hope to hear from you soon

Shahnawaz

---

### Post by Shahnawaz on 2009-11-02
As you said, it usually ends with Karmic.
I tried that way too:
I tried to add:
**deb [http://*cz.archive.ubuntu.com/ubuntu](http://*cz.archive.ubuntu.com/ubuntu)* karmic**

in the repository, it asked me to reload and this happened:

[FONT=Verdana]
[B]Could not download all repository indexes
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.[/B]

and then

[B]An error occurred
The following details are provided:
E: Malformed line 47 in source list /etc/apt/sources.list (dist parse)
E: Unable to lock the list directory[/B]

and then

[B]An error occurred
The following details are provided:
E: Malformed line 47 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

[/B][/FONT]

---

