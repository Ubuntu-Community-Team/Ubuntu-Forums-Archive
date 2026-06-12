---
title: "Why does Mono require a Password"
date: 2008-11-10
forum: General Help
---

### Post by a person on 2008-11-10
Every time I boot up Ubuntu I get a dialog telling me mono needs my password.  Why does mono need my password and how to I enable it so it does not require my intervention every boot?  Thanks in advance.

---

### Post by directhex on 2008-11-10
It's not Mono itself, it's an app which uses Mono, and presumably also uses some Gnome libraries (e.g. gnome-do)

Try: Applications/Accessories/Passwords & Encryption Keys/Edit/Preferences/login/Change Unlock Password

Ensure this password 100% matches the password you use to log into the system.

Note: I don't think there's a way around it if you have automatic login (as the automatic login doesn't actually touch your password, so it can't pass your password on to gnome-keyring)

---

### Post by a person on 2008-11-10
I made sure the login password was the same as my login password and it still asks me for my pasword, though I also have automatic login on so I may be sol on this.  Thanks for your reply, I really hoped there would have been a way around this.  Anyone else have a suggestion?

---

### Post by directhex on 2008-11-10
[http://bugzilla.gnome.org/show_bug.cgi?id=386866](http://bugzilla.gnome.org/show_bug.cgi?id=386866)

---

