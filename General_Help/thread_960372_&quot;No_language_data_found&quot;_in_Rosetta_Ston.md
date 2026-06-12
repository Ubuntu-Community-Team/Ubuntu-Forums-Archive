---
title: "&quot;No language data found&quot; in Rosetta Stone and WINE."
date: 2008-10-27
forum: General Help
---

### Post by BrendanM on 2008-10-27
So I'm trying to use Rosetta Stone 2.0.8.1A with WINE 1.0.0-1 on Ubuntu 8.04.

The install goes fine, and even the sound appears to work well. However, when I go to load the program, it tells me "No Language Data Found"

I've tried following the suggestions here: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1867](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1867)

I'm running on an EEE PC, so I don't have an optical drive. I've tried mounting the data CD iso
```
sudo mount -t iso9660 -o loop,norock,map=off,ro RS_French.iso /media/isomount/

```
and then configuring WINE to have that mountpoint as the D: drive. I've made sure all the files are uppercase, since some people have suggested that as a problem, and I've also tried mounting it, copying/extracting the files to some other directory and then setting that directory as the D: drive for WINE.

Does anyone have any other ideas/suggestions?

---

