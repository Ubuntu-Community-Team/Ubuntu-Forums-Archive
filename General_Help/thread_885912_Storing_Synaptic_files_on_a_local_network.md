---
title: "Storing Synaptic files on a local network?"
date: 2008-08-10
forum: General Help
---

### Post by Zeotronic on 2008-08-10
In my household there are several computers networked together which use Ubuntu, and we all connect to an internet connection with a limited 30 day bandwidth... in order to keep the bandwidth down, I was wondering if there was any way to download synaptic files from another computer on the network which had already downloaded them, rather than from the internet. It would save us bandwidth, and a little bit of time... it would probably be at the expense of hard drive space wouldn't it (?), but I still think it would be worth it. Is there any way to do this? I would imagine there is, but obviously I don't know how.

---

### Post by billmc on 2008-08-10
Start up Synaptic and do a search on mirror.  It'll bring up a number of different types of mirror programs, I think you're looking for apt-mirror.  Personally, I've never used it, I have been using Debmirror and creating a local mirror for the distrubution I'm interested in.  Currently, I'm not downloading source files and I am dowloading binaries for i386 and amd64 for the Hardy distro.  My mirror is approximately 36 G.

---

### Post by InfinityCircuit on 2008-08-10
I think that you can do this with NFS.  If you set one computer to mount /var/cache/apt/archives on an NFS volume, you could mount that same NFS by the other computers.  Then they would all download updates into the same directory and use the same cache.

---

