---
title: "I can't change my password"
date: 2008-12-08
forum: Hardware
---

### Post by muxalko on 2008-12-08
Since I've changed my password with "Users and Groups" utility, I cannot login to Ubuntu, neither change my pass with passwd... It says "Passwd: Password updated successfully", but not asking me to provide my current password or to enter a new one.

---

### Post by taurus on 2008-12-08
Boot into recovery mode from GRUB menu and change your password at the prompt.  Assuming your username is john, run

```
passwd john
```
Once you are done, reboot and see if you can log in with your username and the new password.

```
shutdown -r now
```

---

