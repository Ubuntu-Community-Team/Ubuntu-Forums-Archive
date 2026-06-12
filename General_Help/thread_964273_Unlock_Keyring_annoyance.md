---
title: "Unlock Keyring annoyance"
date: 2008-10-30
forum: General Help
---

### Post by rmcellig on 2008-10-30
Every time I start up my PC, The Unlock Keyring window comes up prompting me to "enter a password for default keyring to Unlock. The application Network Manager applet wants access to the default keyring but it is locked" message I enter my admin password and all is well.

Is there a way to prevent this window from always appearing when I start up my PC?

I'm using 8.10.

---

### Post by spiderbatdad on 2008-10-30
You should be able to edit the preferences in the passwords and encryption keys menu, under the accessories menu.

---

### Post by koruptid on 2008-10-31
I am having the same issue and my password and encryption menu doesn't have the keyrings section at all.... please help!

---

### Post by spiderbatdad on 2008-10-31
> **koruptid said:**
> I am having the same issue and my password and encryption menu doesn't have the keyrings section at all.... please help!

```
sudo apt-get install seahorse
```

---

### Post by koruptid on 2008-10-31
seahorse was already installed.

I found the problem... auto-login to my account causes the keyring to not load at login, this was making it so that the network manager was the first opject to try loading it.

---

### Post by 8200 on 2008-11-02
Hi koruptid!

I have got the same problem here since upgrading my hp-notebook from 8.04 to 8.10.

Can you explain me how you managed loading keyring just after login?


Thank you!

Regards Arthur

---

