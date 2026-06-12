---
title: "KeePass 2 packaging"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by yhrn on 2009-09-10
Since [KeePass 2]("http://keepass.info/") runs on Mono 2.2 and higher I was thinking that it might be nice if it was made available through a repository for Karmic (which, I believe, includes the necessary Mono version). I've looked around and didn't find it anywhere. Does anybody know if KeePass 2 is in any repository? If not - is there any way of getting it in to one?

---

### Post by directhex on 2009-09-10
> **yhrn said:**
> Since [KeePass 2]("http://keepass.info/") runs on Mono 2.2 and higher I was thinking that it might be nice if it was made available through a repository for Karmic (which, I believe, includes the necessary Mono version). I've looked around and didn't find it anywhere. Does anybody know if KeePass 2 is in any repository? If not - is there any way of getting it in to one?

There's no package because nobody has made a package.

If it's 100% distributable Free Software (i.e. the source code is available for download and doesn't contain any pre-compiled .dll files of questionable provenance) then a package COULD be prepared by an interested party.

---

### Post by yhrn on 2009-09-10
It's licensed under GPLv2. I've had a look at the source package and it seems to be completely without precompiled external dependencies. The old 1.X port of KeePass (KeePassX) is already available in the repositories but it is nowhere close to the newer versionsof KeePass when it comes to functionality.

I've seen requests for packaging of other applications in Launchpad but I felt that I (as a noob) should ask around a bit before opening a bug there. Is that the way to go?

---

### Post by directhex on 2009-09-10
> **yhrn said:**
> It's licensed under GPLv2. I've had a look at the source package and it seems to be completely without precompiled external dependencies. The old 1.X port of KeePass (KeePassX) is already available in the repositories but it is nowhere close to the newer versionsof KeePass when it comes to functionality.

I've seen requests for packaging of other applications in Launchpad but I felt that I (as a noob) should ask around a bit before opening a bug there. Is that the way to go?

directhex@desire:/tmp/keeeeeeee$ find . -iname *.exe
directhex@desire:/tmp/keeeeeeee$ find . -iname *.dll
./Build/KeePassLibSD_Distrib/KeePassLibSD.dll
./Build/KeePassLib_Distrib/KeePassLib.dll

Not as clean as all that. Seems to build without those files though

Some light patching is needed to make it compile, mostly fixing hard-coded paths in the .resx files (and removing a couple of bad imports in the csproj). Doesn't look like too much of an ordeal to package, other than the politics involved in WinForms apps.

HOWEVER.

Two things. Firstly, quality packaging comes from interest - and someone who isn't interested in a package won't really care too much about packaging it well. That's the problem with simply filing a bug on Launchpad and hoping someone picks it up. Secondly, the biggest ordeal in packaging is generating the debian/copyright file, which turns into /usr/share/doc/packagename/copyright - this file MUST be COMPLETE AND ACCURATE or a package will not be accepted into Debian/Ubuntu, and generating the file and ensuring its correctness is a long and boring process. If you want this packaged (and it's too late for Karmic, just FYI) then firstly I'd talk to [email]debian-cli@lists.debian.org[/email] about it, and secondly, I'd strongly recommend that if you don't want to go all the way towards learning to make your own package, then at least generate a debian/copyright file as "doing your bit" to help the packager.

---

### Post by yhrn on 2009-09-11
> **directhex said:**
> directhex@desire:/tmp/keeeeeeee$ find . -iname *.exe
directhex@desire:/tmp/keeeeeeee$ find . -iname *.dll
./Build/KeePassLibSD_Distrib/KeePassLibSD.dll
./Build/KeePassLib_Distrib/KeePassLib.dll

Not as clean as all that. Seems to build without those files though

Some light patching is needed to make it compile, mostly fixing hard-coded paths in the .resx files (and removing a couple of bad imports in the csproj). Doesn't look like too much of an ordeal to package, other than the politics involved in WinForms apps.

HOWEVER.

Two things. Firstly, quality packaging comes from interest - and someone who isn't interested in a package won't really care too much about packaging it well. That's the problem with simply filing a bug on Launchpad and hoping someone picks it up. Secondly, the biggest ordeal in packaging is generating the debian/copyright file, which turns into /usr/share/doc/packagename/copyright - this file MUST be COMPLETE AND ACCURATE or a package will not be accepted into Debian/Ubuntu, and generating the file and ensuring its correctness is a long and boring process. If you want this packaged (and it's too late for Karmic, just FYI) then firstly I'd talk to [EMAIL="debian-cli@lists.debian.org"]debian-cli@lists.debian.org[/EMAIL] about it, and secondly, I'd strongly recommend that if you don't want to go all the way towards learning to make your own package, then at least generate a debian/copyright file as "doing your bit" to help the packager.

Regarding the .dll files, I assumed that they were actually output from building the application since they reside in the Build directory. I might be wrong about that though - they might also be used for some optional native operations I think KeePass support.
I'll look into that and give it a go at [EMAIL="debian-cli@lists.debian.org"]debian-cli@lists.debian.org[/EMAIL] and see what they say.

Thanks for your help.

---

### Post by directhex on 2009-09-11
> **yhrn said:**
> Regarding the .dll files, I assumed that they were actually output from building the application since they reside in the Build directory.

Well, I dunno. They're in the source zip, I didn't build them myself.

---

