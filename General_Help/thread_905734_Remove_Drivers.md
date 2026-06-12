---
title: "Remove Drivers"
date: 2008-08-30
forum: General Help
---

### Post by bbspiritdancer on 2008-08-30
Hi,I installed drivers for my Cnet Wireless G Dongle using code:
sudo ndiswrapper -i rt2500usb.inf and it was successful.Could someone please tell me, how i get the drivers off of my computer?

---

### Post by jonian_g on 2008-08-30
```
sudo ndiswrapper -r rt2500usb
```

To see options for commands type command --help. for example:

```
ndiswrapper --help
```

---

