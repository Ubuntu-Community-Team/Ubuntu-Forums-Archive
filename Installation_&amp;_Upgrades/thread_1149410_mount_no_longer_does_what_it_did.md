---
title: "mount no longer does what it did"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by leemajors on 2009-05-05
hey,

after a fresh 9.04 install, my mount command doesn't do what it used to on 8.10.

i have a NAS and i used to type:

sudo mount -t nfs 192.168.2.243:/mnt/vader /media/vader

which would mount a folder on the NAS to a local folder.

now, when I type that I get:

mount: wrong fs type, bad option, bad superblock on 192.168.2.243:/mnt/vader,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


any thoughts?

---

