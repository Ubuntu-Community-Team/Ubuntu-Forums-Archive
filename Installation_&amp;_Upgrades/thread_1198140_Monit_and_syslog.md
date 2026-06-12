---
title: "Monit and syslog"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by riivella on 2009-06-27
Hi,

Does anyone know how to prevent monit actions from being logged to syslog?

For example when monit checks postfix is running this appears in the syslog

Jun 18 10:57:18 host postfix/smtpd[8544]: connect from localhost[127.0.0.1]
Jun 18 10:57:18 host postfix/smtpd[8544]: disconnect from localhost[127.0.0.1]

Now since monit checks regularly it floods the logs, so anyone know how to have these not logged?

riivella

---

