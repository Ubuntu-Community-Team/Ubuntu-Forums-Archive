---
title: "Nvidia graphics card (problems installing driver)"
date: 2009-02-04
forum: Hardware
---

### Post by Claustrophobic Roadkill on 2009-02-04
When trying to install The nVidia 177 driver (via synaptic package manager, the other way is not working due to another problem) I get the following message:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Any ideas? And how would I add it with the apt-get function in the terminal?

---

### Post by taurus on 2009-02-04
Make sure you don't have update manager running in the background when you try to enable/install nvidia driver for your graphic card.

Applications -> Accessories -> Terminal
```
ps -A
```

---

