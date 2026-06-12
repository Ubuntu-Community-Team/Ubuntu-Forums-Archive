---
title: "ubuntu crush while running thunderbird"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by jl6568 on 2009-02-24
Hi, All,

Please help. My ubuntu 8.10 started crushing recently. It is very annoying that  the screen suddenly turn black for a few seconds and then the login in screen show up so I have to login again. Everything I worked on disappeared. I have noticed the following:

1. It only happen if I am runing Thunderbird or other email program (Evolution);
2. It most likely happened when the email program check for emails from server and there is a new email in the account;

Any suggestions? 

Thanks.

---

### Post by bazzer on 2009-03-13
I think that may be down to your x server restarting, for whatever reason. If it were me, I'd log back in after a crash and look at the following log files:
/var/log/syslog
/var/log/Xorg.0.log
/var/log/messages
It's likely you may see something in there with 'EE' or 'error' and it may give you more of a clue.

---

