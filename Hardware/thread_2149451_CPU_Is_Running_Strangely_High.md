---
title: "CPU Is Running Strangely High"
date: 2013-05-28
forum: Hardware
---

### Post by dscarfogliero on 2013-05-28
I have a Dell Precision 390 running a Intel Core 2 Quad 4300 processor. I used to have Windows 7 installed on it and everything was running normal. Now I have Ubuntu 13.04 and the processor is constantly running at 60+%.

Is that normal, or is there something wrong?

Thanks for the help.

---

### Post by Yellow Pasque on 2013-05-28
You should look at what's using that much CPU:
```
sudo apt-get install htop
htop
```

---

### Post by ahallubuntu on 2013-05-28
~

---

### Post by dscarfogliero on 2013-05-28
Unity and Compiz were running at around 80% each always. I mainly use this machine as a server so I installed Cinnamon and uninstalled Unity. CPU is running at a normal 5% now.

Thanks for the tip about htop. Awesome tool.

---

