---
title: "DVB card not working after update to 18.04.4"
date: 2020-04-16
forum: Hardware
---

### Post by pam197 on 2020-04-16
I have a TBS6280 DVB card with drivers installed from github/tbsdtv and it was working. I recently did some updates and I am now running Ubuntu 18.04.4 but I find that my DVB card is no longer working. I do not have a /dev/dvb directory, which I think I had previously. My knowledge of Ubuntu is limited and I am not sure what to try next.

---

### Post by CelticWarrior on 2020-04-16
You may try to reinstall the drivers and if that fails you need to wait for an eventual update of those drivers. Also please read: [https://www.tbsdtv.com/forum/viewtopic.php?f=153&t=24957](https://www.tbsdtv.com/forum/viewtopic.php?f=153&t=24957)

---

### Post by pam197 on 2020-04-16
Thanks for the reference. It's good to know it's not just me with the problem of the driver disappearing on update. I have tried reinstalling, but it seems to install to /lib/modules/5.3.0-40-generic whereas /lib/modules/5.3.0-46-generic looks to be the most recent. Am I missing a step in the reinstall? If I have to wait for an updated driver, can I revert to a previous kernal in the meantime? Am I correct in thinking I should have a /dev/dvb and when should it get created?

---

