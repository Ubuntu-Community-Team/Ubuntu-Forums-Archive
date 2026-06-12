---
title: "apt-get/synaptic and the Proxy Problem"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by ShepHeard on 2008-12-09
Hi everyone,

I'm trying to get my Ubuntu 8.10 installation to update at work. However, we have to go via an automatic proxy configuration script ([http://www.uct.ac.za/cache.pac](http://www.uct.ac.za/cache.pac)). This also requires authentication with my username and password.

This is fine for FireFox, you just add it to the network settings and it asks for the log in details whenever I open FF.

However, when I use sudo apt-get update I get 404 errors, e.g. text

> Ign [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) intrepid-updates Release.gpg
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
  404 Not Found
Ign [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) intrepid-updates/main Translation-en_US
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
  404 Not Found

and

> Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) intrepid-security/multiverse Sources
  404 Not Found
W: Failed to fetch [http://ppa.launchpad.net/psyke83/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/psyke83/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/psyke83/ubuntu/dists/intrepid/main/source/Sources.gz](http://ppa.launchpad.net/psyke83/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found

With Synaptic, I get the same issues:

> W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to ubuntu.mirror.ac.za http:

W: Failed to fetch [http://ppa.launchpad.net/psyke83/ubuntu/dists/intrepid/Release.gpg](http://ppa.launchpad.net/psyke83/ubuntu/dists/intrepid/Release.gpg)  Could not connect to ppa.launchpad.net:80 (91.189.90.217), connection timed out

W: Failed to fetch [http://ppa.launchpad.net/psyke83/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/psyke83/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Unable to connect to ppa.launchpad.net http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

I have tried adding the config script to System/Preferences/Network Proxy but this doesn't help.

I've also added 

```
# to try and resolve proxy issue:
export http_proxy="http://usrnm:pwrd8@www.uct.ac.za/cache.pac"
```

to /etc/bash.bashrc

but to no avail.

It seems to work fine at home, so pretty sure it's an issue with the proxy.. Though it doesn't give a 407 authentification error... Could it actually be a problem with the uni firewall?

It would be the ultimate irony as the Ubuntu repos are on a server somewhere on the site (I'm at UCT, South Africa)!

Any ideas?

---

### Post by albinootje on 2008-12-09
You could talk to the tech-department about this. But why not try another local mirror first to test whether it is really a firewall-issue at the uni ?

---

### Post by ShepHeard on 2008-12-09
Hi - cheers for the reply.

Yeah, I'm pretty sure I'd already tried another a while back (including the default one). Plus, it works fine on my home network...


...

---

### Post by bapoumba on 2008-12-09
That is quite strange. I use a .pac automatic proxy at my univ and have no trouble updating/upgrading. But it does not ask for authentication. Would it happen to be an ISA proxy?

---

### Post by ShepHeard on 2008-12-10
Hi - thanks for the reply..

To be honest I'm not sure - I'll drop a mail to the IT guys..

Cheers

---

### Post by ShepHeard on 2008-12-10
Yeah, it's an ISA proxy... 

To use ISA proxies, we should use a programme such as cntlm. However, apparently I don't want apt-get to go through that as it'll cane my usage quota...

---

