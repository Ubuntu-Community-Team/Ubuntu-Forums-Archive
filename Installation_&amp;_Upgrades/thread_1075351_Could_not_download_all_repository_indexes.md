---
title: "Could not download all repository indexes"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by miroslav_karpis on 2009-02-20
Hi, I'm getting a notification 'yellow triangle' - that I should update my ubuntu. After clicking on it I get a message - 'Your system is up-to-date' + The package information was last updated 31 days ago.

Then when I click on 'Check' button I get this error:  

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


pls. what does that mean?

---

### Post by Partyboi2 on 2009-02-20
It means it could find the binary-i386/Packages.gz. To workaround it you can open your Software Sources (System>Admin>Software Sources) and disable the [http://www.getautomatix.com/](http://www.getautomatix.com/) deb repo.

---

### Post by miroslav_karpis on 2009-02-20
helped thnks.....

---

