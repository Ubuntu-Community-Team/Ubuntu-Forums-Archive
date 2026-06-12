---
title: "Updates Manger shows update but gives Error on Download"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by mithun.kamath on 2009-09-16
I am having a problem in updating the OS. When i start Updates manager it shows 120mb updates available , but when starts downloading it says something is broken. what am i Doing wrong.

---

### Post by zvacet on 2009-09-16
Does it say broken packages?If it does then go to the applications>accessories>terminal and type

```
sudo apt-get -f install
```

---

### Post by mithun.kamath on 2009-09-17
Yes it says Broken packages. I ll try the solution that you have given tonight and let you know

Thanks :)

---

### Post by mithun.kamath on 2009-09-19
Hi zvacet,

I tried solution that you have given. But still not working as expected. I have attached the screen grab of the issue that i am facing along with the Error.txt, the actual error that i am facing. Please help me.

Regards,
Mithun

---

### Post by wojox on 2009-09-19
Hey Mithun,

Try going into System > Admin > Software Sources and changing your Download from location to Main Server. I had this problem last week when I had to update ten packages it would only give me eight. So I switched back to the main server and all went well.

---

### Post by mithun.kamath on 2009-09-19
Hey wojox,

That did the work ......!Started downloading. Now 20updates remaining. Thanks a lot:)

regards,
Mithun

---

