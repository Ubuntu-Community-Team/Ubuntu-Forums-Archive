---
title: "Privoxy and Ubuntu"
date: 2008-10-15
forum: General Help
---

### Post by tmapj on 2008-10-15
Can Debian's Privioxy package be used for Ubuntu?

This is all I have:
[http://sourceforge.net/project/showfiles.php?group_id=11118](http://sourceforge.net/project/showfiles.php?group_id=11118)

---

### Post by patrickballeux on 2008-10-15
> **tmapj said:**
> Can Debian's Privioxy package be used for Ubuntu?

This is all I have:
[http://sourceforge.net/project/showfiles.php?group_id=11118](http://sourceforge.net/project/showfiles.php?group_id=11118)

Have you looked in Synaptic (System - Administration - Package Manager Synaptic)?  All your available softwares can be found there.  And yes, privoxy is availabe via Synaptic.

It is much easier to use Synaptic than a tar.gz file that you need to compile some source code.  Leave that when you really want the bleeding edge last version.

Also, using Synaptic, you will benefit from the automatic update on all your software.  Installing with a tar.gz won't provide you with that great feature.

Good luck!

---

### Post by tmapj on 2008-10-15
According to tor's website, "*Do not use the packages in ubuntu's universe. They are not maintained and most likely old and therefore miss out on stability and possibly security fixes*."

---

### Post by Yellow Pasque on 2008-10-15
The Debian package should be compatible with Ubuntu. If its control file is specifically written for Debian etch (i.e. too picky about dependency versions), you'll find out before you even get a chance to install it.

---

### Post by patrickballeux on 2008-10-15
> **tmapj said:**
> According to tor's website, "*Do not use the packages in ubuntu's universe. They are not maintained and most likely old and therefore miss out on stability and possibly security fixes*."

Hardy version is 3.0.8 and on Sourceforge it is 3.0.10...  There not that old.

I just re-read your post, and had in mind that you were asking about about a source archive and not about a debian package... Sorry.  

Yes, you can install a debian package on ubuntu, but make sure to pick the right architecture (i386 or amd64).  Download the file, and double-click on it, the package system will guide you in the installation...

But doing this, you can get a conflict with a future update of Ubuntu for that package.   But it is not a big deal, and it quite rare that it can give you any serious problems...

As a suggestion, you can have a look at Dansguardian to filter the content of the internet.  Actually, it is better than privoxy when you want to keep the child safe from porn sites.  Is that your goal?

If you only want to block ads, its good, but using "Ad blocker" in firefox is far more easier to setup and more efficient since the browser will not do the call at all to the blocked site.

Good luck!

---

