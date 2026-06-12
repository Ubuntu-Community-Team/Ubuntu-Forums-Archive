---
title: "Updates and add applications stopped working"
date: 2008-09-08
forum: General Help
---

### Post by Bulova on 2008-09-08
Hi:

I'm a newbie to Ubuntu 8.04. Been using it for about six months.

I'm using the Ubuntu/windows option so I can use both.

Abruptly, I can't update or add new applications. When I do it says there is an error and it can't access drive e. It was working fine.

It says to manually try "dpkg--configure-a"

How do I get this working again? How do I do the manual update? I tried the command line and it says command not recognized...

Thanks in advance.

Regards

Frank

---

### Post by sisco311 on 2008-09-08
run the command as root from a terminal:
```
sudo dpkg --configure -a
```

---

