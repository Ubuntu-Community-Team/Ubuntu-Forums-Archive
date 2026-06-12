---
title: "Is rsync even useful for package mirror?"
date: 2008-10-13
forum: General Help
---

### Post by shaggy999 on 2008-10-13
So I've been mirroring the ubuntu repositories for a long time using apt-mirror, which is really easy to setup and maintain but it uses wget which isn't as efficient as rsync. In my research to reduce bandwidth usage I had read that debmirror allows for the use of the rsync protocol and it just so happens that the closest mirror that I use (osuosl.org) supports the rsync protocol.

So I whipped up a script to grab the repositories via rsync but at the end when it shows that stats it always ends up with a speedup of 1.0, meaning no speedup at all. I'm thinking this is probably because with each new version of a package a completely new package is generated and rsync isn't smart enough to to just download the difference... which means rsync is not able to actually reduce my bandwidth at all. Is this understanding correct? If so, I'll just go back to apt-mirror. For reference, here's the command I run:

debmirror --host=$HOST --method=$METHOD --dist=$DIST --section=$SECTION --arch=$ARCH --root=:ubuntu --nosource --progress --nocleanup --ignore-small-errors -v $DEST

where $HOST = rsync.osuosl.org, $METHOD = rsync, $DIST = hardy, $SECTION = main,restricted,universe,multiverse, $ARCH = i386 and $DEST is the location where my local mirror is.

---

