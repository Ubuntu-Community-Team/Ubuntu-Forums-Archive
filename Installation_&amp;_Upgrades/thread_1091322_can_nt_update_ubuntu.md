---
title: "can nt update ubuntu"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by ewientje on 2009-03-09
Hi, I&#7743; new to ubuntu, just installed ubuntu, and after trying to update , I get the following message, What am I doing wrong.

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/tualatrix/ubuntu/dists/intrepid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by albandy on 2009-03-09
You've modified the repositories with launchpad entries. 
Go to synaptic and disable the third party repositories you've added

---

### Post by ewientje on 2009-03-09
I have never modified the repositories with launchpad. Don t know what they are, and where to find them. And what is synaptic ?
I&#7743; kind of new to Linux, so ??

---

### Post by albandy on 2009-03-09
please, open /etc/apt/sources.list and paste the contents here.

---

### Post by ewientje on 2009-03-09
I reinstalled Ubuntu with another iso, and now I can update, so the problem is solved.
Thank you all for your help.

---

### Post by Neo_The_User on 2009-03-09
heh reinstall works too.

---

