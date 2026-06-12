---
title: "apt-get update problems (badsig)"
date: 2005-11-14
forum: General Help
---

### Post by maxmouse on 2005-11-14
I get the following error when I do an apt-get update:

[B]W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems[/B]

The solution given is sort of silly when I am getting the error doing an apt-get update already.  Any ideas on how to fix this, or what would have caused it in the first place?

---

### Post by Kyral on 2005-11-14
Eh...its happening again. Try changing over to the main archive (archive.ubuntu.com) and see what happens

---

### Post by maxmouse on 2005-11-14
Thanks, that fixed it.

---

