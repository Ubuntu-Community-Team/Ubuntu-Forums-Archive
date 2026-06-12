---
title: "How would I fix high fan speed and low battery life?"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by Ub1476 on 2008-01-05
Hi, my laptop fans is almost running at top speed all the time, and my battery only has about 40 minutes life (85%/100%). When this laptop came with XP two years ago I think it lasted for at 1 hour and 30 minutes. My CPU is also running between 65-80C (sometimes I can barely hold my hand on the mousepad). The fans are also running really loud when I'm not using my laptop (with lid closed, no hibernation though). Actually, it doesn't appear to be any difference if I'm running it with really high CPU usage or very low. This can't be normal?

If anyone has an idea how to fix these issues, please reply:)
Thanks in advance.

---

### Post by Perpetual on 2008-01-05
I have been using powertop to improve battery life in Ubuntu and also Fedora and it seems to add about 25% more time to my battery.

```
sudo apt-get -y install powertop
```

Then run powertop from a root terminal.  I make all of the changes it suggests and have not had any adverse effects.

---

### Post by Ub1476 on 2008-01-06
Thanks, it came up with about 4 options, which I enabled. I'll see if I see any changes after a reboot. Are there anymore suggestions out there?

---

### Post by Ub1476 on 2008-01-07
bump

---

### Post by Ub1476 on 2008-01-08
bump

---

### Post by Perpetual on 2008-01-08
No luck with Powertop?

---

### Post by Ub1476 on 2008-01-08
I got some better battery life, maybe 10-15 minutes, but that's it.

---

