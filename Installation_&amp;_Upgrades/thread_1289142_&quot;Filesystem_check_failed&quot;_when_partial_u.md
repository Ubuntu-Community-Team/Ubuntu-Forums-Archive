---
title: "&quot;Filesystem check failed&quot; when partial upgrading 9.10 beta"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by SergioA on 2009-10-12
Hi there!

I've installed Ubuntu Netbook Remix 9.10 beta on my Asus EeePC 901GO, everything whent fine untill I made a "partial upgrade" and rebooted the system to apply the changes: now I'm stuck with a black screen:

Filesystem check failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try

Any suggestion is welcome!!!

Thanks and ciao

Sergio

PS:

if I try ctrl-d I get the following:

mountall start/starting
fsck from util-linux-ng 2.16
/dev/sda1: Superblock last mount time (...) is in the future.
/dev/sda1: UNEXPECTED INCONSISTENCY; run fsck MANUALLY.
mountall: fsck / [779] terminated with status 4
mountall: Filesystem has errors: /
init: mountall main process (778) terminated with status 2
rm: cannot remove '/forcefsck': Read-only file system
init: mountall post-stop process (785) terminated with status 1
Filesystem check failed
...

---

### Post by SergioA on 2009-10-12
It seems that the installation/upgrade screwed the BIOS settings for the clock, putting it back of 2 hours...
Hence the problem with "Superblock last mount time (...) is in the future" when booting!
I just set the right time again in BIOS and now I can use Ubuntu ;-)

---

### Post by ptn107 on 2009-10-12
[http://ubuntuforums.org/showthread.php?t=1286309](http://ubuntuforums.org/showthread.php?t=1286309)

---

### Post by SergioA on 2009-10-12
> **ptn107 said:**
> [http://ubuntuforums.org/showthread.php?t=1286309](http://ubuntuforums.org/showthread.php?t=1286309)

Thanks ptn107, very interesting reading!

---

