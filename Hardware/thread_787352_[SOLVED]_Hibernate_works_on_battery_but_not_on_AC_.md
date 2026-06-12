---
title: "[SOLVED] Hibernate works on battery but not on AC power (hardy)"
date: 2008-05-08
forum: Hardware
---

### Post by am28111 on 2008-05-08
I have a very odd issue.

I am currently running Hardy on a Acer 4101 laptop. Hibernation works while the computer is running on battery, but once it gets plugged into the wall, trying to hibernate fails. 

Also, hibernation and suspend worked fine in Gusty. 

Any ideas on what the issue could be? Any help is greatly appreciated.

Thanks.

---

### Post by am28111 on 2008-06-18
After scouring the internet, I came across this webpage:

[HTML]https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/226069[/HTML]

It describes that the following steps should be taken to resolve the issue:

```
sudo gedit /usr/lib/pm-utils/functions
```

Then find where it says platform and replace it with shutdown. 

This resolved the issue for me, hopefully it can help someone else

---

### Post by mnmus on 2008-06-21
Help someone else? Indeed you did! Did a Hardy install on a bare metal desktop last night. Walked off for a while and came back to a... not quite hibernated comp, more like in limbo--neither off nor able to resume.

A hardware reset left me with apps that'd been open that were unhappy, naturally. 

So, not just a notebook issue. For this Ubuntu newb, your tip was a real blessing. Thanks.

---

