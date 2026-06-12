---
title: "synaptic ackage manager broken? not working? help"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by new1-2ubun2 on 2009-08-28
when i try and install something from synaptic package manager
in this case krename. i gte an errror message

with this text in the error message:

> W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC6D7D9D009ED615
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 66D5C734F6EFB904
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FEC45DD06899068
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6298AD34413576CB
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D79F61BE8D31A30
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768D
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg](http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused) [IP: 81.171.111.184 80]

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused) [IP: 81.171.111.184 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

i have no idea why this happens. please help. thanks

---

### Post by drs305 on 2009-08-28
You are missing the public keys for those repositories. Try importing them all at once with this command:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6DFBCBAE  7FAC5991  6A423791  0C5A2783 DA6DEEAA 

```
Repeat for any other keys you need. You can use the last eight alphanumeric characters instead of the entire string.

If you already have these keys, try a different server.  This won't fix the wine repository, which is a separate issue.

---

### Post by new1-2ubun2 on 2009-08-28
Thanks :D

that has greatly shrunk the list no i only get this :

> W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg](http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused) [IP: 81.171.111.184 80]

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused) [IP: 81.171.111.184 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.


edit,
when i mark nothing and press reload it downloads 200 odd files and then gives me this error message. is nothing installing?

---

### Post by CHaoSlayeR on 2009-08-28
That is not related to the previous errors.

Try to check in your browser if [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) works. If it doesn't it's either your internet connection or some non-up-to-date DNS servers or the site is completely down for whatever reason.


Greetz,

C]-[aoZ

---

