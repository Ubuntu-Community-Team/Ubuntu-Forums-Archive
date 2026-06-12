---
title: "su password"
date: 2005-11-29
forum: General Help
---

### Post by otec_abraham on 2005-11-29
What is the superuser (su) (root) (administrator) password of LiveCD...?:confused:

---

### Post by Corvillus on 2005-11-30
The root account is locked by default in Ubuntu. You use sudo as an authentication to gain root privileges.
```
sudo <command>
```
executes a command as root in your environment
```
sudo -s
```
gives you a root shell in your environment
```
sudo -i
```
gives you a root login shell.
If sudo prompts for a password, it wants your password, not root's. If the password is correct and you're in the sudoers list, it will give you root privileges. More detailed information is availiable: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2005-11-30
I've never needed a password to do root stuff in the live CD.

---

