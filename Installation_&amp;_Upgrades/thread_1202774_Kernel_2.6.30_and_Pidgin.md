---
title: "Kernel 2.6.30 and Pidgin"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by zoomy942 on 2009-07-02
So i add the PPA for a pidgin update and run it and I get this error listed below.  i have never seen anything like this and i was wondering if it had to do with my newer kernel.

EDIT : Pidgin did update, i just dont know what this error means.

---

### Post by zoomy942 on 2009-07-02
well, i started removing sources, but now i get this

```
Get:2 http://ppa.launchpad.net jaunty Release [74.7kB]              
Ign http://ppa.launchpad.net jaunty Release                           
Hit http://ppa.launchpad.net jaunty/main Packages                     
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Fetched 308B in 11s (26B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: You may want to run apt-get update to correct these problem
```

---

### Post by stolid_agnostic on 2009-07-02
> **zoomy942 said:**
> well, i started removing sources, but now i get this

```
Get:2 http://ppa.launchpad.net jaunty Release [74.7kB]              
Ign http://ppa.launchpad.net jaunty Release                           
Hit http://ppa.launchpad.net jaunty/main Packages                     
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Fetched 308B in 11s (26B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: You may want to run apt-get update to correct these problem
```

run the following to fix this:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 60D11217247D1CFF

(this assumes that you trust the source, whatever it may be)

then do an update again and an upgrade

---

### Post by zoomy942 on 2009-07-03
Excellent!  thanks, that worked great.

now here is another question.  i searched on google and here but i didnt see anything about it.  on mine, i am using ubuntu 2.6.30 and not the 2.6.....old ones ubuntu comes with.  but update manager still shows this one as an update.  i even did the lock version option in the app manager.

---

