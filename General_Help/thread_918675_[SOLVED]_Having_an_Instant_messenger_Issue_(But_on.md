---
title: "[SOLVED] Having an Instant messenger Issue (But only for MSN)"
date: 2008-09-13
forum: General Help
---

### Post by grahambo2005 on 2008-09-13
Hi All

I'm having a problem with Pidgin 
I can connect to my Google account but not My MSN one.

At first I thought it might have been an issue with Pidgin so I tried using the web Msn messenger (which worked fine)

I then re installed pidgin (did not work)

I then installed aMSN and to my surprise that could not connect either.

This leads me to think that there is an issue with my OS as other computers on my home network have no problems accessing MSN

I turned on Debugging in Pidgin and this is what I Got

```
(11:50:39) msn: servconn read error, len: -1 error: Connection reset by peer
(11:50:39) msn: Connection error from Notification server (messenger.hotmail.com): Reading error
(11:50:39) msn: C: NS 000: OUT
(11:50:39) msn: Connection error from Notification server (messenger.hotmail.com): Writing error
(11:50:39) g_log: msn_session_disconnect: assertion `session->connected' failed
```

Any Ideas?

Thanks
Graham

---

### Post by grahambo2005 on 2008-09-13
Resolved

---

### Post by JCM3000 on 2008-09-14
> **grahambo2005 said:**
> Resolved

How?

---

### Post by grahambo2005 on 2008-09-14
Turned out to be a network Issue

Port that MSN uses was forwarded to the other laptop

---

