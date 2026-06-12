---
title: "Startup Script"
date: 2008-08-17
forum: General Help
---

### Post by waapwoop1 on 2008-08-17
Hi guys,

Everytime i log in, i run the following... sudo sysctl -p
and i enter my password.

Is there anyway to run this automatically?   I put it in the login section, but it doesn't work, probably because i have to enter my password.

How can i make this happen automatically?

---

### Post by Vivaldi Gloria on 2008-08-17
> **waapwoop1 said:**
> Hi guys,

Everytime i log in, i run the following... sudo sysctl -p
and i enter my password.

Is there anyway to run this automatically?   I put it in the login section, but it doesn't work, probably because i have to enter my password.

How can i make this happen automatically?

Try putting it in /etc/rc.local as foolows:

```
sysctl -p
exit 0
```

---

### Post by caljohnsmith on 2008-08-17
You can just stick it in /etc/rc.local, without the sudo, since everything in that file will be run as root at startup.
```
gksudo gedit /etc/rc.local
```
And add at the bottom:
```
sysctl -p
```
That should work. :)

EDIT: And of course Vivaldi beat my post by 30 seconds. :)

---

### Post by waapwoop1 on 2008-08-17
Thankyou

---

