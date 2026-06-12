---
title: "Monitoring temp with a Dell Vostro 3700"
date: 2010-05-26
forum: Hardware
---

### Post by rXp on 2010-05-26
[Information]
Ubuntu 10.04
Dell Vostro 3700

Hello,

I tried 10 different monitoring applications, from gdesklets to sensors-applet and they were never able to detect my sensors.
My PC is one of the last Dell and it has sensors (trust me, I used a vmware windows and it worked there).
Help me, I have no idea how to make this work.

I want to be able to see the temp(all), cpu (load), ram(load), gpu (load) in the panel.

Best regards,

rXp>!<

---

### Post by bra|10n on 2010-05-26
Have you tried lm-sensors?
If not, sudo apt-get install lm-sensors, then run sensors-detect and essentially answer yes to all questions

---

### Post by rXp on 2010-05-26
> **bra|10n said:**
> Have you tried lm-sensors?
If not, sudo apt-get install lm-sensors, then run sensors-detect and essentially answer yes to all questions
Yes I already tried and it doesn't work at all. I even tried to create a batch to set the sensors manually.

---

### Post by rXp on 2010-05-27
Nobody has an idea ?

---

### Post by mindpowerz on 2010-05-27
This shows that your motherboard sensors are not supported by your version of Ubuntu, and so not detected.

---

### Post by rXp on 2010-05-27
> **mindpowerz said:**
> This shows that your motherboard sensors are not supported by your version of Ubuntu, and so not detected.
So I need to wait an update ?

---

### Post by dino99 on 2010-05-27
into console: sensors-detect

then follow the given propositions

---

