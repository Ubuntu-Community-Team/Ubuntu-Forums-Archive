---
title: "[SOLVED] Hellanzb download problem"
date: 2008-08-09
forum: General Help
---

### Post by nimbrant on 2008-08-09
I have been using hellanzb for a while now and everything works great,
except that once in a while I will get an nzb file that hellanzb cannot download.

When hellanzb tries to download it, it will be stuck at 2.0KB/s and not download. It does this even when I restart hellanzb. If I cancel this from the queue hellanzb will move on to the next and download the rest of the nzbs without a problem.

I would think that it is a problem with the nzb, but I tried the same nzb file with a different program call nzbperl which downloaded the nzb file without any problems.

Has anyone had similar problems? I'm not sure what to try next to resolve this issue.

---

### Post by nimbrant on 2008-10-06
The problem is if the nzb group element has a space in it.
i.e. <group>_alt.binaries.tv</group> (i put an underscore where the space is)
Hellanzb seems to choke on this.

A fix is described here [http://www.hellanzb.com/trac/hellanzb/ticket/393#comment:6]("http://www.hellanzb.com/trac/hellanzb/ticket/393#comment:6")

All you have to do is add a line to strip the spaces from the group name.
```
group = group.strip()
```
at about line 513 in the file /usr/share/python-support/hellanzb/Hellanzb/NZBLeecher/Protocol.py

Hope this helps someone.

---

### Post by loteq on 2008-12-20
Thanks!! I was pulling my hair trying to figure this one out.

---

