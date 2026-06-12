---
title: "Errors...."
date: 2008-11-19
forum: General Help
---

### Post by Niloc on 2008-11-19
I am running Ubuntu on a 64bit system.
At startup I get a full screen of errors but it scrolls too quickly to read properly. To get Thunderbird and firefox to work I sometimes have to switch off completely and restart two or three times. Is there an error logging system where I can find out what is happening?

Colin

---

### Post by taurus on 2008-11-19
You can look at the /var/log/messages.

```
sudo more /var/log/messages
```
Hit the Space key for the next 24 lines.

---

