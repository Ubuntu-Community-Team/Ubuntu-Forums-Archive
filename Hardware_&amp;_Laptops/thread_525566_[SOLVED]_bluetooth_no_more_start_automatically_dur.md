---
title: "[SOLVED] bluetooth no more start automatically during initscripts boot process ..."
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by BigBob on 2007-08-14
Hi all,

I don't know why, but hcid daemon normally launched automatically by /etc/init.d/bluetooth initscript doesn't start anymore.

Actually, i have to boot my Feisty, then after logged in, start manually bluetooth services with 'sudo /etc/init.d/bluetooth star'

I have spend 2 days trying debugging the trouble, without any success.

The only things I am sure :

- /etc/init.d/bluetooth script was started at boot process (looking in text mode i can see the starting bluetooth [ok] flag).

- Also putting some echo's in the /etc/init.d/bluetooth script i can see it was executed at boot.

By the way how i can see why hcid doesn't start in the /etc/init.d/bluetooth script ?

Any idea ?

A++

---

### Post by BigBob on 2007-08-14
Ok,

I have finally found the problem, priority of dbus initscripts have changed (probably a program i have installed).

A++

---

