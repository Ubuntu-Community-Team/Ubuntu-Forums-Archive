---
title: "Bad Harddrive?"
date: 2008-09-26
forum: General Help
---

### Post by frodak on 2008-09-26
I have installed 8.04 as a LVM partiton.  /boot is on /dev/hda1 and /dev/hda2 is LVM where / is in /dev/system/root and /home is /dev/system/home.

Twice now on my computer the /etc folder became corrupt.  The first time /etc was missing a bunch of /etc/init.d files.  This time /etc is being listed as a file.

Running fsck shows all sorts of problems /dev/system/root, /dev/system/home appears to be fine.

I don't think its the setup because I have my laptop setup the same way for quite awhile without issue.

I'm going to assume that the HD is failing.

---

### Post by cariboo on 2008-09-27
I would suggest to go to your hard drive's manufacurers web site and download their diagnostic utility and run it on your hard drive. At one time Maxtor had a re-certify utility that would repair a lot of problems, but I haven't seen it around lately.

Jim

---

