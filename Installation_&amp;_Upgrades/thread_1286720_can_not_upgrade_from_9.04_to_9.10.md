---
title: "can not upgrade from 9.04 to 9.10"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by atomizer on 2009-10-09
Since yesterday I can not upgrade my 9.04 to 9.10.

Wednesday I could upgrade (I did a reinstall after because my partitions were not set right for triple boot), but I get an error message now when I try to upgrade.


error:
```
tom@tom-laptop:~$ update-manager -d
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 1
Debug information: 


gpg: Signature made Thu 08 Oct 2009 07:31:24 PM CEST using DSA key ID 437D05B5
gpg: /tmp/tmpqlwPSb/trustdb.gpg: trustdb created
gpg: BAD signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
```

---

### Post by Newjersey_nl on 2009-10-10
I have exact the same problem.

I found out what it was. The mirror where i wanted to upgrade from (nl.archive.ubuntu.com) is giving me problems. I replaced it with de.archive.ubuntu.com and now it works.

---

### Post by MelDJ on 2009-10-10
karmic is not officialy released yet. its still in beta. that might be a cause too

---

### Post by atomizer on 2009-10-11
Solved thanks to Newjersey_nl (good first post!!!)


Seems that the dutch mirrors have a wrong Signature or something like that.
Switched to Main US servers and am upgrading atm!.

---

