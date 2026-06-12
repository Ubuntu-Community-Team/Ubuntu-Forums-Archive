---
title: "repositories problem"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by eworman on 2008-12-19
help-Could not download all repository indexes
Hi there. I am facing error message like following when I click upload from Synaptic in version 8.10.

IMHO that must be something with repositories so first of all I tried other's sources.list. The URLs from those files are proved to be valid by connecting them with Firefox. However, I used apt-get update and got error message as following

Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
403 Forbidden
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/...86/Packages.gz) 403 Forbidden

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
cheng@cheng-laptop:/etc/apt$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


Then I resorted to Synaptic. No problem for upload if I untick everything in Settings->Repositories. Then I tick 'Canonical supported Open Source software(main)' and reload. Again I got

'Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/...86/Packages.gz) 403 Forbidden
Some index files failed to download, they have been ignored, or old ones used instead.'

However the URL mentioned here is accessible from my Firefox.


BTW, i had another machine on the same network with 8.04 and never had this kind of problem.


Can anyone kindly give me some suggestion? Many thanks

---

### Post by taurus on 2008-12-19
Do you have any proxy running on that machine?  Did you by any chance install anon-proxy on it?

---

### Post by eworman on 2008-12-19
just checked, no proxy running on this machine.

I am actually using http proxy for web browsing, is that a problem?

thanks anyway

---

### Post by taurus on 2008-12-19
You need to configure the proxy in System -> Administration -> Synaptic Package Manager -> Settings -> Preferences -> Network.

---

### Post by eworman on 2008-12-19
That's a good point. I actually don't know the proxy exactly. I am using automatic proxy configuration, so I only have a .pac file for it. 

Also, I got another machine running on version 8.04 on the office like this one. I tried to have both of them identical network settings and I had no such problem on the 8.04 machine. I checked Network tab of that one, the Proxy Server option is on "Direct connection to the internet"

---

