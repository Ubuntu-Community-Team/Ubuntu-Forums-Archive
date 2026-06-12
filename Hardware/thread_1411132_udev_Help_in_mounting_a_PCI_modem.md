---
title: "udev Help in mounting a PCI modem"
date: 2010-02-19
forum: Hardware
---

### Post by vitae_drinker on 2010-02-19
Hi, I need some help in writing a udev rule that will allow my pci modem to be mounted to make it accessible to every user using the computer so that it can be used to receive and send faxes. This is for a small office environment. I want to have the modem (currently ttySM0) to be symlinked to "modem", to the existing group "modem", with read & write privelages to everyone. So far, I have come up with the following udev rule, /etc/udev/rules.d/10-modem.rules:

```
KERNEL=="ttySM0", SYMLINK+="modem", GROUP="modem", MODE="0666"
```

Well, this isn't working and hasn't been for several weeks of off and on attempts. Can anyone help?

---

### Post by vitae_drinker on 2010-02-19
No one has any ideas? I'd really appreciate some help with this. Am I even close? From what I've seen this looks right...

---

### Post by vitae_drinker on 2010-02-24
Wow, so noone has any helpful hints with using udev?

---

