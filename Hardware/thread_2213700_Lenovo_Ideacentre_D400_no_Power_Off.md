---
title: "Lenovo Ideacentre D400 no Power Off"
date: 2014-03-28
forum: Hardware
---

### Post by andreas17 on 2014-03-28
Hi,

I installed Ubuntu Server 13.10 on my Lenovo Ideacentre D400 Home Server. The problem I have is that every time I shut the server down with
```
sudo shutdown -P now
```
or
```
sudo halt -p
```

the server switches off and after 5 seconds it reboots again. Does anybody have an idea what could be wrong?

Thanks for your help!

@edit
I just tested with an Open Suse Live USB distribution - there everything works as intended. Seems to be an ubuntu specific issue.

---

### Post by ajgreeny on 2014-03-28
I have no idea if it will make any difference, and I can not think why it should, but try the alternative options for shutdown.
**sudo shutdown -H now **or[B]
sudo shutdown -h now[/B]

---

### Post by andreas17 on 2014-03-28
Thanks for your reply. No it didn't make a difference. Maybe you have another idea? Can I check if ACPI is being configured the right way?

---

