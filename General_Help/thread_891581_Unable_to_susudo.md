---
title: "Unable to su/sudo"
date: 2008-08-16
forum: General Help
---

### Post by Hilipatti on 2008-08-16
Right, so I installed Ubuntu with a simple password earlier and I decided that I'm not going to use a password at all, so I deleted the user password from /etc/shadow (using regular "passwd -d" is boring!) Now, if I remember my steps correctly, I was unable to use sudo or su after a reboot. Even though I had a blank password the sudo/su prompt failure'd and the old password didn't work either. So I booted in rescue mode, enabled the root account and wiped the password.

I'm able to normally login as root from a tty and my user account doesn't require a password either, but sudo and su don't work. sudo fails silently after I hit enter for password and su "authentication failure"s.

I'm pretty much clueless even though it might be something really simple :P

Thanks..

---

### Post by Hilipatti on 2008-08-16
Bumpo...

---

### Post by Sycron on 2008-08-16
Try with su.
```
$ su
```
or
```
$ gksu
```

---

### Post by dexter on 2008-08-16
Are you still allowed to have sudo rights? 
You can modify it by executing visudo as root.

---

### Post by sisco311 on 2008-08-16
Edit /etc/shadow line to:[FONT=monospace]
```
[/FONT]*username*:**U6aMy0wojraho**:13721:0:99999:7:::
```
[http://ubuntuforums.org/showthread.php?t=513820](http://ubuntuforums.org/showthread.php?t=513820)

---

