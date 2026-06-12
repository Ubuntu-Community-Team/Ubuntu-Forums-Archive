---
title: "i get abiut 2 mins of battery life unplugged"
date: 2010-10-31
forum: Hardware
---

### Post by craig7 on 2010-10-31
i just got my netbook yesterday and got ubuntu 10.10 on it, the battery life was fine yesterday but now when i unplug it it says 8hr till empty and then after a min it goes down to 3hr and then it tells me that my battery is critically low and then it hibernates. is there any way i can fix this problem?

---

### Post by craig7 on 2010-10-31
plz, anything?

---

### Post by craig7 on 2010-10-31
anything? i need this fixed for school tomorow

---

### Post by cpmman on 2010-10-31
Sorry - back to the retailer.

---

### Post by IcarusR on 2010-10-31
What is battery life in windows ?

Take it back to retailor with Ubuntu on it & more likely than not they will tell you that it is Ubuntu that is causing it.

You could try adding the following Kernel boot option to see if it makes any difference.

```
acpi_osi="linux" 
```

Instructions howto do it here

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation")

---

