---
title: "Kubuntu CUPS problem"
date: 2006-05-19
forum: Hardware &amp; Laptops
---

### Post by evilmonkey on 2006-05-19
Hello,

I installed Kubuntu in an unusual way. I got an Ubuntu CD, installed the base system, did an apt-get install kubuntu desktop, followed by the dist-upgrade to KDE 3.5.2 from the ubuntu repositories. My problem is that CUPS doesn't work. Whenever I try to start CUPS (go into Konsole and type in cupsd), it spits back an error 13. If I do sudo cupsd, it spits back an error 99. I tried searching google, but didn't come to anything that helps me decifer what that actually means. I think I'm missing some package. Help is appreciated. :)

Cheers!

---

### Post by evilmonkey on 2006-05-19
Okay, here's the problem. For some dumb reason, loopback is not being set to 127.0.0.1. Therefore, you must force it.

```
sudo ifconfig lo 127.0.0.1
```

And that will be the end of CUPS problems.

---

