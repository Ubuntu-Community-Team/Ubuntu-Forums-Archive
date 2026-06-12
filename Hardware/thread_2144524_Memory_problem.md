---
title: "Memory problem"
date: 2013-05-12
forum: Hardware
---

### Post by arnaldus on 2013-05-12
Hi everybody, 
i have such a big problem. I have just installed ubuntu 13.04 on my pc, and I selected the x64 one because I have a FX4100 quad-core processor. now if I go in settings, the system says I only have 2GB of RAM, while I have 4GB and Windows recognises it. How can I do?

---

### Post by arnaldus on 2013-05-12
Nobody helps?

---

### Post by grahammechanical on 2013-05-12
Is the operating system working as it should? Then, what is the hurry? The people who try to give help on this forum are all volunteers. We have other things to do in our lives. Such as watching television.

There are some things that you can do to check.

1) Load System Monitor and see what it says as to the amount of memory. 2) open the terminal and run the command ```
top
``` What does that say the total memory is?

Regards.

---

### Post by arnaldus on 2013-05-12
2031636 kib in total. Thanks for help, I didn't meant to disturb anyone. Well, actually the system is working, but it's kinda weird knowing you have 4gb of ram and being able to use only two.

---

### Post by sanderj on 2013-05-12
You can run the python script from [http://www.appelboor.com/dump/check-my-memory.py](http://www.appelboor.com/dump/check-my-memory.py) to tell everything about your memory

```
wget [http://www.appelboor.com/dump/check-my-memory.py](http://www.appelboor.com/dump/check-my-memory.py)
python check-my-memory.py
sudo python check-my-memory.py
```

HTH

---

