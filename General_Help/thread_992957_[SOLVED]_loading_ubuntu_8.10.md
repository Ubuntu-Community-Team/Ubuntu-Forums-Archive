---
title: "[SOLVED] loading ubuntu 8.10"
date: 2008-11-25
forum: General Help
---

### Post by Nailhac on 2008-11-25
When loading ubuntu 8.10 do I overwrite my previous version 8.04 Hardy Heron or do I fresh instal? I would appreciate any advice.:(

---

### Post by CatKiller on 2008-11-25
I've always done the [network upgrades]("http://www.ubuntu.com/getubuntu/upgrading") (from Hoary to Intrepid, that I'm on now) without any problems.

If you've got your [/home as a separate partition]("http://www.psychocats.net/ubuntu/separatehome"), you can install 8.10 to your / partition, and still keep your data and configuration files. As I understand it, you'll need to re-add your users in the same order, and re-install any applications you've currently got installed that aren't included by default.

If you haven't got your /home as a separate partition, re-installing will also knock out all of your personal data and settings.

So personally, I would back up any data that I wanted to keep, then do the upgrade to 8.10, and if it didn't work for some reason, I would go for a fresh install and restore my data.

Of course, you don't **have** to upgrade to 8.10 unless it has features that you want. 8.04 is a Long Term Support release, which means that you'll continue to get security updates and bugfixes for some time yet.

---

### Post by Nailhac on 2008-11-26
Thanks Catkiller. I may have a rethink as I understand it is not compatable with openoffice.org 3

---

### Post by CatKiller on 2008-11-26
It doesn't come with OpenOffice.org 3.0, since it wasn't released in time before the release of the latest version of Ubuntu. It'll be in the next one though. And I understand that you can get a .deb from [www.openoffice.org](www.openoffice.org) if you want to install it. I haven't tried it though, since I don't use documents that much.

---

