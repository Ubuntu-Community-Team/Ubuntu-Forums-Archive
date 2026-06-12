---
title: "replacement for beagle"
date: 2008-07-23
forum: General Help
---

### Post by orrorin on 2008-07-23
On my Feisty installation, I had the beagle extension for firefox, which allowed me to search my web history (i.e. web pages that I had visited) so I could find a webpage based on some keyword.

The beagle indexer does not work with Firefox3 for some reason and no one seems to be working on it.

So, what are my alternatives on Hardy?

---

### Post by dbera on 2008-07-23
You can get the updated extension which is FF3 compatible from [http://beagle-project.org/files/0.3/](http://beagle-project.org/files/0.3/) (this is the same version that is available in Intrepid)

---

### Post by orrorin on 2008-07-23
Thanks dbera; it works. BTW, where can I find a .svg for beagle so I can use it on app launcher for gnome?

---

### Post by orrorin on 2008-07-23
BTW, when I goto my.yahoo.com, it complains ... "Fail to write content/metadata, Would you like to disable beagle now?". Since this is the home page for my FF3, this is kind of painful.

Hitting Cancel ignores the warning.

---

### Post by dbera on 2008-07-24
I will reply both.

svg are here
[http://svn.gnome.org/viewvc/beagle/trunk/beagle/logo/](http://svn.gnome.org/viewvc/beagle/trunk/beagle/logo/)

the warning problem was fixed in the 0.3.8 version. Intrepid has 0.3.7 and thats the version online. I dont know when Ubuntu will have the new version. If you want, download the Debian package for 0.3.8 and use it.

---

### Post by orrorin on 2008-07-24
Thanks again.

Interestingly enough when I try this on on Fedora 9 machine, which is running ForeFox 3.0.1, I don't get the warning for my.yahoo.com. So, I'll wait until Ubuntu makes Firefox 3.0.1 available.

Strangely though on Fedora 9/FF3.0.1, I'm not sure if the indexing is working. Running beagle-search doesn't hit any web-page that I've visited (unlike ubuntu) and .beagle/Indexes doesn't show any entry for FireFoxIndexes (I presume that would be the name).

---

### Post by orrorin on 2008-07-24
It is now working in Fedora 9 as well after the following addition to /etc/sysctl.conf and a reboot.

```
# as recommended by beagle-search
fs.inotify.max_user_watches = 65535
```

---

### Post by dbera on 2008-07-24
> **orrorin said:**
> ) and .beagle/Indexes doesn't show any entry for FireFoxIndexes (I presume that would be the name).

Just for future debugging, firefox webpage indexes are in Indexes/IndexingServiceIndex. I know its weird :-).

And a new beagle-1.1.1.xpi is available at the beagle-project.org link given above. This one is based on beagle-0.3.8.

---

