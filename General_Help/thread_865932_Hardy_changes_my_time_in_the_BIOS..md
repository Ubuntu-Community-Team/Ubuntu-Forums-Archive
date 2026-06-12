---
title: "Hardy changes my time in the BIOS."
date: 2008-07-21
forum: General Help
---

### Post by pilot550 on 2008-07-21
I am running a dual boot Hardy64/Vista64. I live in New York and every time I boot to Hardy it shows the correct time, but when I boot to Windows after that it changes the time to 4 hours ahead. I pulled up the BIOS after a Hardy boot and that's where the time change is going on. Since it's 4 hours ahead I am assuming its got something to do with zulu time (GMT). Anyone know how I can fix this?

---

### Post by Tim Sharitt on 2008-07-21
This is due to Ubuntu thinking that the hardware clock is UTC time when it is actually local time (or it may be the other way around). As a result, when ubuntu shuts down it resets the hardware clock to what it thinks it should be which is incorrect. I believe you can fix this by editing the /etc/default/rcS file. There is a entry for utc which is set to true or false. Change it to the opposite and it should fix the problem.

---

### Post by pilot550 on 2008-07-21
That worked. Thank you very much.

---

