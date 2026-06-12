---
title: "Cannot Suspend / Hibernate"
date: 2008-09-11
forum: General Help
---

### Post by grmbl on 2008-09-11
Hi,

Since recently I switched to Ubuntu and love it, except for some minor things I can't get fixed, which bother me.

One of those is that my PC will not suspend / hibernate. I've looked in the system log and it says:

[COLOR="Blue"]Sep 11 11:30:51 ZOLDER gnome-power-manager: (steven) Suspending computer. Reason: System idle.
Sep 11 11:30:51 ZOLDER gnome-power-manager: (steven) cannot suspend as not allowed from policy
Sep 11 11:30:52 ZOLDER gnome-power-manager: (steven) suspend failed
Sep 11 11:30:52 ZOLDER gnome-power-manager: (steven) cannot hibernate as not allowed from policy
Sep 11 11:30:52 ZOLDER gnome-power-manager: (steven) hibernate failed
[/COLOR]

"cannot hibernate as not allowed from policy"?

Searches, so far, have come back empty. Can anybody please help?

---

### Post by grmbl on 2008-09-23
Geez, nobody? I had no idea this would be SO hard to debug! :confused:

---

### Post by lynx_hanan on 2008-09-23
I once had this problem. It turned out that my swap parttion was formatted to another Filesystem by XP (becuase i installed ext3 \,2 and swap support in XP).

---

### Post by lynx_hanan on 2008-09-23
check if u have a swap or not???

---

