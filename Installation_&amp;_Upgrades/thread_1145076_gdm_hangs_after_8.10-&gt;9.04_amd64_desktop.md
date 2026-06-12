---
title: "gdm hangs after 8.10-&gt;9.04 amd64 desktop"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by ktenney on 2009-05-01
Howdy,

X starts, timer icon appears correct, but the login box
never appears.

If I alt-ctl-f1, sudo killall gdm, startx
I get my desktop wallpaper only.

Running sudo strace -p<gdm> shows lots of access
to pam stuff
pam_ck_connector.so
pam.d/common-session
pam.d/common-account
...

Suggestions?

Thanks,
Kent

---

### Post by ktenney on 2009-05-01
looking at strace output, finding this

sched_yield()
read(10, "*"..., 1)

followed by the more read(10, <char>...,1)

where char spells
(gdmgreeter:8700): DEBUG: sending command:  CLOSE

also stuff like
Got response OK false\n

---

### Post by ktenney on 2009-05-01
OK, the strace stuff is pretty useless, here's snippets from /var/log/auth.log


gdm[4696]: pam_nologin(gdm:auth): cannot determine username
last message repeated 52 times
...

Does this ring any bells?

---

