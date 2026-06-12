---
title: "Can't log into terminal"
date: 2008-11-23
forum: General Help
---

### Post by imnotabot on 2008-11-23
So I am having some sort of problem logging into super user. You see, I need to manually run 'dpkg --configure -a' to sudo, but for that I need super user. 

(The full thing I get is:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
)

When I type in 'su' to get super user, and type my ubuntu log-in password, it says:
su: Authentication failure

Is there any way I can fix this and get super user?

---

### Post by Elfy on 2008-11-23
Use sudo instead

```
sudo dpkg --configure -a
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by beno1990 on 2008-11-23
By default, the actual root account (which the su command logs you into) is disabled in Ubuntu for security reasons. Instead, you have to use the sudo command, which emulates the super-user on a per-command basis.

---

### Post by SIGTERMer on 2008-11-23
try doing it at runlevel 1, assuming you can run the program here..
sense you can't use sudo, you'll have to do it manually. just restart the system. when you see the grub, choose the latest kernel with recovery (usually the second highest). a blue screen should appear then choose "root. this will let you start the system with root permissions

edit: i thought that you were having problems with sudo.. O well..

---

