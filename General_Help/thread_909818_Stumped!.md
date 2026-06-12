---
title: "Stumped!"
date: 2008-09-03
forum: General Help
---

### Post by Pandyrenim on 2008-09-03
I still haven't been able to figure this problem out. its still giving me the same error message and i don't see any of that in my list.

------------------------------------------------------------------
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://security.ubuntu.com/ubuntu/di...curity/Release](http://security.ubuntu.com/ubuntu/di...curity/Release) Unable to find expected entry deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

I don't know what do to :confused:

---

### Post by Locutus_of_Borg on 2008-09-03
"http://security.ubuntu.com/ubuntu/di...curity/Release"
is not the correct address

check your /etc/apt/sources.list and put the correct full address there
then update again

---

### Post by Pandyrenim on 2008-09-04
ttp://security.ubuntu.com/ubuntu/dists/hardy-security/Release

thats the full address

plus the h in front it kept shortening it

---

### Post by Oldsoldier2003 on 2008-09-04
try changing mirrors in System>Administration>Software Sources. there may a transient problem with that particualr mirror

---

