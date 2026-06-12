---
title: "Can I set a NULL/blank root password?"
date: 2008-09-27
forum: General Help
---

### Post by phil81uk on 2008-09-27
Hi,

Is it possible to have a blank/Null/empty root password? So that when it asks me for the root password I just press enter without actually typing one in? I know that htpasswd won't allow this, but knowing Linux there's always a way round these things!

The reason is that I am the only user of my machine. I like that it asks me to confirm actions that require administrative rights, but I dont see the point of entering a password (so I just set mine to a one letter password). In fact I like the Vista method where Administrative actions require you to confirm (but no password unlike Ubuntu).

As for my machines security, my Hardy install is fully encrypted.

---

### Post by amauk on 2008-09-27
it is possible to modify the behaviour of sudo via the 'visudo' command

(don't try to edit the sudoers file manually - see man page for reasons)

I wouldn't recommend it personally, but if you change the entry
```
root    ALL=(ALL) ALL
```
to
```
root    ALL=(ALL) NOPASSWD: ALL
```
then sudo will never prompt for a password

---

### Post by thegodfaza on 2008-09-27
fyi just because an attacker doesn't have physical access to the machine doesn't mean your safe. Since you have no authentication now, anything can run as root. So you should be very careful since someone could write a ```
rm -rf /
``` program and it would run without asking permission.

---

### Post by amauk on 2008-09-27
> **thegodfaza said:**
> fyi just because an attacker doesn't have physical access to the machine doesn't mean your safe. Since you have no authentication now, anything can run as root. So you should be very careful since someone could write a ```
rm -rf /
``` program and it would run without asking permission.
using my example above, you still have to prefix sudo to the rf to gain root priv's,
but yes, it will execute without any sort of confirmation

---

### Post by ImDaMan Sarcastic Beast on 2012-03-29
Just what if the machine in question is a VM, allowed to be run only by one user, without network connection or connecting through a firewall and a proxy (permitting only http[s] requests to certain hosts), with regularly made back-ups? It is actually the case with my machine, and all these comments on how dangerous it is to make a blank root password + auto login should really take into account that sometimes it just _is_ what you actually want and yes, there are other methods to keep things safe. Also if the user is stupid enough to format the hard disk or delete the say, kernel image, then just as well they can cause this harm using sudo and password. It doesn't really happen by mistake to type something like rm -rf /, unless the user in question has serious problems with maintaining sane consciousness and they should never walk out on the streets for their safety. :lolflag:

---

### Post by nothingspecial on 2012-03-29
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

