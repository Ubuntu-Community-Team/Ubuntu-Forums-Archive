---
title: "editing polkit file does not enable hibernate"
date: 2013-01-25
forum: Hardware
---

### Post by stefansjs on 2013-01-25
I just (finally) installed Ubuntu 12.04 on my laptop and I find that the hibernation function is not present.  I discovered quickly by googling that it is disabled by default so I followed the instructions at [https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html).  It definitely works to hibernate my computer using pm-hibernate, but after editing ```
/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
``` I still do not see the hibernate option in the power menu.  Please help.  Is there another way to enable hibernation?

```
$ pwd
/etc/polkit-1/localauthority/50-local.d
$ ls -l
total 4
-rw-r--r-- 1 root root 113 Jan 24 22:32 com.ubuntu.enable-hibernate.pkla
$ cat com.ubuntu.enable-hibernate.pkla 

[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

```

---

### Post by ahallubuntu on 2013-01-25
That sure worked for me, and that's all I had to do to get it back in the menu.  Maybe you have to logout and back in again or reboot?


_Does pm-hibernate itself work for you from a terminal window when you try it?_

Sorry, strike that, I saw that you said you'd tried it already after my post....

---

### Post by stefansjs on 2013-02-01
Well, not sure what I did, but restarting a couple more times seemed to solve the problem.  Oddly enough "hibernate" appeared in the power manager before the actual power menu.

---

