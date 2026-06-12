---
title: "E-Blue Arco+ Wireless Keyboard"
date: 2010-11-26
forum: Hardware
---

### Post by AdventClive on 2010-11-26
Hello, I'm experiencing a problem with the keyboard.
It work fine on windows, but on ubuntu, it didn't work, but the wireless mouse are working.
I'm using Ubuntu 10.10.

Hoping for a solution ;)

---

### Post by Fafler on 2010-11-26
O, i wish i didn't have to look up product info myself every time i help someone out with hardware i don't actually own or know. 

Anyway, we need to know what happens when you connect the keyboard. Open a terminal and type:
```
lsusb
tail -f /var/log/messages
```

Now reconnect the receiver and post the output from both commands.

---

