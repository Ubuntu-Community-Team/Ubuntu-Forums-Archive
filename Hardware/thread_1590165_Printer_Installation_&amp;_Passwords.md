---
title: "Printer Installation &amp; Passwords"
date: 2010-10-07
forum: Hardware
---

### Post by OperatorA on 2010-10-07
Was in my "Administrator" account, trying to install a printer driver for my Lexmark X2650 printer, a driver for Linux (Debian derivatives) I got from Lexmark. It was installing it and asked for my administrative password. I gave it and it said INCORRECT PASSWORD. I double checked and I DID use the CORRECT password.

Now what do I do? What is wrong? The password works for doing other things that call for a password. In fact I just installed the Firewall with it & upgraded some security patches...

Please help.
Larry

---

### Post by sikander3786 on 2010-10-07
I haven't used Lexmark printer, so not that much experienced on it.

It might be asking for the root password which is by default disabled in Ubuntu. Did you try

```
sudo -i
```

Then run the driver installer and see if it gets installed or not.

Note, sudo is sufficient in most cases.

---

### Post by dabl on 2010-10-07
If you're using the CUPS utility, I think it wants "admin" as the root password.  Dunno why they do it that way ....

---

### Post by OperatorA on 2010-10-11
None of that works...

---

