---
title: "Are there any logs to help me find out why my computer hangs?"
date: 2018-03-10
forum: Hardware
---

### Post by Bernard_Faucher on 2018-03-10
Hi,

I am running Lubuntu 17.10 on a machine that is used as a DNLA server, so I have Apache and Serviio installed. The machine has been working without any issues, and then I installed Radarr and Transmissoin-Daemon. Since I have done this the machine is hanging after being up for a couple of hours consistently.

I was wondering if someone out here could point me in the right direction so that I can resolve this mysterious problem?

---

### Post by holiday on 2018-03-10
journalctl  is a log aggregator that in the default configuration keeps logs going back for quite some time.

$ journalctl

Perhaps most convenient is 

$ journalctl > journalctl.out

You can then browse the text file journalctl.out with any text editor.  Look for entries indicating system startup. The journal entry just prior to that will be the last logged to any of the logs that journalctl is tracking. 

You could also try removing Radarr and Transmission-Daemon -- one at a time. Hopefully this will identify the culprit.

---

### Post by TheFu on 2018-03-10
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

