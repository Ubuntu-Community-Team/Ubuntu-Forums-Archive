---
title: "Touchpad Not Working After Install"
date: 2014-04-19
forum: Hardware
---

### Post by emilward on 2014-04-19
I had to reinstall Ubuntu 13.10 but when I did I had my wireless keyboard and mouse plugged in while I was doing the install. Now my touchpad doesn't work. Ubuntu recognizes my laptop's keyboard but it does not recognize the touchpad, only my wireless mouse. I've searched the forums and askubuntu.com and nothing seems to work. Am I missing something?

---

### Post by varunendra on 2014-04-20
Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
xinput
synclient
grep -i touchpad /var/log/Xorg.0.log
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

Do you have a Fn+ key combination or a dedicated switch to enable/disable the touchpad? Have you tried it?

**PS:**
Now that 14.04 is out, have you tried it yet? Fresh install of 13.10 doesn't make much sense now unless you have a very specific reason to stick with it.

---

