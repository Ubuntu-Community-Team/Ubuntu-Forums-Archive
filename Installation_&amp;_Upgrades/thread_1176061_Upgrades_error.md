---
title: "Upgrades error"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by aaron2073 on 2009-06-01
Please help,(I am a newbie) I am trying to upgrade and the system turned off during install, and now I have Error: BrokenCount > 0.. What should I do.

---

### Post by raymondh on 2009-06-01
> **aaron2073 said:**
> Please help,(I am a newbie) I am trying to upgrade and the system turned off during install, and now I have Error: BrokenCount > 0.. What should I do.

Hello Aaron,

Try this. Use Synaptic (system > administration > synaptic manager).  In synaptic, go to edit then "fix broken package".  Exit/close and try in a terminal

```
sudo apt-get update
sudo apt-get upgrade
```

For your reference

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Let me us know how goes :)

regards,

---

