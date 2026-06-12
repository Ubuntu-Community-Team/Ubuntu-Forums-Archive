---
title: "Launcher to start service"
date: 2008-08-20
forum: General Help
---

### Post by jamesdcarroll on 2008-08-20
I installed Apache's Directory server to play with and I can start the service from the command line with:

sudo /etc/init.d/apacheds start

followed by my password. 

I'd prefer to create a launcher/menu item in the Main Menu, but the above command doesn't work.

How do I get that to work? 

Thanks!

---

### Post by dominiquec on 2008-08-20
Try using 

```
gksudo /etc/init.d/apacheds start
```

as your launch code.  It will still prompt you for a password, though.

If you want to not enter your password at all, you might have to fiddle with the permissions or the /etc/sudoers file.

---

### Post by jamesdcarroll on 2008-08-21
> **dominiquec said:**
> Try using 

```
gksudo /etc/init.d/apacheds start
```

as your launch code.  It will still prompt you for a password, though.

If you want to not enter your password at all, you might have to fiddle with the permissions or the /etc/sudoers file.

Thanks! I think I can live with entering the password, it was just typing (or in all honesty having that line laying around so I can copy/paste) was the real pain.

Thanks again!

---

