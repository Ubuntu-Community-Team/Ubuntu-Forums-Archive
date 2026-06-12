---
title: "copying users and groups when upgrading machine"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by whitteng on 2009-04-15
We often upgrade hardware for our servers and when we do, we need to copy the users and groups info to the new machine which is often running a new OS. Is there some easy (not tedious) way to do this? Just copying /etc/passwd,group,shadow,gshadow causes major permission problems since many of the system group ids are inconsistent with actual files on the file system. It seems like this would be a pretty common need, is there any good solution other than tediously adding dozens of users and groups manually?

Thank you,
Gary Whitten
[email]whitteng@con2inc.com[/email]

---

