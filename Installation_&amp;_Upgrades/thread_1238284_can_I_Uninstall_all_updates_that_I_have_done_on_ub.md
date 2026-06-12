---
title: "can I Uninstall all updates that I have done on ubuntu 9.04 ?"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by anoop.singh.knit on 2009-08-12
[B]After I am unable to download any software and it is giving following error. 
please tell what this error means and how could I correct it.This happened After installing updates .Not all updates were install some are still remaining .[/B]
_**Thanks ....**_



W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures were invalid: NODATA 1 NODATA 2  


W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.canonical.com](http://archive.canonical.com) jaunty Release: The following signatures were invalid: NODATA 1 NODATA 2  

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release: The following signatures were invalid: NODATA 1 NODATA 2  

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

 W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-backports Release: The following signatures were invalid: NODATA 1 NODATA 2 

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-proposed Release: The following signatures were invalid: NODATA 1 NODATA 2  

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/Release)    W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release)    W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release) 

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release)    W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/Release](http://archive.canonical.com/ubuntu/dists/jaunty/Release)    W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/Release](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/Release)    
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by raymondh on 2009-08-12
Try changing the server source and then run update again. See if it downloads.

---

