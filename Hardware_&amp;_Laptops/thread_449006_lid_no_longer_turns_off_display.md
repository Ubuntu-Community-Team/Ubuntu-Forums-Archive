---
title: "lid no longer turns off display"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by jlmb on 2007-05-19
I don't remember changing anything that might have caused this. I found out that something was wrong when the power manager icon from power management stopped reporting when on AC or BATT. 
Battery charge monitor does report when on AC or BATT. 

/var/log/acpid still receives the event.

```
[Sat May 19 18:22:12 2007] received event "button/lid LID 00000080 00000015"
[Sat May 19 18:22:12 2007] notifying client 4401[107:114]
[Sat May 19 18:22:12 2007] notifying client 5630[1000:1000]
[Sat May 19 18:22:12 2007] executing action "/etc/acpi/lid.sh"
[Sat May 19 18:22:12 2007] BEGIN HANDLER MESSAGES
[Sat May 19 18:22:12 2007] END HANDLER MESSAGES
[Sat May 19 18:22:12 2007] action exited with status 0
[Sat May 19 18:22:12 2007] completed event "button/lid LID 00000080 00000015"
[Sat May 19 18:22:17 2007] received event "button/lid LID 00000080 00000016"
[Sat May 19 18:22:17 2007] notifying client 4401[107:114]
[Sat May 19 18:22:17 2007] notifying client 5630[1000:1000]
[Sat May 19 18:22:17 2007] executing action "/etc/acpi/lid.sh"
[Sat May 19 18:22:17 2007] BEGIN HANDLER MESSAGES
[Sat May 19 18:22:17 2007] END HANDLER MESSAGES
[Sat May 19 18:22:17 2007] action exited with status 0
[Sat May 19 18:22:17 2007] completed event "button/lid LID 00000080 00000016"
```

thanks for your time

---

### Post by Hairy_Palms on 2007-05-20
what happens if you enter

"xset dpms force off" in a console (no quotes)

---

### Post by jlmb on 2007-05-20
screen turns off until a key is pressed....

---

