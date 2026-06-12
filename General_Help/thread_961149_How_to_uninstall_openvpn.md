---
title: "How to uninstall openvpn"
date: 2008-10-28
forum: General Help
---

### Post by JustMe5555 on 2008-10-28
Hello.

I have Ubuntu 8.04 LTS. I installed openvpn using these instructions [http://openvpn.net/index.php/documentation/howto.html#quick](http://openvpn.net/index.php/documentation/howto.html#quick). Now I would like uninstall openvpn, but i don't know how. I tried apt-get remove openvpn. It did not work. I could still use openvpn. I just don't know what to do.

---

### Post by mr nintendo on 2008-10-28
```
sudo synaptic
```
search for openvpn then right-click openvpn and then complete removal.

---

### Post by JustMe5555 on 2008-10-28
> **mr nintendo said:**
> ```
sudo synaptic
```
search for openvpn then right-click openvpn and then complete removal.

I did that. However when I type ```
openvpn
``` I get the listing of what different options I can choose. It is the same listing I had when I had openvpn installed. I'm just wondering should I get same kind of error message if I don't have openvpn installed on my computer?

---

### Post by Kevbert on 2008-10-28
Have you tried 
```
make uninstall

```

---

### Post by JustMe5555 on 2008-10-28
Thank you. I was able to uninstall openvpn.

---

