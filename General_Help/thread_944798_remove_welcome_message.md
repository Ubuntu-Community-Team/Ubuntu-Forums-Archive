---
title: "remove welcome message"
date: 2008-10-11
forum: General Help
---

### Post by lin00bie on 2008-10-11
i've removed gnome login screen and have been using the terminal to login. everytime my computer boots up i get the following message:
```
  The programs included with the Ubuntu system are free software;
    the exact distribution terms for each program are described in the
    individual files in /usr/share/doc/*/copyright.

    Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
    applicable law.

```

i don't want to see this message everytime. i tried editing   /etc/motd and deleting everything from it. i rebooted and still got the same message. how do i get rid of this message?

thanks

also, how do i make my terminal look more colorful?

---

### Post by Sam on 2008-10-11
/etc/motd is generated on boot. You need to change /etc/motd.tail instead.

---

### Post by lin00bie on 2008-10-11
Thank You.:KS

---

