---
title: "how to bypass login screen in Lubuntu 18.04 with Lightdm"
date: 2020-04-18
forum: Hardware
---

### Post by thosecars822 on 2020-04-18
Hello

I would like to ask how I can boot straight without seeing any login screen with LightDM in Lubuntu 18.04. I have already set up the user settings, by means of the user settings graphic interface, so that the password does not get asked at boot time. That does work because the password does not need to get typed now. Anyway a login screen keeps on getting displayed and the Enter key needs to get pressed to get the OS finish booting. I would like to know what needs to get done in order to avoid having to press this Enter key to finish the OS boot everytime the computer is started.

Thanks in advance

PD: @admin: please change this thread into the General Help forum because I just realied, that this question probably does not match the Hardware forum. Thanks.

---

### Post by thosecars822 on 2020-04-19
Already solved by adding the following lines 
```

autologin-user=x
autologin-user-timeout=0
greeter-session=lightdm-gtk-greeter

```
at the end of the following file's content:

/usr/share/lightdm/lightdm.conf.d/20-lubuntu.conf

so that the full file's content looks like as follows:
```

user-session=Lubuntu
autologin-user=x
autologin-user-timeout=0
greeter-session=lightdm-gtk-greeter

```

---

