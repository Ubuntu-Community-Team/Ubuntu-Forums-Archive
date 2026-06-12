---
title: "Sources update a mess"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by espressobeanie on 2009-10-30
I updated from 9.04 to 9.10. I cant seem to update any software through the repositories after that. I get this error msg: 
[
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
]
And...
[
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release](http://archive.ubuntu.com/ubuntu/dists/karmic/Release)  Unable to find expected entry  partner/binary-amd64/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
]

I checked the Software Sources.  Under "Ubuntu Sources" tab, the Karmic 9.10 CD shows up and the download from is listed as "Main". Under the Other Software tab, there was nothing. I added a 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner' line, so partners is in there. 

However, this still didn't work. I then tried apt-get update, and received this error: 
[
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
]

Does anyone know what I should do?

---

