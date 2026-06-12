---
title: "sudo apt-get update error."
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by bhishan on 2009-05-24
When I run " sudo apt-get update " in the terminal I get the following message at the end of the process.

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages)  404 Not Found

W: Failed to fetch [http://apt.boxee.tv/dists/jaunty/main/binary-amd64/Packages](http://apt.boxee.tv/dists/jaunty/main/binary-amd64/Packages)  404 Not Found

How do I fix it?

---

### Post by kerry_s on 2009-05-24
open up synaptic(settings>repositories) and uncheck or delete those repos, there no good.

---

### Post by bhishan on 2009-05-24
But I want to install Skype and Boxee.

---

### Post by whoop on 2009-05-24
> **bhishan said:**
> But I want to install Skype and Boxee.
These repo's do not seem to be online, you should find repo's that are online. In any case these two lines seem to be useless (at least for now).
This one seems ok for skype: [http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html)

As a side note you could also just install them via a deb packages (unless you prefer the repo's, at least I do).

---

### Post by bhishan on 2009-05-24
> **whoop said:**
> These repo's do not seem to be online, you should find repo's that are online. In any case these two lines seem to be useless (at least for now).
This one seems ok for skype: [http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html)

Thanks, I managed to run skype. I deleted both lines. How do I install Boxee? I have Jaunty 64bit.

---

### Post by whoop on 2009-05-24
> **bhishan said:**
> Thanks, I managed to run skype. I deleted both lines. How do I install Boxee? I have Jaunty 64bit.
Try google ;) : 
[http://www.google.nl/search?q=boxee+64+bit+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.nl/search?q=boxee+64+bit+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Here's one:
[http://ossnotebook.blogspot.com/2008/12/how-to-install-boxee-in-ubuntu-64-bit.html](http://ossnotebook.blogspot.com/2008/12/how-to-install-boxee-in-ubuntu-64-bit.html)

Never tried it myself though.

---

