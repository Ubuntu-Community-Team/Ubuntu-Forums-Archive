---
title: "How to get the latest vlc for ubuntu 8.10?"
date: 2008-11-14
forum: General Help
---

### Post by yinglcs2 on 2008-11-14
Hi,

How to get the latest vlc (version 0.9.6) for ubuntu 8.10?

Thank you.

---

### Post by jimmy the saint on 2008-11-14
deb [http://nightlies.videolan.org/build/intrepid-amd64/arch/](http://nightlies.videolan.org/build/intrepid-amd64/arch/)

add that to your souces and you will get the nightly builds.  I don't know that I would recommend it, but it'll get you what you want.  you may want to freeze the version in synaptic so that you are not updating every few days.

---

### Post by thestig_992 on 2008-11-14
vlc should have a .deb file on their homepage (google search to find it). Thats similar to a .exe for windows. Otherwise, make sure you have the latest ubuntu updates, that should have any new vlc updates included.

---

### Post by doas777 on 2008-11-14
is the version in the apt repos not new enough for your needs? mine shows as 0.9.4. 

if you want the very latest direct from videoLAN, just check out these instructions: [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by mc4man on 2008-11-14
I'm using a self built version of 0.9.6 but I'd think you could do a direct download and install from here. Just ck. for any dependency changes from 0.9.4  (shouldn't be very hard to square away if necessary. Vlc-nox would need to match ver. and be installed first.

[http://packages.debian.org/experimental/vlc](http://packages.debian.org/experimental/vlc)


Or you could build or 
temporarily add the appropriate debian repo (just for installing vlc

[http://www.videolan.org/vlc/download-debian.html](http://www.videolan.org/vlc/download-debian.html)

Edit: while I haven't tried the debian package it wouldn't surprise me if 'embedded video' is disabled - it is 'officially' considered 'broken'.

---

### Post by yinglcs2 on 2008-11-15
Actually, I have vlc 0.9.4. But I am looking for a fix which fixes VLC pops up a new window everytime it plays a video. 

I wonder if vlc 0.9.6 fixes that.

---

### Post by mc4man on 2008-11-15
> which fixes VLC pops up a new window everytime it plays a video. 
If you mean "allow only one instance" and or "allow only one running instance", then all the 0.9.x versions have a setting for that. (tools -> preferences -> interface (simple) and main advanced window (all)

There are bugs and regressions in vlc 0.9.x, newer versions are slowly addressing them.

---

### Post by dotancohen on 2008-12-01
> **doas777 said:**
> is the version in the apt repos not new enough for your needs? mine shows as 0.9.4. 

if you want the very latest direct from videoLAN, just check out these instructions: [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

That page just shows how to add Ubuntu's multiverse repo and install from there. Multiverse is a few versions behind, however.

---

