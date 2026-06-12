---
title: "mount: error while loading shared libraries"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by signal99 on 2009-11-02
I just received a copy of 9.10 32 Bit (x86, i386) in the mail from On-Disk.com and was planning on installing it on my Dell Inspiron laptop which I have had no past problems installing Ubuntu, Suse, and Fedora. I tried to run the install and after I select install I get the following messages after about 3 minutes???

mount: error while loading shared libraries: /lib/libblkid.so.1: cannot read file data: Input/output error

mountall: mount /dev/pts [1238] terminated with status 127
mountall: Filesystem could not be mounted: /dev/pts

mount: error while loading shared libraries: /lib/libblkid.so.1: cannot read file data: Input/output error

mountall: mount /dev/pts [1239] terminated with status 127
mountall: Filesystem could not be mounted: /dev/shm

mount: error while loading shared libraries: /lib/libblkid.so.1: cannot read file data: Input/output error

mountall: mount /dev/pts [1240] terminated with status 127
mountall: Filesystem could not be mounted: /tmp


mount: error while loading shared libraries: /lib/libblkid.so.1: cannot read file data: Input/output error

mountall: mount /dev/pts [1241] terminated with status 127
mountall: Filesystem could not be mounted: /var/run


I ran the test to make sure there was not a problem with the CD and it said that it was fine. Any ideas????

---

### Post by signal99 on 2009-11-03
I forgot to mention, my laptop is currently running XP.

---

### Post by signal99 on 2009-11-05
Anybody????

---

### Post by senor_smile on 2009-11-26
I have just upgraded an acer aspire one to 9.10 32-bit(fresh install).  I booted once successfully and ran an upgrade.  It froze and I did a sysrq+REISUB.  Now upon rebooting I get the exact same error as previously mentioned.  Anyone have any ideas?

---

### Post by Gilankzz on 2009-11-26
try to reisstal your samba..
its work:popcorn:

---

### Post by jacobs444 on 2009-11-26
Honestly, it sounds like a bad disc, or bad drive. I can't guarantee anything though.

---

### Post by senor_smile on 2009-11-26
I am unable to boot up the machine.  also, samba was never installed.  Only the base install of ubuntu karmic was installed.

---

