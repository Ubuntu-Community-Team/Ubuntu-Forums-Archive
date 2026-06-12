---
title: "/etc/rc.local FAIL during boot"
date: 2008-08-08
forum: General Help
---

### Post by adcwoef on 2008-08-08
Hello

I have a box running Ubuntu Server 8.04 and during boot i get the message 

```
Running /etc/rc.local      [COLOR="Red"]Fail![/COLOR]
```

But the rc.local-file completely empty, I haven't put anything there nor has the system. So how could it fail? I tailed the /var/syslog but saw nothing about it.

Is there another log to check what is happening during boot? Any help solving this mysterious problem is appreciated.

Thanks.
/Erikw

---

### Post by x1a4 on 2008-08-08
If it's completely empty than that's the problem.  Add ```
exit 0
``` to the file, and remove its execute bit.```
chmod -x /etc/rc.local
```

---

### Post by adcwoef on 2008-08-08
The "exit 0" did exist, my bad. But why should i remove execute for the file?

---

### Post by Vivaldi Gloria on 2008-08-08
> **ErikWestrup said:**
> The "exit 0" did exist, my bad. But why should i remove execute for the file?

The permission of /etc/rc.local should be

```
vivaldi@narval:/etc$ ls -l rc.local 
-rwxr-xr-x 1 root root 409 2008-07-22 04:28 rc.local

```

So change the owner to root and chmod 755 it.

I suggest you try commands of the sort

```
sudo update-rc.d rc.local defaults 
sudo update-rc.d rc.local multiuser 
```

See

```
man update-rc.d 
```

for more info. First use with the flag

```
-n     Don’t do anything, just show what we would do.
```

---

### Post by x1a4 on 2008-08-08
> **ErikWestrup said:**
> But why should i remove execute for the file?

So it won't execute.  If you're not using it, the script that launches it (/etc/init.d/rc.local) won't bother with it.  On Ubuntu, the default thing to do is to remove the execute bit from /etc/rc.local, unless it's being used.

---

