---
title: "lm-sensors installs, conky doesn't find 12c devices"
date: 2008-07-11
forum: General Help
---

### Post by sjnims on 2008-07-11
Hey guys, I'm having an issue after installing lm-sensors and conky from the repository (and also from source). I can get lm-sensors to work and it does output temperature and fan readings, however when I start conky no temperatures or fan readings are output, and when run from command line conky outputs an error about not finding any i2c devices.

It used to work with ubuntu 7.10 but ever since upgrading to 8.04, it hasn't worked.

Any thoughts?

Thanks!

---

### Post by jludeman on 2008-08-23
Did you ever get this working? I have the same issue. Works fine in Gutsy and fails in Hardy. 

sensors shows the correct temps for lm90.

---

### Post by jludeman on 2008-08-23
Never mind I found the answer here.
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=770821]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=770821")

---

