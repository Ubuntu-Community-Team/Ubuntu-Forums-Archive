---
title: "Wireless Card"
date: 2009-11-28
forum: Hardware
---

### Post by amaz1ng on 2009-11-28
How can I find out the name of the wireless card that Ubuntu 9.10 is using to connect to the Internet?

---

### Post by cariboo on 2009-11-28
You can do it so many different ways, I'll just give you two. Open a terminal and type:

```
lspci
```

or for more detailed info:

```
sudo lshw -C network
```

---

