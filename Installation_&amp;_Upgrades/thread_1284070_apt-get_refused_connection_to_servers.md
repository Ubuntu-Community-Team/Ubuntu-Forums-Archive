---
title: "apt-get refused connection to servers"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by ram57 on 2009-10-06
I recently installed 9.04.  All was working well, but at some point apt-get stopped working.  I would appreciate any insights into resolving this problem.  Below is the output from running apt-get update.

Thank you for your help.

sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_US
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_US
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]
Reading package lists...
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:8080 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 8080]

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

