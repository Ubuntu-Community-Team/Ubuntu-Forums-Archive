---
title: "feh doesn't work after upgrade"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by barchamb on 2009-10-31
I have been using 9.04 for a while now.  This morning, I upgraded to 9.10.  I have a script that runs a feh slideshow for me, which looks like this:

feh -rzFZD5 /mnt/Docs/Pictures/

After upgrade, this no longer work.  It gives me this error:

feh WARNING: couldn't open /mnt/Docs/Pictures

However, I can "cd" or "dir" or "ls" that directory just fine, so I know it's mounted and I have permissions.  Here's the permissions:

drwxr-xr-x 1 root root      12288 2009-10-18 18:56 Pictures

Any ideas?

---

### Post by barchamb on 2009-11-01
Help!  I really need some ideas on this.  My family is upset that the slideshow isn't running anymore!  :-)

Where should I be looking?

---

### Post by jollyrogr on 2009-11-14
I'm having the same issue with FEH since upgrading to 9.10  FEH works fine on local images, but on my mounted windows shares it wont work anymore.  My shares are permanently mounted using fstab and cifs.  This doesn't seem to be a user perm issue, since it doesn't work logged in as root either.  The images on the remote machine can be viewed with a different viewer, or copied to the local machine and then viewed with FEH but this is less than ideal.  I get the same warning message: feh WARNING: couldn't open path/to/0751.jpg

---

### Post by barchamb on 2009-11-14
Did you ever figure out how to fix it, or get an answer from anyone?

---

### Post by jollyrogr on 2009-11-14
since FEH works perfectly on images on local drives and the issue is only with remote file systems I think the root cause is a networking issue.  Something changed in 9.10's networking so FEH doesn't work.  I dont know how to fix it.

---

### Post by lwr07 on 2010-06-01
I've run into this exact same issue.  Has anyone figured out why feh can't read files off of a CIFS mount anymore?

---

