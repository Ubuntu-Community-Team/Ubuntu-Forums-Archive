---
title: "I need help updating"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by Bark N on 2009-04-17
Hi i'm new to ubuntu and i'm using ubuntu 8.10 i want to install wine but when i try to install it i get a message that says: "Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release)  Unable to find expected entry  multiversedeb/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Please help :confused::confused:

---

### Post by Therion on 2009-04-17
Go to System/Administration/Software Sources/Third Party Software (tab).

Enable the first four repositories [as seen here](http://www.davestechsupport.com/blog/images/softwaresources.png).

Exit, Reload, and look for Wine again under Add/Remove in the Applications menu.

---

