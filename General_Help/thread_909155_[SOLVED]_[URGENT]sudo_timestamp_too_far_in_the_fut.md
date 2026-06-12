---
title: "[SOLVED] [URGENT]sudo: timestamp too far in the future"
date: 2008-09-03
forum: General Help
---

### Post by dexter.deepak on 2008-09-03
i frequently changed the  sudo password, and then i started getting this error , whenever i use sudo.
```
sudo: timestamp too far in the future: Sep  3 21:13:29 2008

```
now would i have to wait till the specified time ? i have lots of work to be done...

---

### Post by Dougie187 on 2008-09-03
[http://ubuntuforums.org/showthread.php?t=173505](http://ubuntuforums.org/showthread.php?t=173505)

---

### Post by ayoung on 2008-11-05
A quick follow-up on this, since the duplicate thread is now read-only.

I was having this problem on a PowerPC running Dapper Server.  Reading the boot log, I found a note that:

"No usable clock interface found.
Cannot access the Hardware Clock via any known method."

This seemed like a likely culprit for the timestamp issue, so I found this LaunchPad bug and workaround which fixed the problem for me: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/26658/comments/2](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/26658/comments/2)

Happy sudo'ing.

---

