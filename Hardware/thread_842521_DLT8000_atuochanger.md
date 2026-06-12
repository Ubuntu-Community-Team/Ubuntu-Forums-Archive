---
title: "DLT8000 atuochanger"
date: 2008-06-27
forum: Hardware
---

### Post by jujitsu-nut on 2008-06-27
Hi.

I am not sure if this is the correct forum or this should go to the  server platform...

I have a DLT8000 autochanger which keeps changing device ID's on restarts. It should come up as /dev/sg1 and does until I do a restart - then it may show up as /dev/sg0 or even /dev/sg4. 

Is there anyway to force the device to come up consistently as /dev/sg1? I am using 8.04 LTS

--james

---

### Post by thideras on 2008-06-27
If you are trying to mount it, you can mount it via the UUID, which should not change.

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

