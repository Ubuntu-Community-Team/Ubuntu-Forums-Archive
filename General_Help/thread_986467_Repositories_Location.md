---
title: "Repositories Location"
date: 2008-11-18
forum: General Help
---

### Post by Cool Javelin on 2008-11-18
Here is a disk usage question.

When I do an apt-get, or use the Synaptic Package Manager (I assume both these functions do the same thing,) and I ask for an application to be installed, where is the package retrieved from?

Was it placed on my hard drive when I installed Xubuntu, or it is retrieved from some repository on the internet in real time?

Because of all the disk activity, I tend to think it is on the hard drive. If so, can I remove the hundreds (if not thousands) of packages from my hard drive and point the install to the internet?

Thanks. Mark

---

### Post by scragar on 2008-11-18
The repo's are online, which repo you download from is decided by a text file on your system( /etc/apt/sources.list ).

As for the disk activity, well that could be a number of things, it downloads the files, maybe that's your suspect disk activity, when it saves it localy to work with, or maybe it's the datase reading/updating tasks it does during the save/update procedure. I can't comment too much on this without any more data.

---

### Post by Yellow Pasque on 2008-11-18
Actually, Synaptic will download the (compressed) package from an Ubuntu server and eventually store it in the /var/cache/apt/archive directory. The disk activity you hear is from dpkg/Synaptic uncompressing and md5summing files (and other scripted tasks).

In Synaptic Package Manager's Preferences (under the Settings menu), there is a File  tab where you can clear/control the cache.

---

