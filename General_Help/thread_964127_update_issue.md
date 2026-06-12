---
title: "update issue"
date: 2008-10-30
forum: General Help
---

### Post by metalmaniac248 on 2008-10-30
i am being told that i need to manualy check for updates in update manager however when i do this i get this error


> 
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg](http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_GB.bz2](http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_GB.bz2)  Unable to connect to wine.budgetdedicated.com http:

W: Failed to fetch [http://people.ubuntu.com/~doko/OOo2/dists/./deb/http://people.ubuntu.com/~doko/OOo2/binary-i386/Packages.gz](http://people.ubuntu.com/~doko/OOo2/dists/./deb/http://people.ubuntu.com/~doko/OOo2/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://people.ubuntu.com/~doko/OOo2/dists/./deb/.//binary-i386/Packages.gz](http://people.ubuntu.com/~doko/OOo2/dists/./deb/.//binary-i386/Packages.gz)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.



this is also resulting in me not being able to update to intrepid


any ideas 




thanks

---

### Post by ju2wheels on 2008-10-30
Just remove those sources from the Software Sources list and then run the update again.

By the way, those repositories are listed as Gutsy repositories, are you really planning to jump from Gutsy to Intrepid through a single update/ugprade? You might want to back up your stuff because if you are that might not go too well.

---

### Post by metalmaniac248 on 2008-10-30
i am in hardy not gusty

---

