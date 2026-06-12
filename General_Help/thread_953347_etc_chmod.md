---
title: "/etc chmod"
date: 2008-10-20
forum: General Help
---

### Post by rayfidelity on 2008-10-20
Hi,

I have a problem. I've chmoded /etc because i couldn't get ufw runing...There seemed to be problems with the rights on my HDD. Then i couldn't mount USB drives (which i've fixed with chmod +x /etc/init.d/hal)

I still can't mound internal drives...could someone help me?? what should the rights in /etc be? how should i chmod them to solve this problem...

Thank you!

---

### Post by Nepherte on 2008-10-20
These are the permissions for the directory /etc: 0755 (drwxr-xr-x). Be careful next time with chmodding important parts of your system. Typically the original permissions for files and directories is already set right and in general you shouldn't mess with them. For example, I've never heard of a problem with ufw that involves changing the original settings.

---

### Post by geirha on 2008-10-20
> **rayfidelity said:**
> 
I have a problem. I've chmoded /etc because i couldn't get ufw runing...

How exactly did you "chmod" /etc?

---

### Post by rayfidelity on 2008-10-20
well actually i chowned it first... chown -R root /etc

-R was a big mistake as it seems

Any my hdd still won't mount 

is there any solution??

also if i click on the exit button nothing happens...

---

### Post by tonybaqain on 2008-10-20
use this, and i hope it solves the problem :
[list]
[*] reboot into single ( recovery ) mode
[*] use this code carefully :
```

chmod -R 755 /etc/
chmod +x /etc/init.d/*

```
[*] reboot your system into normal mode
[/list]

have fun :)

---

### Post by geirha on 2008-10-20
> **tonybaqain said:**
> use this, and i hope it solves the problem :
[list]
[*] reboot into single ( recovery ) mode
[*] use this code carefully :
```

chmod -R 755 /etc/
chmod +x /etc/init.d/*

```
[*] reboot your system into normal mode
[/list]

have fun :)

Do not do this!

It will most certainly disallow further use of sudo, and leave password hashes wide open.

---

### Post by JohnFH on 2008-10-20
> **tonybaqain said:**
> use this, and i hope it solves the problem :
[list]
[*] reboot into single ( recovery ) mode
[*] use this code carefully :
```

chmod -R 755 /etc/
chmod +x /etc/init.d/*

```
[*] reboot your system into normal mode
[/list]

have fun :)

The advice on this thread is worrying.
755 are the permissions for a *directory*, not the whole /etc tree and not the files within it!  The best advice is to restore the /etc tree from your backups.  
The above sequence of commands is insecure, incorrect and don't make sense anyway (755 permissions include execute, so no need for second line).

Never do chmod -R unless you know *exactly* what you are doing, especially on files you don't own (and shouldn't own!).

---

