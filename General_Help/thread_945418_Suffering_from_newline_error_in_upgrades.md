---
title: "Suffering from newline error in upgrades"
date: 2008-10-12
forum: General Help
---

### Post by Yoshis88 on 2008-10-12
Any time I try to do anything involving installation or upgrades, I get this newline error.

```

dpkg: parse error, in file `/var/lib/dpkg/available' near line 2811 package `openoffice.org-gnome':
 newline in field name `debian-openoffice@lists.debian./rg>'
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Let it be noted that during (re-)installation of Ubuntu on my Westinghouse NB-14w2, it threw a write error on an openoffice.org file.  I was installing from the 8.04.1 i386 DVD, and it kept throwing such errors and couldn't finish the installation.  I switched to the CD, and it only threw the one error about the single openoffice.org file.  Unfortunately, I didn't take the name of that file down.  I just figured I would reinstall the package (or wait till 3.0 was released).

Any help figuring this out would be greatly apreciated :).

---

### Post by fooman on 2008-10-12
try running the following command in a terminal:

```
sudo dpkg --clear-avail && sudo apt-get update
```

see if that helps.

---

### Post by Yoshis88 on 2008-10-21
Sorry 'bout that. I just re-wiped and reinstalled the system from a USB key, and everything is flawless.

But I believe your solution would have worked.  In the /var/lib/dpkg/available file, there were a whole bunch of extraneous and dropped characters, easily recognized by we the humans as transcription errors.  That seemed to be the only corrupted file too.  Thank you for your help!

---

