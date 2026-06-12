---
title: "Ubuntu 8.04 hardware information on IBM t30"
date: 2008-07-25
forum: Hardware
---

### Post by nycalien on 2008-07-25
I'm new to Ubuntu. I was able to install Ubuntu 8.04 on my IBM T30 as standalone OS. However, I cannot find "Hardware information" under System --> preference. I'm trying to setup my wireless connection but I cannot find my wireless card. However, when I run the hardware test the wireless card detects. But when I go to the network management, it only shows the wired connection and the dial-up modem connection, no wireless. Can someone help me to get the "hardware information" and setup my wireless?

---

### Post by tamoneya on 2008-07-25
run this in terminal(applications-> accessories -> terminal):```
sudo lshw -C network
```

---

